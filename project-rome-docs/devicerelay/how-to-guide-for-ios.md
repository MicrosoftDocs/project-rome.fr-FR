---
title: Implémentation des fonctionnalités de relais d’appareil pour iOS
description: Ce guide explique comment découvrir des applications et des appareils à distance et lancer des applications ou interagir avec les services d’application.
ms.topic: article
keywords: Microsoft, windows, project rome, exécution des commandes, ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: c9c3e8bf580884c6f0c3b6ccdf177f163f05c03a
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755780"
---
# <a name="implementing-device-relay-for-ios"></a>Implémentation de relais d’appareil pour iOS

La fonctionnalité de relais de l’appareil de Project Rome se compose d’un ensemble d’API qui prennent en charge les deux fonctionnalités principales : lancement à distance (également appelés commandes) et les services d’application.

API de lancement à distance prennent en charge les scénarios où un processus sur un appareil distant est démarré à partir d’un périphérique local. Par exemple, un utilisateur peut écouter la radio sur leur téléphone dans la voiture, mais quand ils obtiennent accueil ils utilisent leur téléphone pour transférer la lecture à leur Xbox qui est relié à la chaîne stéréo.

API de Services d’application permettent à une application établir un pipeline persistant entre les deux appareils par le biais duquel les messages contenant n’importe quel contenu arbitraire peuvent être envoyés. Par exemple, une application qui s’exécute sur un appareil mobile de partage de photos peut établir une connexion avec des PC de l’utilisateur afin de récupérer les photos.

Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter fonctionnalités liées à relais de l’appareil.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la plateforme de périphériques connectés et les Notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>À l’aide de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Découvrir les applications et des périphériques distants

Un **MCDRemoteSystemWatcher** instance gère la fonctionnalité principale de cette section. Déclarez-le dans la classe qui consiste à découvrir des systèmes distants.

`MCDRemoteSystemWatcher* _watcher;`

Avant de créer un observateur et démarrer la découverte des périphériques, vous pouvez souhaiter ajouter des filtres de détection pour déterminer quels types de périphériques de votre application ciblera. Ils peuvent être déterminés par l’utilisateur d’entrée ou codé en dur dans l’application, en fonction de votre cas d’utilisation.

Le code suivant à partir de l’exemple d’application montre comment créer et démarrer une instance de l’Observateur autoriser votre application analyser et interagir avec les appareils qui sont détectées.

```ObjectiveC
// Start watcher with filter for transport types, form factors
- (void)startWatcherWithFilter:(NSMutableArray<NSObject<MCDRemoteSystemFilter>*>*)remoteSystemFilter
{
    _discoveredSystems = [[NSMutableArray alloc] init];
    _devicesAdded = 0;
    _devicesUpdated = 0;
    _devicesRemoved = 0;

    // add filters (not defined here)
    _watcher = (remoteSystemFilter.count > 0) ? [[MCDRemoteSystemWatcher alloc] initWithFilters:remoteSystemFilter] :
        [[MCDRemoteSystemWatcher alloc] init];

    // add event handlers
    RemoteSystemViewController* __weak weakSelf = self;
    [_watcher addRemoteSystemAddedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemAdded:system]; }];

    [_watcher addRemoteSystemUpdatedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemUpdated:system]; }];

    [_watcher addRemoteSystemRemovedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemRemoved:system]; }];

    // start watcher
    [_watcher start];
}
```

Les méthodes de gestionnaire d’événements sont définis ici.

```ObjectiveC
// Handle when RemoteSystems are added
- (void)_onRemoteSystemAdded:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesAdded++;
        [_discoveredSystems addObject:system];
        [_delegate remoteSystemsDidUpdate];
    }
}

// Handle when RemoteSystems are updated
- (void)_onRemoteSystemUpdated:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesUpdated++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems replaceObjectAtIndex:i withObject:system];
                break;
            }
        }
    }
}

// Handle when RemoteSystems are removed
- (void)_onRemoteSystemRemoved:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesRemoved++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems removeObjectAtIndex:i];
                break;
            }
        }
    }
}
```

Nous conseillons de votre application de conserver un ensemble de périphériques détectés (représenté par **MCDRemoteSystem** instances) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, de type nom et le périphérique d’affichage) sur l’interface utilisateur. 

Une fois `[_watcher start]` est appelée, elle commencera surveille l’activité du système distant et déclenche des événements lorsque des appareils connectés sont découverts, mis à jour ou supprimés à partir de l’ensemble des périphériques détectés. Il analyse en continu en arrière-plan, il est donc recommandé que vous arrêtez l’Observateur (avec `[_watcher stop]`) lorsque vous n’avez plus besoin afin d’éviter de drainage de communication et de la batterie inutiles sur le réseau.

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Exemple de cas d’usage : implémentation de lancement à distance et les services d’application à distance
À ce stade dans votre code, vous devez avoir une liste de travail de **MCDRemoteSystem** les objets qui font référence à des appareils disponibles. Ce que vous faire avec ces périphériques dépendra de la fonction de votre application. Les principaux types d’interaction sont lancement à distance et les services d’application à distance. Ils sont expliqués dans les sections suivantes.

### <a name="a-remote-launching"></a>A) le lancement à distance

Le code suivant montre comment sélectionner un de la **MCDRemoteSystem** objets (dans l’idéal, ceci s’effectue via un contrôle d’interface utilisateur), puis utiliser **MCDRemoteLauncher** pour lancer une application dessus en passant d’une application compatible URI.

Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lancera l’URI donné avec son application par défaut pour ce modèle d’URI) _ou_ une application spécifique à distance sur cet appareil.

Comme la section précédente décrivait, détection se produit au niveau du périphérique tout d’abord (un **MCDRemoteSystem** représente un périphérique), mais vous pouvez appeler la `getApplications` méthode sur un **MCDRemoteSystem** instance pour obtenir un tableau de **MCDRemoteSystemApp** objets qui représentent des applications sur l’appareil à distance qui ont été inscrits pour utiliser la plateforme d’appareils connectés (comme vous avez inscrit votre propre application dans les étapes préliminaires ci-dessus). Les deux **MCDRemoteSystem** et **MCDRemoteSystemApp** peut être utilisé pour construire un **MCDRemoteSystemConnectionRequest**, qui est ce qui est nécessaire pour lancer un URI.

Le code de l’exemple suivant montre le lancement à distance d’un URI sur une demande de connexion.

```ObjectiveC
// Send a remote launch of a uri to RemoteSystemApplication
- (IBAction)launchUriButton:(id)sender
{
    NSString* uri = self.uriField.text;
    MCDRemoteLauncher* remoteLauncher = [[MCDRemoteLauncher alloc] init];
    MCDRemoteSystemConnectionRequest* connectionRequest =
        [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
    [remoteLauncher launchUriAsync:uri
        withConnectionRequest:connectionRequest
            completion:^(MCDRemoteLaunchUriStatus result, NSError* _Nullable error) {
                if (error)
                {
                    NSLog(@"LaunchURI [%@]: ERROR: %@", uri, error);
                    return;
                }

                if (result == MCDRemoteLaunchUriStatusSuccess)
                {
                    NSLog(@"LaunchURI [%@]: Success!", uri);
                }
                else
                {
                    NSLog(@"LaunchURI [%@]: Failed with code %d", uri, (int)result);
                }
            }];
}
```

En fonction de l’URI qui est envoyé, vous pouvez lancer une application dans un état spécifique ou la configuration sur un périphérique distant. Cela permet la capacité à poursuivre une tâche de l’utilisateur, telles que regarder un film, sur un autre appareil sans interruption.

En fonction de votre utilisation, vous devrez peut-être couvrir les cas dans lequel aucune application sur le système cible ne peut gérer l’URI, ou plusieurs applications peuvent le gérer. Le **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** classe et **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** classe décrivent comment effectuer cette opération.

### <a name="b-remote-app-services"></a>B) services d’application à distance

Votre application iOS peut utiliser le portail des appareils connectés pour interagir avec les services d’application sur d’autres appareils. Cela fournit de nombreuses façons de communiquer avec d’autres appareils&mdash;tout cela sans avoir besoin de migrer une application au premier plan de l’appareil hôte.

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurer le service d’application sur l’appareil cible
Ce guide utilise les [Roman application Test pour Windows](http://aka.ms/romeapp) en tant que son service d’application cible. Par conséquent, le code ci-dessous génère une application iOS rechercher ce service d’application spécifique sur le système distant donné. Si vous souhaitez tester ce scénario, téléchargez l’application de Test Roman sur un appareil Windows et vérifiez que vous êtes connecté avec le même MSA que vous avez utilisé dans les étapes préliminaires ci-dessus.

Pour obtenir des instructions sur la façon d’écrire votre propre service d’application UWP, consultez [créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Vous devrez apporter quelques modifications afin que le service compatible avec les appareils connectés. Consultez le [guide UWP pour les services d’application à distance](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour obtenir des instructions sur la procédure à suivre. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Ouvrir une connexion de service d’application sur le périphérique client
Votre application iOS doit acquérir une référence à un périphérique distant ou une application. Comme la section de lancement, ce scénario requiert l’utilisation d’un **MCDRemoteSystemConnectionRequest**, ce qui peut être construit à partir de l’un **MCDRemoteSystem** ou un **MCDRemoteSystemApp**  représentant une application disponible sur le système.

En outre, votre application a besoin identifier son service de l’application ciblée par deux chaînes : le *nom app service* et *identificateur de package*. Ceux-ci sont trouvent dans le code source du fournisseur de services d’application (consultez [créer et consommer un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations). Ces chaînes créent le **MCDAppServiceDescription**, qui est chargé dans un **MCDAppServiceConnection** instance.

```ObjectiveC
// Step #1:  Establish an app service connection
- (IBAction)connectAppServiceButton:(id)sender
{
    MCDAppServiceConnection* connection = nil;
    @synchronized(self)
    {
        connection = _appServiceConnection;
        if (!connection)
        {
            connection = _appServiceConnection = [MCDAppServiceConnection new];
            connection.appServiceDescription =
                [MCDAppServiceDescription descriptionWithName:g_appServiceName packageId:g_packageIdentifier];
            _serviceClosedRegistration = [connection addServiceClosedListener:^(__unused MCDAppServiceConnection* connection,
                MCDAppServiceClosedStatus status) { [self appServiceConnection:connection closedWithStatus:status]; }];
        }
    }

    @try
    {
        MCDRemoteSystemConnectionRequest* connectionRequest =
            [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
        [connection openRemoteAsync:connectionRequest
            completion:^(MCDAppServiceConnectionStatus status, NSError* error) {
                if (error)
                {
                    NSLog(@"ConnectAppService: ERROR: %@", error);
                    return;
                }
                if (status != MCDAppServiceConnectionStatusSuccess)
                {
                    NSLog(@"ConnectAppService: Failed with code %d", (int)status);
                    return;
                }
                NSLog(@"Successfully connected!");
                dispatch_async(
                    dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = @"App service connected! no ping sent"; });
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"ConnectAppService: EXCEPTION! %@", ex);
    }
}
```


#### <a name="create-a-message-to-send-to-the-app-service"></a>Créer un message à envoyer au service d’application

Déclarez une variable pour stocker le message à envoyer. Sur iOS, les messages que vous envoyez aux services d’application à distance sera de la **NSDictionary** type.

> [!NOTE]
> Lorsque votre application communique avec les services d’application sur d’autres plateformes, la plateforme d’appareils connectés traduit la **NSDictionary** dans la construction équivalente sur la plateforme de réception. Par exemple, un **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** envoyé à partir de cette application à un Windows service d’application est alors traduite en une [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objet (de .NET Framework), qui peut ensuite être interprété par le service d’application. Informations passées dans l’autre sens subit la traduction inverse.

La méthode suivante crée un message qui peut être interprété par app service l’application Test Roman pour Windows.

```ObjectiveC
// Create a message to send
- (NSDictionary*)_createPingMessage
{
    return @{
        @"Type" : @"ping",
        @"CreationDate" : [_dateFormatter stringFromDate:[NSDate date]],
        @"TargetId" : _selectedApplication.applicationId
    };
}
```

> [!IMPORTANT]
> Le **NSDictionary** objets qui sont passés entre les applications et services dans le scénario de services d’application à distance doivent respecter le format suivant : Les clés doivent être **chaîne NSString**s et les valeurs peuvent être : **Chaîne NSString**, boxed de types numériques (entiers ou points flottante), boxed de valeurs booléennes, **NSDate**, **NSUUID**, tableaux homogènes d’une de ces types, ou d’autres **NSDictionary**  objets qui répondent à cette spécification. 

#### <a name="send-messages-to-the-app-service"></a>Envoyer des messages au service d’application

Une fois la connexion de service d’application est établie et que le message est créé, envoyer vers le service d’application est simple et peut être effectuée depuis n’importe où dans l’application qui a une référence à l’instance de la connexion et le message.

Le code suivant à partir de l’exemple montre l’envoi d’un message à un service d’application et la gestion de la réponse.

```ObjectiveC
//  Send a message using the app service connection
- (IBAction)sendAppServiceButton:(id)sender
{
    if (!_appServiceConnection)
    {
        return;
    }

    // Send the message and get a response
    @try
    {
        [_appServiceConnection sendMessageAsync:[self _createPingMessage]
            completion:^(MCDAppServiceResponse* response, NSError* error) {
                if (error)
                {
                    NSLog(@"SendPing: ERROR: %@", error);
                    return;
                }

                if (response.status != MCDAppServiceResponseStatusSuccess)
                {
                    NSLog(@"SendPing: Response received with bad status code %d", (int)response.status);
                    return;
                }

                NSString* creationDateString = response.message[@"CreationDate"];
                if (creationDateString)
                {
                    NSDate* date = [_dateFormatter dateFromString:creationDateString];
                    if (date)
                    {
                        NSTimeInterval diff = [[NSDate date] timeIntervalSinceDate:date];
                        dispatch_async(dispatch_get_main_queue(),
                            ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"%g", diff]; });
                    }
                }
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"SendPing: EXCEPTION! %@", ex);
    }
}
```

Dans le cas de Roman application, la réponse contient la date de que sa création, donc dans ce cas d’usage très simple, nous pouvons comparer les dates pour obtenir l’heure de transit totale de la réponse du message.

Ainsi se conclut un échange de messages unique avec un service d’application à distance.

#### <a name="finish-app-service-communication"></a>Terminer la communication de service d’application

Lorsque votre application est terminée interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a>Rubriques connexes
* [Page de référence des API](api-reference-for-ios.md) 
* [exemple d’application iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [Communiquer avec un service d’application à distance (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).
