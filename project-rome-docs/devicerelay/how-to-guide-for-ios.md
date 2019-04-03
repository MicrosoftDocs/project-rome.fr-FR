---
title: Implémentation des fonctionnalités de relais d’appareil pour iOS
description: Ce guide explique comment découvrir des applications et des appareils à distance et lancer des applications ou interagir avec les services d’application.
ms.topic: article
keywords: Microsoft, windows, project rome, exécution des commandes, ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 11596720d9363f0ef29fd9c7bf0ccc5b4db62fae
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907731"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="b7e9e-104">Implémentation de relais d’appareil pour iOS</span><span class="sxs-lookup"><span data-stu-id="b7e9e-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="b7e9e-105">La fonctionnalité de relais de l’appareil de Project Rome se compose d’un ensemble d’API qui prennent en charge les deux fonctionnalités principales : lancement à distance (également appelés commandes) et les services d’application.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="b7e9e-106">API de lancement à distance prennent en charge les scénarios où un processus sur un appareil distant est démarré à partir d’un périphérique local.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="b7e9e-107">Par exemple, un utilisateur peut écouter la radio sur leur téléphone dans la voiture, mais quand ils obtiennent accueil ils utilisent leur téléphone pour transférer la lecture à leur Xbox qui est relié à la chaîne stéréo.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="b7e9e-108">API de Services d’application permettent à une application établir un pipeline persistant entre les deux appareils par le biais duquel les messages contenant n’importe quel contenu arbitraire peuvent être envoyés.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="b7e9e-109">Par exemple, une application qui s’exécute sur un appareil mobile de partage de photos peut établir une connexion avec des PC de l’utilisateur afin de récupérer les photos.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="b7e9e-110">Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="b7e9e-111">Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter fonctionnalités liées à relais de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="b7e9e-112">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="b7e9e-113">Configuration de la plateforme de périphériques connectés et les Notifications</span><span class="sxs-lookup"><span data-stu-id="b7e9e-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="b7e9e-114">À l’aide de la plateforme</span><span class="sxs-lookup"><span data-stu-id="b7e9e-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="b7e9e-115">Découvrir les applications et des périphériques distants</span><span class="sxs-lookup"><span data-stu-id="b7e9e-115">Discover remote devices and apps</span></span>

<span data-ttu-id="b7e9e-116">Un **MCDRemoteSystemWatcher** instance gère la fonctionnalité principale de cette section.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="b7e9e-117">Déclarez-le dans la classe qui consiste à découvrir des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="b7e9e-118">Avant de créer un observateur et démarrer la découverte des périphériques, vous pouvez souhaiter ajouter des filtres de détection pour déterminer quels types de périphériques de votre application ciblera.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="b7e9e-119">Ils peuvent être déterminés par l’utilisateur d’entrée ou codé en dur dans l’application, en fonction de votre cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="b7e9e-120">Le code suivant à partir de l’exemple d’application montre comment créer et démarrer une instance de l’Observateur autoriser votre application analyser et interagir avec les appareils qui sont détectées.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

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

<span data-ttu-id="b7e9e-121">Les méthodes de gestionnaire d’événements sont définis ici.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-121">The event handler methods are defined here.</span></span>

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

<span data-ttu-id="b7e9e-122">Nous conseillons de votre application de conserver un ensemble de périphériques détectés (représenté par **MCDRemoteSystem** instances) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, de type nom et le périphérique d’affichage) sur l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="b7e9e-123">Une fois `[_watcher start]` est appelée, elle commencera surveille l’activité du système distant et déclenche des événements lorsque des appareils connectés sont découverts, mis à jour ou supprimés à partir de l’ensemble des périphériques détectés.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="b7e9e-124">Il analyse en continu en arrière-plan, il est donc recommandé que vous arrêtez l’Observateur (avec `[_watcher stop]`) lorsque vous n’avez plus besoin afin d’éviter de drainage de communication et de la batterie inutiles sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="b7e9e-125">Exemple de cas d’usage : implémentation de lancement à distance et les services d’application à distance</span><span class="sxs-lookup"><span data-stu-id="b7e9e-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="b7e9e-126">À ce stade dans votre code, vous devez avoir une liste de travail de **MCDRemoteSystem** les objets qui font référence à des appareils disponibles.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="b7e9e-127">Ce que vous faire avec ces périphériques dépendra de la fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="b7e9e-128">Les principaux types d’interaction sont lancement à distance et les services d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="b7e9e-129">Ils sont expliqués dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="b7e9e-130">A) le lancement à distance</span><span class="sxs-lookup"><span data-stu-id="b7e9e-130">A) Remote launching</span></span>

<span data-ttu-id="b7e9e-131">Le code suivant montre comment sélectionner un de la **MCDRemoteSystem** objets (dans l’idéal, ceci s’effectue via un contrôle d’interface utilisateur), puis utiliser **MCDRemoteLauncher** pour lancer une application dessus en passant d’une application compatible URI.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="b7e9e-132">Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lancera l’URI donné avec son application par défaut pour ce modèle d’URI) _ou_ une application spécifique à distance sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="b7e9e-133">Comme la section précédente décrivait, détection se produit au niveau du périphérique tout d’abord (un **MCDRemoteSystem** représente un périphérique), mais vous pouvez appeler la `getApplications` méthode sur un **MCDRemoteSystem** instance pour obtenir un tableau de **MCDRemoteSystemApp** objets qui représentent des applications sur l’appareil à distance qui ont été inscrits pour utiliser la plateforme d’appareils connectés (comme vous avez inscrit votre propre application dans les étapes préliminaires ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="b7e9e-134">Les deux **MCDRemoteSystem** et **MCDRemoteSystemApp** peut être utilisé pour construire un **MCDRemoteSystemConnectionRequest**, qui est ce qui est nécessaire pour lancer un URI.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="b7e9e-135">Le code de l’exemple suivant montre le lancement à distance d’un URI sur une demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

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

<span data-ttu-id="b7e9e-136">En fonction de l’URI qui est envoyé, vous pouvez lancer une application dans un état spécifique ou la configuration sur un périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="b7e9e-137">Cela permet la capacité à poursuivre une tâche de l’utilisateur, telles que regarder un film, sur un autre appareil sans interruption.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="b7e9e-138">En fonction de votre utilisation, vous devrez peut-être couvrir les cas dans lequel aucune application sur le système cible ne peut gérer l’URI, ou plusieurs applications peuvent le gérer.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="b7e9e-139">Le **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** classe et **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** classe décrivent comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="b7e9e-140">B) services d’application à distance</span><span class="sxs-lookup"><span data-stu-id="b7e9e-140">B) Remote app services</span></span>

<span data-ttu-id="b7e9e-141">Votre application iOS peut utiliser le portail des appareils connectés pour interagir avec les services d’application sur d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="b7e9e-142">Cela fournit de nombreuses façons de communiquer avec d’autres appareils&mdash;tout cela sans avoir besoin de migrer une application au premier plan de l’appareil hôte.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="b7e9e-143">Configurer le service d’application sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="b7e9e-143">Set up the app service on the target device</span></span>
<span data-ttu-id="b7e9e-144">Ce guide utilise les [Roman application Test pour Windows](http://aka.ms/romeapp) en tant que son service d’application cible.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-144">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="b7e9e-145">Par conséquent, le code ci-dessous génère une application iOS rechercher ce service d’application spécifique sur le système distant donné.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="b7e9e-146">Si vous souhaitez tester ce scénario, téléchargez l’application de Test Roman sur un appareil Windows et assurez-vous que vous êtes connecté avec le même compte de service administré ou AAD que vous avez utilisé dans les étapes préliminaires ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA or AAD that you used in the preliminary steps above.</span></span>

<span data-ttu-id="b7e9e-147">Pour obtenir des instructions sur la façon d’écrire votre propre service d’application UWP, consultez [créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="b7e9e-148">Vous devrez apporter quelques modifications afin que le service compatible avec les appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="b7e9e-149">Consultez le [guide UWP pour les services d’application à distance](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour obtenir des instructions sur la procédure à suivre.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-149">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="b7e9e-150">Ouvrir une connexion de service d’application sur le périphérique client</span><span class="sxs-lookup"><span data-stu-id="b7e9e-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="b7e9e-151">Votre application iOS doit acquérir une référence à un périphérique distant ou une application.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="b7e9e-152">Comme la section de lancement, ce scénario requiert l’utilisation d’un **MCDRemoteSystemConnectionRequest**, ce qui peut être construit à partir de l’un **MCDRemoteSystem** ou un **MCDRemoteSystemApp**  représentant une application disponible sur le système.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="b7e9e-153">En outre, votre application a besoin identifier son service de l’application ciblée par deux chaînes : le *nom app service* et *identificateur de package*.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="b7e9e-154">Ceux-ci sont trouvent dans le code source du fournisseur de services d’application (consultez [créer et consommer un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="b7e9e-155">Ces chaînes créent le **MCDAppServiceDescription**, qui est chargé dans un **MCDAppServiceConnection** instance.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

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


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="b7e9e-156">Créer un message à envoyer au service d’application</span><span class="sxs-lookup"><span data-stu-id="b7e9e-156">Create a message to send to the app service</span></span>

<span data-ttu-id="b7e9e-157">Déclarez une variable pour stocker le message à envoyer.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="b7e9e-158">Sur iOS, les messages que vous envoyez aux services d’application à distance sera de la **NSDictionary** type.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="b7e9e-159">Lorsque votre application communique avec les services d’application sur d’autres plateformes, la plateforme d’appareils connectés traduit la **NSDictionary** dans la construction équivalente sur la plateforme de réception.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="b7e9e-160">Par exemple, un **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** envoyé à partir de cette application à un Windows service d’application est alors traduite en une [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objet (de .NET Framework), qui peut ensuite être interprété par le service d’application.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="b7e9e-161">Informations passées dans l’autre sens subit la traduction inverse.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="b7e9e-162">La méthode suivante crée un message qui peut être interprété par app service l’application Test Roman pour Windows.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="b7e9e-163">Le **NSDictionary** objets qui sont passés entre les applications et services dans le scénario de services d’application à distance doivent respecter le format suivant : Les clés doivent être **chaîne NSString**s et les valeurs peuvent être : **Chaîne NSString**, boxed de types numériques (entiers ou points flottante), boxed de valeurs booléennes, **NSDate**, **NSUUID**, tableaux homogènes d’une de ces types, ou d’autres **NSDictionary**  objets qui répondent à cette spécification.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString**s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="b7e9e-164">Envoyer des messages au service d’application</span><span class="sxs-lookup"><span data-stu-id="b7e9e-164">Send messages to the app service</span></span>

<span data-ttu-id="b7e9e-165">Une fois la connexion de service d’application est établie et que le message est créé, envoyer vers le service d’application est simple et peut être effectuée depuis n’importe où dans l’application qui a une référence à l’instance de la connexion et le message.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="b7e9e-166">Le code suivant à partir de l’exemple montre l’envoi d’un message à un service d’application et la gestion de la réponse.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

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

<span data-ttu-id="b7e9e-167">Dans le cas de Roman application, la réponse contient la date de que sa création, donc dans ce cas d’usage très simple, nous pouvons comparer les dates pour obtenir l’heure de transit totale de la réponse du message.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="b7e9e-168">Ainsi se conclut un échange de messages unique avec un service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="b7e9e-169">Terminer la communication de service d’application</span><span class="sxs-lookup"><span data-stu-id="b7e9e-169">Finish app service communication</span></span>

<span data-ttu-id="b7e9e-170">Lorsque votre application est terminée interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="b7e9e-171">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b7e9e-171">Related topics</span></span>
* [<span data-ttu-id="b7e9e-172">Page de référence des API</span><span class="sxs-lookup"><span data-stu-id="b7e9e-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="b7e9e-173">exemple d’application iOS</span><span class="sxs-lookup"><span data-stu-id="b7e9e-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="b7e9e-174">Communiquer avec un service d’application à distance (UWP)</span><span class="sxs-lookup"><span data-stu-id="b7e9e-174">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="b7e9e-175">[Créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-175">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
