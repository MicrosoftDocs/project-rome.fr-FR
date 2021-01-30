---
title: Commander des appareils et des applications distants (Android)
description: Ce guide vous explique comment découvrir des appareils et des applications distants et comment lancer ensuite des applications ou interagir avec des services d’application.
ms.topic: article
keywords: microsoft, windows, projet rome, commandes, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: ce261c6571e4606ddcb8e1c2b75d989db51d8d9f
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901556"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="94749-104">Implémentation de relais d’appareils pour Android</span><span class="sxs-lookup"><span data-stu-id="94749-104">Implementing device relay for Android</span></span>

<span data-ttu-id="94749-105">La fonctionnalité Relais d’appareils du projet Rome se compose d’un ensemble d’API qui prennent en charge les deux principales fonctionnalités : le lancement à distance (aussi appelé commandes) et les services d’application distants.</span><span class="sxs-lookup"><span data-stu-id="94749-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="94749-106">Les API de lancement à distance prennent en charge les scénarios dans lesquels un processus est démarré sur un appareil distant à partir d’un appareil local.</span><span class="sxs-lookup"><span data-stu-id="94749-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="94749-107">Par exemple, un utilisateur écoute la radio sur son téléphone en voiture, mais une fois à la maison, il bascule la lecture de son téléphone vers sa Xbox qui est raccordée à sa chaîne stéréo.</span><span class="sxs-lookup"><span data-stu-id="94749-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="94749-108">Les API App Services permettent à une application d’établir un pipeline persistant entre deux appareils qui permet l’envoi de messages comportant du contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="94749-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="94749-109">Par exemple, l’utilisateur pourrait établir une connexion entre l’application de partage de photos qui s’exécute sur son appareil mobile et son PC en vue de récupérer des photos.</span><span class="sxs-lookup"><span data-stu-id="94749-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="94749-110">Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="94749-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="94749-111">Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées au relais d’appareils à l’aide de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="94749-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="94749-112">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="94749-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="94749-113">Utilisation de la plateforme</span><span class="sxs-lookup"><span data-stu-id="94749-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="94749-114">Découvrir les appareils et les applications distants</span><span class="sxs-lookup"><span data-stu-id="94749-114">Discover remote devices and apps</span></span>

<span data-ttu-id="94749-115">Une instance de **RemoteSystemWatcher** gérera la principale fonctionnalité de cette section.</span><span class="sxs-lookup"><span data-stu-id="94749-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="94749-116">Déclarez-la dans la classe qui doit découvrir les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="94749-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="94749-117">Avant de créer un observateur et de lancer la découverte d’appareils, vous pouvez souhaiter ajouter des filtres de découverte pour déterminer les types d’appareil que votre application doit cibler.</span><span class="sxs-lookup"><span data-stu-id="94749-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="94749-118">Ils peuvent être déterminés par entrée utilisateur ou codés en dur dans l’application, selon votre cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="94749-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

```Java
private void onStartWatcherClicked() {
    // RemoteSystemWatcher cannot be started unless the platform is 
    // initialized and the user is logged in. It may be helpful to use
    // methods like these to track the state of the application.
    // See the sample app for their implementations.
    if (!getMainActivity().isSignedIn()) {
        return;
    }
    if (!getMainActivity().isPlatformInitialized()) {
        return;
    }

    // create and populate a list of filters. The filter choices below are arbitrary.
    ArrayList<RemoteSystemFilter> filters = new ArrayList<>();

    /*  RemoteSystemDiscoveryType filters can be used to filter the types of Remote Systems you discover.
    Possible values:
        ANY(0),
        PROXIMAL(1),
        CLOUD(2),
        SPATIALLY_PROXIMAL(3)
    */
    filters.add(new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.ANY));

    /*  RemoteSystemStatusType filters can be used to filter the status of Remote Systems you discover.
    Possible values:
        ANY(0),
        AVAILABLE(1)
    */
    filters.add(new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.AVAILABLE));


    /*  RemoteSystemKindFilter can filter the types of devices you want to discover.
    Possible values are members of the RemoteSystemKinds class.
    */
    String[] kinds = new String[] { RemoteSystemKinds.Phone(), RemoteSystemKinds.Tablet() };

    RemoteSystemKindFilter kindFilter = new RemoteSystemKindFilter(kinds);
    filters.add(kindFilter);

    /*  RemoteSystemAuthorizationKind determines the category of user whose system(s) you want to discover.
    Possible values:
        SAME_USER(0),
        ANONYMOUS(1)
    */
    filters.add(new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SAME_USER)); 
    // ...
```

<span data-ttu-id="94749-119">À ce stade, l’application peut initialiser l’objet observateur qui détermine la façon dont votre application analyse et interagit avec les appareils découverts.</span><span class="sxs-lookup"><span data-stu-id="94749-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="94749-120">De préférence, votre application doit tenir à jour un ensemble d’appareils découverts (représentés par des instances de **RemoteSystem**) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, le nom d’affichage et le type d’appareil) dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94749-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="94749-121">Les stubs de classe suivants peuvent servir d’écouteurs d’événements pour l’instance d’observateur.</span><span class="sxs-lookup"><span data-stu-id="94749-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

```Java
private class RemoteSystemAddedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // add instance "remoteSystem" to program memory. See sample for full implementation.
    }
}

private class RemoteSystemUpdatedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // update instance "remoteSystem" in program memory. See sample for full implementation.
    }
}

private class RemoteSystemRemovedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // remove instance "remoteSystem" from program memory. See sample for full implementation.
    }
}

private class RemoteSystemWatcherErrorOccurredListener implements EventListener<RemoteSystemWatcher, RemoteSystemWatcherError> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystemWatcherError remoteSystemWatcherError) {
        // handle the error
    }
}
```

<span data-ttu-id="94749-122">Une fois `mWatcher.start` appelé, il se met à observer l’activité du système distant et déclenche des événements quand des appareils sont découverts, mis à jour ou supprimés de l’ensemble d’appareils découverts.</span><span class="sxs-lookup"><span data-stu-id="94749-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="94749-123">Sachant que l’observateur poursuit son analyse en arrière-plan, il est recommandé de l’arrêter dès que cela n’est plus nécessaire pour éviter de consommer des ressources de communication réseau et de batterie.</span><span class="sxs-lookup"><span data-stu-id="94749-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

```Java
// if you call this from the activity's onPause method, you ensure that
// it will stop when the activity exits the foreground.
public void stopWatcher() {
    if (mWatcher == null) {
        return;
    }
    mWatcher.stop();
}
```
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="94749-124">Exemple de cas d’utilisation : implémentation du lancement à distance et de services d’application distants</span><span class="sxs-lookup"><span data-stu-id="94749-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="94749-125">À ce stade, votre code doit comporter une liste opérationnelle d’objets **RemoteSystem** qui font référence aux appareils disponibles.</span><span class="sxs-lookup"><span data-stu-id="94749-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="94749-126">Ce à quoi vont vous servir ces appareils dépend de la fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="94749-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="94749-127">Les principaux types d’interaction sont le lancement à distance et les services d’application distants.</span><span class="sxs-lookup"><span data-stu-id="94749-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="94749-128">Ils vous sont expliqués dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="94749-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="94749-129">A) Lancement à distance</span><span class="sxs-lookup"><span data-stu-id="94749-129">A) Remote launching</span></span>

<span data-ttu-id="94749-130">Le code suivant montre comment sélectionner un de ces appareils (dans l’idéal, via un contrôle d’interface utilisateur) et utilise ensuite **RemoteLauncher** pour lancer une application sur cet appareil en lui transmettant un URI compatible avec l’application.</span><span class="sxs-lookup"><span data-stu-id="94749-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="94749-131">Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lance l’URI donné avec son application par défaut pour ce schéma d’URI) _ou_ une application distante spécifique sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="94749-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="94749-132">Comme nous l’avons vu dans la section précédente, la découverte se produit d’abord au niveau de l’appareil (un objet **RemoteSystem** représente un appareil), mais vous pouvez appeler la méthode `getApplications` sur une instance de **RemoteSystem** pour obtenir un tableau d’objets **RemoteSystemApp**, qui représentent les applications de l’appareil distant qui ont été inscrites pour utiliser la Plateforme d’appareils connectés (de la même façon que vous avez inscrit votre propre application dans les étapes préliminaires décrites plus haut).</span><span class="sxs-lookup"><span data-stu-id="94749-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="94749-133">Les objets **RemoteSystem** et **RemoteSystemApp** peuvent servir à construire un **RemoteSystemConnectionRequest**, qui est nécessaire au lancement d’un URI.</span><span class="sxs-lookup"><span data-stu-id="94749-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

```java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the launch operation
// is called.
private RemoteSystem target; 

// ...

/**
* Responsible for calling into the Rome API to launch the given URI and provides
* the logic to handle the RemoteLaunchUriStatus response.
* @param uri URI to launch
* @param target The target for the launch URI request
*/
private void launchUri(final String uri, final RemoteSystem target, final long messageId)
{
    RemoteLauncher remoteLauncher = new RemoteLauncher();

    AsyncOperation<RemoteLaunchUriStatus> resultOperation = remoteLauncher.launchUriAsync(new RemoteSystemConnectionRequest(target), uri);
    // ...
```
<span data-ttu-id="94749-134">Utilisez l’**AsyncOperation** retourné pour traiter le résultat de la tentative de lancement.</span><span class="sxs-lookup"><span data-stu-id="94749-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

```Java
    // ...
    resultOperation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<RemoteLaunchUriStatus, Throwable>() {
        @Override
        public void accept(RemoteLaunchUriStatus status, Throwable throwable) throws Throwable {
            if (throwable != null) {
                // handle the exception, referencing "throwable"
            } else {
                if (status == RemoteLaunchUriStatus.SUCCESS) {
                    // report the success case
                } else {
                    // report the non-success case, referencing "status"
                }
            }
        }
    });
}
```
<span data-ttu-id="94749-135">Selon l’URI qui est envoyé, vous pouvez lancer une application dans un état ou une configuration spécifiques sur un appareil distant.</span><span class="sxs-lookup"><span data-stu-id="94749-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="94749-136">Cela donne la possibilité de poursuivre une tâche d’utilisateur, comme regarder un film, sur un autre appareil sans interruption.</span><span class="sxs-lookup"><span data-stu-id="94749-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="94749-137">Selon votre cas d’utilisation, vous devrez peut-être prévoir les cas où aucune application du système ciblé ne peut gérer l’URI et ceux où plusieurs applications peuvent le gérer.</span><span class="sxs-lookup"><span data-stu-id="94749-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="94749-138">Les classes **[RemoteLauncher](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** et **[RemoteLauncherOptions](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** décrivent comment faire.</span><span class="sxs-lookup"><span data-stu-id="94749-138">The **[RemoteLauncher](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="94749-139">B) Services d’application distants</span><span class="sxs-lookup"><span data-stu-id="94749-139">B) Remote app services</span></span>

<span data-ttu-id="94749-140">Votre application Android peut utiliser le portail Appareils connectés pour interagir avec des services d’application sur d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="94749-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="94749-141">Cela donne la possibilité de communiquer de diverses façons avec d’autres appareils, tout cela sans qu’il soit nécessaire de placer une application au premier plan de l’appareil hôte.</span><span class="sxs-lookup"><span data-stu-id="94749-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="94749-142">Configurer le service d’application sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="94749-142">Set up the app service on the target device</span></span>
<span data-ttu-id="94749-143">Ce guide utilise l’[application de test Roman pour Windows](https://aka.ms/romeapp) comme service d’application cible.</span><span class="sxs-lookup"><span data-stu-id="94749-143">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="94749-144">Par conséquent, le code ci-dessous conduit une application Android à rechercher ce service d’application spécifique sur le système distant donné.</span><span class="sxs-lookup"><span data-stu-id="94749-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="94749-145">Si vous souhaitez tester ce scénario, téléchargez l’application de test Roman sur un appareil Windows et veillez à vous connecter avec le compte MSA que vous avez utilisé dans les étapes préliminaires décrites plus haut.</span><span class="sxs-lookup"><span data-stu-id="94749-145">If you wish to test this scenario,download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="94749-146">Pour savoir comment écrire votre propre service d’application UWP, consultez [Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="94749-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="94749-147">Vous devrez apporter quelques modifications pour rendre le service compatible avec Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="94749-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="94749-148">Consultez le [Guide UWP pour les services d’application distants](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour savoir comment procéder.</span><span class="sxs-lookup"><span data-stu-id="94749-148">See the [UWP guide for remote app services](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="94749-149">Ouvrir une connexion de service d’application sur l’appareil client</span><span class="sxs-lookup"><span data-stu-id="94749-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="94749-150">Votre application Android doit acquérir une référence à un appareil ou une application distants.</span><span class="sxs-lookup"><span data-stu-id="94749-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="94749-151">Comme dans la section relative au lancement, ce scénario nécessite l’utilisation d’un objet **RemoteSystemConnectionRequest**, qui peut être construit à partir d’un objet **RemoteSystem** ou **RemoteSystemApp** représentant une application disponible sur le système.</span><span class="sxs-lookup"><span data-stu-id="94749-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="94749-152">De plus, votre application devra identifier son service d’application cible avec deux chaînes : le *nom du service d’application* et l’*identificateur de package*.</span><span class="sxs-lookup"><span data-stu-id="94749-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="94749-153">Celles-ci se trouvent dans le code source du fournisseur de service d’application (consultez [Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour savoir comment obtenir ces chaînes pour les services d’application Windows).</span><span class="sxs-lookup"><span data-stu-id="94749-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="94749-154">Ensemble, ces chaînes constituent **AppServiceDescription**, qui est chargé dans une instance de **AppServiceConnection**.</span><span class="sxs-lookup"><span data-stu-id="94749-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

```Java
// this is defined below
private AppServiceConnection connection = null; 


/**
* Creates an AppService connection with the current identifier and service name and opens the
* app service connection.
*/
private void onNewConnectionButtonClicked()
{
    connection = new AppServiceConnection();

    // these hard-coded strings must be defined elsewhere in the app
    connection.setAppServiceDescription(new AppServiceDescription(mAppServiceName, mPackageIdentifier));

    // this method is defined below
    openAppServiceConnection();
}
```
```Java
/**
* Establish an app service connection.
* Opens the given AppService connection using the connection request. Once the connection is
* opened, it adds the listeners for request-received and close. Catches all exceptions
* to show behavior of API surface exceptions.
*/
private void openAppServiceConnection()
{
    // optionally report outbound request
    // ...

    RemoteSystemConnectionRequest connectionRequest = new RemoteSystemConnectionRequest(target));

    /* Will asynchronously open the app service connection using the given connection request
    * When this is done, we log the traffic in the UI for visibility to the user (for sample purposes)
    * We can check the status of the connection to determine whether or not it was successful, and show 
    * some UI if it wasn't (in this case it is part of the list item).
    */
    connection.openRemoteAsync(connectionRequest)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceConnectionStatus>() {
            @Override
            public void accept(AppServiceConnectionStatus appServiceConnectionStatus) throws Throwable {
                // optionally report inbound response
                // ...

                if (appServiceConnectionStatus != AppServiceConnectionStatus.SUCCESS) {
                    // report the error, referencing "appServiceConnectionStatus"
                    return;
                }
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception
                return null;
            }
        });
}
```

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="94749-155">Créer un message à envoyer au service d’application</span><span class="sxs-lookup"><span data-stu-id="94749-155">Create a message to send to the app service</span></span>

<span data-ttu-id="94749-156">Déclarez une variable pour y stocker le message à envoyer.</span><span class="sxs-lookup"><span data-stu-id="94749-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="94749-157">Sur Android, les messages que vous envoyez à des services d’application distants sont de type **Map**.</span><span class="sxs-lookup"><span data-stu-id="94749-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="94749-158">Quand votre application communique avec les services d’application d’autres plateformes, la Plateforme d’appareils connectés traduit l’objet **Map** en construction correspondante sur la plateforme de réception.</span><span class="sxs-lookup"><span data-stu-id="94749-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="94749-159">Par exemple, un objet **[Map](https://developer.android.com/reference/java/util/Map)** envoyé à un service d’application Windows à partir de cette application est traduit en objet [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) (du .NET Framework), qui peut ensuite être interprété par le service d’application.</span><span class="sxs-lookup"><span data-stu-id="94749-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="94749-160">Les informations transmises dans l’autre direction font l’objet d’une traduction inverse.</span><span class="sxs-lookup"><span data-stu-id="94749-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="94749-161">La méthode suivante compose un message qui peut être interprété par le service d’application de l’application de test Roman pour Windows.</span><span class="sxs-lookup"><span data-stu-id="94749-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

```Java
/**
* Send the current message payload through all selected AppService connections on a non-UI
* thread as to not block user interaction, a result of the delay between API calls.
*/
private void onMessageButtonClicked()
{
    mMessagePayload = new HashMap<>();
    // Add the required fields of RomanApp on Windows
    DateFormat df = new SimpleDateFormat(DATE_FORMAT);
    mMessagePayload.put("Type", "ping");
    mMessagePayload.put("CreationDate", df.format(new Date()));
    mMessagePayload.put("TargetId", "check if this field needs to be included");

    // this method is defined below.
    sendMessage(connection, mMessagePayload);
}
```

> [!IMPORTANT]
> <span data-ttu-id="94749-162">Les objets **Map** qui sont transmis entre les applications et les services dans le scénario de services d’application distants doivent respecter le format suivant : Les clés doivent être des chaînes (Strings) et les valeurs peuvent être les suivantes : chaînes (Strings), types numériques convertis (boxed) (entiers ou virgules flottantes), valeurs booléennes converties (boxed), android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, tableaux homogènes d’un de ces types ou autres objets **Map** respectant cette spécification.</span><span class="sxs-lookup"><span data-stu-id="94749-162">The **Map** s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="94749-163">Envoyer le message au service d’application</span><span class="sxs-lookup"><span data-stu-id="94749-163">Send message to the app service</span></span>

<span data-ttu-id="94749-164">Une fois que la connexion au service d’application est établie et que le message est créé, il est facile de l’envoyer au service d’application n’importe où dans l’application où figure une référence à l’instance de connexion au service d’application et le message.</span><span class="sxs-lookup"><span data-stu-id="94749-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


```java

// When assigning message IDs, use an incremental counter
private AtomicInteger mMessageIdAppServices = new AtomicInteger(0);

// ...

/**
* Send a message using the app service connection
* Send the given Map object through the given AppServiceConnection. Uses an internal messageId
* for logging purposes.
* @param connection AppServiceConnection to send the Map payload
* @param message Payload to be translated to a ValueSet
*/
private void sendMessage(final AppServiceConnection connection, Map<String, Object> message)
{
    final long messageId = mMessageIdAppServices.incrementAndGet();

    connection.sendMessageAsync(message)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceResponse>() {
            @Override
            public void accept(AppServiceResponse appServiceResponse) throws Throwable {
                // optionally report an inbound response

                // this method is defined below
                handleAppServiceResponse(appServiceResponse, messageId);
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception, referencing "throwable"

                return null;
            }
        });

    // optionally log the outbound message request here, referencing 
    // connection.getAppServiceDescription().getName() as the recipient.
}
```

<span data-ttu-id="94749-165">La réponse du service d’application est reçue et interprétée par la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="94749-165">The app service's response will be received and interpreted by the following method.</span></span>

```Java
private void handleAppServiceResponse(AppServiceResponse appServiceResponse, long messageId)
{
    AppServiceResponseStatus status = appServiceResponse.getStatus();
    if (status == AppServiceResponseStatus.SUCCESS)
    {
        // the message was delivered successfully; interpret the response.
        Map<String, Object> response;
        response = appServiceResponse.getMessage();

        // in the Roman App case, the response contains the date it was created.
        String dateStr = (String)response.get("CreationDate");
        DateFormat df = new SimpleDateFormat(DATE_FORMAT, Locale.getDefault());

        // in this very simple use case, we compare the dates to get the total
        // transit time of the message response.
        try {
            Date startDate = df.parse(dateStr);
            Date nowDate = new Date();
            long diff = nowDate.getTime() - startDate.getTime();
            // do something with "diff"
        } catch (ParseException e) { e.printStackTrace(); }
    }
}
```
<span data-ttu-id="94749-166">Dans le cas de l’application Roman, la réponse contient la date de sa création. S’agissant d’un cas d’utilisation très simple, nous pouvons comparer les dates pour obtenir la durée totale de transit de la réponse au message.</span><span class="sxs-lookup"><span data-stu-id="94749-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="94749-167">Cela met fin à un échange de messages unique avec un service d’application distant.</span><span class="sxs-lookup"><span data-stu-id="94749-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="94749-168">Terminer la communication du service d’application</span><span class="sxs-lookup"><span data-stu-id="94749-168">Finish app service communication</span></span>

<span data-ttu-id="94749-169">Une fois que votre application a achevé son interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.</span><span class="sxs-lookup"><span data-stu-id="94749-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="94749-170">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="94749-170">Related topics</span></span>
* [<span data-ttu-id="94749-171">Page de référence des API</span><span class="sxs-lookup"><span data-stu-id="94749-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="94749-172">Exemple d’application Android</span><span class="sxs-lookup"><span data-stu-id="94749-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="94749-173">Communiquer avec un service d’application distant (UWP)</span><span class="sxs-lookup"><span data-stu-id="94749-173">Communicate with a remote app service (UWP)</span></span>](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="94749-174">[Créer et utiliser un service d’application (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)</span><span class="sxs-lookup"><span data-stu-id="94749-174">[Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>