---
title: Implémentation des fonctionnalités de relais d’appareils pour iOS
description: Ce guide vous explique comment découvrir des appareils et des applications distants et comment lancer ensuite des applications ou interagir avec des services d’application.
ms.topic: article
keywords: microsoft, windows, projet rome, commandes, android
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: c9c3e8bf580884c6f0c3b6ccdf177f163f05c03a
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755780"
---
# <a name="implementing-device-relay-for-ios"></a>Implémentation de relais d’appareils pour iOS

La fonctionnalité Relais d’appareils du projet Rome se compose d’un ensemble d’API qui prennent en charge les deux principales fonctionnalités : le lancement à distance (aussi appelé commandes) et les services d’application distants.

Les API de lancement à distance prennent en charge les scénarios dans lesquels un processus est démarré sur un appareil distant à partir d’un appareil local. Par exemple, un utilisateur écoute la radio sur son téléphone en voiture, mais une fois à la maison, il bascule la lecture de son téléphone vers sa Xbox qui est raccordée à sa chaîne stéréo.

Les API App Services permettent à une application d’établir un pipeline persistant entre deux appareils qui permet l’envoi de messages comportant du contenu arbitraire. Par exemple, l’utilisateur pourrait établir une connexion entre l’application de partage de photos qui s’exécute sur son appareil mobile et son PC en vue de récupérer des photos.

Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées au relais d’appareils à l’aide de la plateforme.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la Plateforme d’appareils connectés et des notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Utilisation de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Découvrir les appareils et les applications distants

Une instance de **MCDRemoteSystemWatcher** gérera la principale fonctionnalité de cette section. Déclarez-la dans la classe qui doit découvrir les systèmes distants.

`MCDRemoteSystemWatcher* _watcher;`

Avant de créer un observateur et de lancer la découverte d’appareils, vous pouvez souhaiter ajouter des filtres de découverte pour déterminer les types d’appareil que votre application doit cibler. Ils peuvent être déterminés par entrée utilisateur ou codés en dur dans l’application, selon votre cas d’utilisation.

Le code suivant tiré de l’exemple d’application montre comment créer et démarrer une instance d’observateur permettant à votre application d’analyser et d’interagir avec les appareils découverts.

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

Les méthodes de gestionnaire d’événements sont définies ici.

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

De préférence, votre application doit tenir à jour un ensemble d’appareils découverts (représentés par des instances de **MCDRemoteSystem**) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, le nom d’affichage et le type d’appareil) dans l’interface utilisateur. 

Une fois `[_watcher start]` appelé, il se met à observer l’activité du système distant et déclenche des événements quand des appareils connectés sont découverts, mis à jour ou supprimés de l’ensemble d’appareils détectés. Sachant que l’observateur poursuit son analyse en arrière-plan, il est recommandé de l’arrêter (avec `[_watcher stop]`) dès que cela n’est plus nécessaire pour éviter de consommer des ressources de communication réseau et de batterie.

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Exemple de cas d’utilisation : implémentation du lancement à distance et de services d’application distants
À ce stade, votre code doit comporter une liste opérationnelle d’objets **MCDRemoteSystem** qui font référence aux appareils disponibles. Ce à quoi vont vous servir ces appareils dépend de la fonction de votre application. Les principaux types d’interaction sont le lancement à distance et les services d’application distants. Ils vous sont expliqués dans les sections suivantes.

### <a name="a-remote-launching"></a>A) Lancement à distance

Le code suivant montre comment sélectionner un des objets **MCDRemoteSystem** (dans l’idéal, via un contrôle d’interface utilisateur) et utiliser ensuite **MCDRemoteLauncher** pour lancer une application sur cet objet en lui transmettant un URI compatible avec l’application.

Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lance l’URI donné avec son application par défaut pour ce schéma d’URI) _ou_ une application distante spécifique sur cet appareil.

Comme nous l’avons vu dans la section précédente, la découverte se produit d’abord au niveau de l’appareil (un objet **MCDRemoteSystem** représente un appareil), mais vous pouvez appeler la méthode `getApplications` sur une instance de **MCDRemoteSystem** pour obtenir un tableau d’objets **MCDRemoteSystemApp**, qui représentent les applications de l’appareil distant qui ont été inscrites pour utiliser la Plateforme d’appareils connectés (de la même façon que vous avez inscrit votre propre application dans les étapes préliminaires décrites plus haut). Les objets **MCDRemoteSystem** et **MCDRemoteSystemApp** peuvent tous deux servir à construire un objet **MCDRemoteSystemConnectionRequest**, qui est nécessaire au lancement d’un URI.

Le code suivant tiré de l’exemple illustre le lancement à distance d’un URI sur une demande de connexion.

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

Selon l’URI qui est envoyé, vous pouvez lancer une application dans un état ou une configuration spécifiques sur un appareil distant. Cela donne la possibilité de poursuivre une tâche d’utilisateur, comme regarder un film, sur un autre appareil sans interruption.

Selon votre utilisation, vous devrez peut-être prévoir les cas où aucune application du système ciblé ne peut gérer l’URI et ceux où plusieurs applications peuvent le gérer. Les classes **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** et **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** décrivent comment faire.

### <a name="b-remote-app-services"></a>B) Services d’application distants

Votre application iOS peut utiliser le portail Appareils connectés pour interagir avec des services d’application sur d’autres appareils. Cela donne la possibilité de communiquer de diverses façons avec d’autres appareils, tout cela sans qu’il soit nécessaire de placer une application au premier plan de l’appareil hôte.

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurer le service d’application sur l’appareil cible
Ce guide utilise l’[application de test Roman pour Windows](http://aka.ms/romeapp) comme service d’application cible. Par conséquent, le code ci-dessous conduit une application iOS à rechercher ce service d’application spécifique sur le système distant donné. Si vous souhaitez tester ce scénario, téléchargez l’application de test Roman sur un appareil Windows et vérifiez que vous êtes connecté avec le même compte MSA que vous avez utilisé dans les étapes préliminaires plus haut.

Pour savoir comment écrire votre propre service d’application UWP, consultez [Créer et utiliser un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Vous devrez apporter quelques modifications pour rendre le service compatible avec Appareils connectés. Consultez le [Guide UWP pour les services d’application distants](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour savoir comment procéder. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Ouvrir une connexion de service d’application sur l’appareil client
Votre application iOS doit acquérir une référence à un appareil ou application distants. Comme dans la section relative au lancement, ce scénario nécessite l’utilisation d’un objet **MCDRemoteSystemConnectionRequest**, qui peut être construit à partir d’un objet **MCDRemoteSystem** ou **MCDRemoteSystemApp** représentant une application disponible sur le système.

De plus, votre application devra identifier son service d’application cible avec deux chaînes : le *nom du service d’application* et l’*identificateur de package*. Celles-ci se trouvent dans le code source du fournisseur de service d’application (consultez [Créer et utiliser un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations). Ensemble, ces chaînes constituent **MCDAppServiceDescription**, qui est chargé dans une instance de **MCDAppServiceConnection**.

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

Déclarez une variable pour y stocker le message à envoyer. Sur iOS, les messages que vous envoyez à des services d’application distants sont de type **NSDictionary**.

> [!NOTE]
> Quand votre application communique avec les services d’application d’autres plateformes, la Plateforme d’appareils connectés traduit l’objet **NSDictionary** en construction équivalente sur la plateforme de réception. Par exemple, un objet **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** envoyé à partir de cette application à un service d’application Windows est traduit en objet [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (du .NET Framework), qui peut ensuite être interprété par le service d’application. Les informations transmises dans l’autre direction font l’objet d’une traduction inverse.

La méthode suivante façonne un message qui peut être interprété par le service d’application de l’application de test Roman pour Windows.

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
> Les objets **NSDictionary** qui sont transmis entre les applications et les services dans le scénario des services d’application distants doivent respecter le format suivant : Les clés doivent être des chaînes **NSString** et les valeurs peuvent être les suivantes : **NSString**, types numériques convertis (boxed) (entiers ou virgules flottante), valeurs booléennes converties (boxed), **NSDate**, **NSUUID**, tableaux homogènes d’un de ces types ou autres objets **NSDictionary**  qui respectent cette spécification. 

#### <a name="send-messages-to-the-app-service"></a>Envoyer des message au service d’application

Une fois que la connexion au service d’application est établie et que le message est créé, il est facile de l’envoyer au service d’application. Cela peut se faire de n’importe où dans l’application à condition de disposer d’une référence à l’instance de connexion et du message.

Le code suivant tiré de l’exemple illustre l’envoi d’un message à un service d’application et le traitement de la réponse.

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

Dans le cas de l’application Roman, la réponse contient la date de sa création. S’agissant d’un cas d’utilisation très simple, nous pouvons comparer les dates pour obtenir la durée totale de transit de la réponse au message.

Cela met fin à un échange de messages unique avec un service d’application distant.

#### <a name="finish-app-service-communication"></a>Terminer la communication du service d’application

Une fois que votre application a achevé son interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.

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
* [Exemple d’application iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [Communiquer avec un service d’application distant (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Créer et utiliser un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
