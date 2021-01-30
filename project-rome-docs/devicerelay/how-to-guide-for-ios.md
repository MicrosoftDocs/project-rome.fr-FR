---
title: Implémentation des fonctionnalités de relais d’appareils pour iOS
description: Ce guide vous explique comment découvrir des appareils et des applications distants et comment lancer ensuite des applications ou interagir avec des services d’application.
ms.topic: article
keywords: microsoft, windows, projet rome, commandes, android
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 33dd7e0148c5c7e4ff9d254b4039b95129ac6c69
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901549"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="d39ca-104">Implémentation de relais d’appareils pour iOS</span><span class="sxs-lookup"><span data-stu-id="d39ca-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="d39ca-105">La fonctionnalité Relais d’appareils du projet Rome se compose d’un ensemble d’API qui prennent en charge les deux principales fonctionnalités : le lancement à distance (aussi appelé commandes) et les services d’application distants.</span><span class="sxs-lookup"><span data-stu-id="d39ca-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="d39ca-106">Les API de lancement à distance prennent en charge les scénarios dans lesquels un processus est démarré sur un appareil distant à partir d’un appareil local.</span><span class="sxs-lookup"><span data-stu-id="d39ca-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="d39ca-107">Par exemple, un utilisateur écoute la radio sur son téléphone en voiture, mais une fois à la maison, il bascule la lecture de son téléphone vers sa Xbox qui est raccordée à sa chaîne stéréo.</span><span class="sxs-lookup"><span data-stu-id="d39ca-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="d39ca-108">Les API App Services permettent à une application d’établir un pipeline persistant entre deux appareils qui permet l’envoi de messages comportant du contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="d39ca-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="d39ca-109">Par exemple, l’utilisateur pourrait établir une connexion entre l’application de partage de photos qui s’exécute sur son appareil mobile et son PC en vue de récupérer des photos.</span><span class="sxs-lookup"><span data-stu-id="d39ca-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="d39ca-110">Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="d39ca-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="d39ca-111">Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées au relais d’appareils à l’aide de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="d39ca-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="d39ca-112">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="d39ca-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="d39ca-113">Configuration de la Plateforme d’appareils connectés et des notifications</span><span class="sxs-lookup"><span data-stu-id="d39ca-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="d39ca-114">Utilisation de la plateforme</span><span class="sxs-lookup"><span data-stu-id="d39ca-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="d39ca-115">Découvrir les appareils et les applications distants</span><span class="sxs-lookup"><span data-stu-id="d39ca-115">Discover remote devices and apps</span></span>

<span data-ttu-id="d39ca-116">Une instance de **MCDRemoteSystemWatcher** gérera la principale fonctionnalité de cette section.</span><span class="sxs-lookup"><span data-stu-id="d39ca-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="d39ca-117">Déclarez-la dans la classe qui doit découvrir les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="d39ca-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="d39ca-118">Avant de créer un observateur et de lancer la découverte d’appareils, vous pouvez souhaiter ajouter des filtres de découverte pour déterminer les types d’appareil que votre application doit cibler.</span><span class="sxs-lookup"><span data-stu-id="d39ca-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="d39ca-119">Ils peuvent être déterminés par entrée utilisateur ou codés en dur dans l’application, selon votre cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d39ca-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="d39ca-120">Le code suivant tiré de l’exemple d’application montre comment créer et démarrer une instance d’observateur permettant à votre application d’analyser et d’interagir avec les appareils découverts.</span><span class="sxs-lookup"><span data-stu-id="d39ca-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

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

<span data-ttu-id="d39ca-121">Les méthodes de gestionnaire d’événements sont définies ici.</span><span class="sxs-lookup"><span data-stu-id="d39ca-121">The event handler methods are defined here.</span></span>

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

<span data-ttu-id="d39ca-122">De préférence, votre application doit tenir à jour un ensemble d’appareils découverts (représentés par des instances de **MCDRemoteSystem**) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, le nom d’affichage et le type d’appareil) dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d39ca-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="d39ca-123">Une fois `[_watcher start]` appelé, il se met à observer l’activité du système distant et déclenche des événements quand des appareils connectés sont découverts, mis à jour ou supprimés de l’ensemble d’appareils détectés.</span><span class="sxs-lookup"><span data-stu-id="d39ca-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="d39ca-124">Sachant que l’observateur poursuit son analyse en arrière-plan, il est recommandé de l’arrêter (avec `[_watcher stop]`) dès que cela n’est plus nécessaire pour éviter de consommer des ressources de communication réseau et de batterie.</span><span class="sxs-lookup"><span data-stu-id="d39ca-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="d39ca-125">Exemple de cas d’utilisation : implémentation du lancement à distance et de services d’application distants</span><span class="sxs-lookup"><span data-stu-id="d39ca-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="d39ca-126">À ce stade, votre code doit comporter une liste opérationnelle d’objets **MCDRemoteSystem** qui font référence aux appareils disponibles.</span><span class="sxs-lookup"><span data-stu-id="d39ca-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="d39ca-127">Ce à quoi vont vous servir ces appareils dépend de la fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="d39ca-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="d39ca-128">Les principaux types d’interaction sont le lancement à distance et les services d’application distants.</span><span class="sxs-lookup"><span data-stu-id="d39ca-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="d39ca-129">Ils vous sont expliqués dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="d39ca-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="d39ca-130">A) Lancement à distance</span><span class="sxs-lookup"><span data-stu-id="d39ca-130">A) Remote launching</span></span>

<span data-ttu-id="d39ca-131">Le code suivant montre comment sélectionner un des objets **MCDRemoteSystem** (dans l’idéal, via un contrôle d’interface utilisateur) et utiliser ensuite **MCDRemoteLauncher** pour lancer une application sur cet objet en lui transmettant un URI compatible avec l’application.</span><span class="sxs-lookup"><span data-stu-id="d39ca-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="d39ca-132">Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lance l’URI donné avec son application par défaut pour ce schéma d’URI) _ou_ une application distante spécifique sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="d39ca-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="d39ca-133">Comme nous l’avons vu dans la section précédente, la découverte se produit d’abord au niveau de l’appareil (un objet **MCDRemoteSystem** représente un appareil), mais vous pouvez appeler la méthode `getApplications` sur une instance de **MCDRemoteSystem** pour obtenir un tableau d’objets **MCDRemoteSystemApp**, qui représentent les applications de l’appareil distant qui ont été inscrites pour utiliser la Plateforme d’appareils connectés (de la même façon que vous avez inscrit votre propre application dans les étapes préliminaires décrites plus haut).</span><span class="sxs-lookup"><span data-stu-id="d39ca-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="d39ca-134">Les objets **MCDRemoteSystem** et **MCDRemoteSystemApp** peuvent tous deux servir à construire un objet **MCDRemoteSystemConnectionRequest**, qui est nécessaire au lancement d’un URI.</span><span class="sxs-lookup"><span data-stu-id="d39ca-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="d39ca-135">Le code suivant tiré de l’exemple illustre le lancement à distance d’un URI sur une demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="d39ca-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

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

<span data-ttu-id="d39ca-136">Selon l’URI qui est envoyé, vous pouvez lancer une application dans un état ou une configuration spécifiques sur un appareil distant.</span><span class="sxs-lookup"><span data-stu-id="d39ca-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="d39ca-137">Cela donne la possibilité de poursuivre une tâche d’utilisateur, comme regarder un film, sur un autre appareil sans interruption.</span><span class="sxs-lookup"><span data-stu-id="d39ca-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="d39ca-138">Selon votre utilisation, vous devrez peut-être prévoir les cas où aucune application du système ciblé ne peut gérer l’URI et ceux où plusieurs applications peuvent le gérer.</span><span class="sxs-lookup"><span data-stu-id="d39ca-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="d39ca-139">Les classes **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** et **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** décrivent comment faire.</span><span class="sxs-lookup"><span data-stu-id="d39ca-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="d39ca-140">B) Services d’application distants</span><span class="sxs-lookup"><span data-stu-id="d39ca-140">B) Remote app services</span></span>

<span data-ttu-id="d39ca-141">Votre application iOS peut utiliser le portail Appareils connectés pour interagir avec des services d’application sur d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="d39ca-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="d39ca-142">Cela donne la possibilité de communiquer de diverses façons avec d’autres appareils, tout cela sans qu’il soit nécessaire de placer une application au premier plan de l’appareil hôte.</span><span class="sxs-lookup"><span data-stu-id="d39ca-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="d39ca-143">Configurer le service d’application sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="d39ca-143">Set up the app service on the target device</span></span>
<span data-ttu-id="d39ca-144">Ce guide utilise l’[application de test Roman pour Windows](https://aka.ms/romeapp) comme service d’application cible.</span><span class="sxs-lookup"><span data-stu-id="d39ca-144">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="d39ca-145">Par conséquent, le code ci-dessous conduit une application iOS à rechercher ce service d’application spécifique sur le système distant donné.</span><span class="sxs-lookup"><span data-stu-id="d39ca-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="d39ca-146">Si vous souhaitez tester ce scénario, téléchargez l’application de test Roman sur un appareil Windows et vérifiez que vous êtes connecté avec le même compte MSA que vous avez utilisé dans les étapes préliminaires plus haut.</span><span class="sxs-lookup"><span data-stu-id="d39ca-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span>

<span data-ttu-id="d39ca-147">Pour savoir comment écrire votre propre service d’application UWP, consultez [Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="d39ca-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="d39ca-148">Vous devrez apporter quelques modifications pour rendre le service compatible avec Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="d39ca-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="d39ca-149">Consultez le [Guide UWP pour les services d’application distants](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour savoir comment procéder.</span><span class="sxs-lookup"><span data-stu-id="d39ca-149">See the [UWP guide for remote app services](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="d39ca-150">Ouvrir une connexion de service d’application sur l’appareil client</span><span class="sxs-lookup"><span data-stu-id="d39ca-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="d39ca-151">Votre application iOS doit acquérir une référence à un appareil ou application distants.</span><span class="sxs-lookup"><span data-stu-id="d39ca-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="d39ca-152">Comme dans la section relative au lancement, ce scénario nécessite l’utilisation d’un objet **MCDRemoteSystemConnectionRequest**, qui peut être construit à partir d’un objet **MCDRemoteSystem** ou **MCDRemoteSystemApp** représentant une application disponible sur le système.</span><span class="sxs-lookup"><span data-stu-id="d39ca-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="d39ca-153">De plus, votre application devra identifier son service d’application cible avec deux chaînes : le *nom du service d’application* et l’*identificateur de package*.</span><span class="sxs-lookup"><span data-stu-id="d39ca-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="d39ca-154">Celles-ci se trouvent dans le code source du fournisseur de service d’application (consultez [Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations).</span><span class="sxs-lookup"><span data-stu-id="d39ca-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="d39ca-155">Ensemble, ces chaînes constituent **MCDAppServiceDescription**, qui est chargé dans une instance de **MCDAppServiceConnection**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

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


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="d39ca-156">Créer un message à envoyer au service d’application</span><span class="sxs-lookup"><span data-stu-id="d39ca-156">Create a message to send to the app service</span></span>

<span data-ttu-id="d39ca-157">Déclarez une variable pour y stocker le message à envoyer.</span><span class="sxs-lookup"><span data-stu-id="d39ca-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="d39ca-158">Sur iOS, les messages que vous envoyez à des services d’application distants sont de type **NSDictionary**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="d39ca-159">Quand votre application communique avec les services d’application d’autres plateformes, la Plateforme d’appareils connectés traduit l’objet **NSDictionary** en construction équivalente sur la plateforme de réception.</span><span class="sxs-lookup"><span data-stu-id="d39ca-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="d39ca-160">Par exemple, un objet **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** envoyé à partir de cette application à un service d’application Windows est traduit en objet [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) (du .NET Framework), qui peut ensuite être interprété par le service d’application.</span><span class="sxs-lookup"><span data-stu-id="d39ca-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="d39ca-161">Les informations transmises dans l’autre direction font l’objet d’une traduction inverse.</span><span class="sxs-lookup"><span data-stu-id="d39ca-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="d39ca-162">La méthode suivante façonne un message qui peut être interprété par le service d’application de l’application de test Roman pour Windows.</span><span class="sxs-lookup"><span data-stu-id="d39ca-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="d39ca-163">Les objets **NSDictionary** qui sont transmis entre les applications et les services dans le scénario des services d’application distants doivent respecter le format suivant : Les clés doivent être des chaînes **NSString** et les valeurs peuvent être les suivantes : **NSString**, types numériques convertis (boxed) (entiers ou virgules flottante), valeurs booléennes converties (boxed), **NSDate**, **NSUUID**, tableaux homogènes d’un de ces types ou autres objets **NSDictionary**  qui respectent cette spécification.</span><span class="sxs-lookup"><span data-stu-id="d39ca-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString** s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="d39ca-164">Envoyer des message au service d’application</span><span class="sxs-lookup"><span data-stu-id="d39ca-164">Send messages to the app service</span></span>

<span data-ttu-id="d39ca-165">Une fois que la connexion au service d’application est établie et que le message est créé, il est facile de l’envoyer au service d’application. Cela peut se faire de n’importe où dans l’application à condition de disposer d’une référence à l’instance de connexion et du message.</span><span class="sxs-lookup"><span data-stu-id="d39ca-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="d39ca-166">Le code suivant tiré de l’exemple illustre l’envoi d’un message à un service d’application et le traitement de la réponse.</span><span class="sxs-lookup"><span data-stu-id="d39ca-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

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

<span data-ttu-id="d39ca-167">Dans le cas de l’application Roman, la réponse contient la date de sa création. S’agissant d’un cas d’utilisation très simple, nous pouvons comparer les dates pour obtenir la durée totale de transit de la réponse au message.</span><span class="sxs-lookup"><span data-stu-id="d39ca-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="d39ca-168">Cela met fin à un échange de messages unique avec un service d’application distant.</span><span class="sxs-lookup"><span data-stu-id="d39ca-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="d39ca-169">Terminer la communication du service d’application</span><span class="sxs-lookup"><span data-stu-id="d39ca-169">Finish app service communication</span></span>

<span data-ttu-id="d39ca-170">Une fois que votre application a achevé son interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.</span><span class="sxs-lookup"><span data-stu-id="d39ca-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="d39ca-171">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d39ca-171">Related topics</span></span>
* [<span data-ttu-id="d39ca-172">Page de référence des API</span><span class="sxs-lookup"><span data-stu-id="d39ca-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="d39ca-173">Exemple d’application iOS</span><span class="sxs-lookup"><span data-stu-id="d39ca-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="d39ca-174">Communiquer avec un service d’application distant (UWP)</span><span class="sxs-lookup"><span data-stu-id="d39ca-174">Communicate with a remote app service (UWP)</span></span>](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="d39ca-175">[Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)</span><span class="sxs-lookup"><span data-stu-id="d39ca-175">[Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>