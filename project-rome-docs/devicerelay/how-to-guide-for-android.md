---
title: Commandes appareils distants et les applications (Android)
description: Ce guide explique comment découvrir des applications et des appareils à distance et lancer des applications ou interagir avec les services d’application.
ms.topic: article
keywords: Microsoft, windows, project rome, exécution des commandes, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 9ca9caf60c59c619d1f7ec4e7b3af529acbb2ffc
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755751"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="1ce52-104">Implémentation de relais d’appareil pour Android</span><span class="sxs-lookup"><span data-stu-id="1ce52-104">Implementing device relay for Android</span></span>

<span data-ttu-id="1ce52-105">La fonctionnalité de relais de l’appareil de Project Rome se compose d’un ensemble d’API qui prennent en charge les deux fonctionnalités principales : lancement à distance (également appelés commandes) et les services d’application.</span><span class="sxs-lookup"><span data-stu-id="1ce52-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="1ce52-106">API de lancement à distance prennent en charge les scénarios où un processus sur un appareil distant est démarré à partir d’un périphérique local.</span><span class="sxs-lookup"><span data-stu-id="1ce52-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="1ce52-107">Par exemple, un utilisateur peut écouter la radio sur leur téléphone dans la voiture, mais quand ils obtiennent accueil ils utilisent leur téléphone pour transférer la lecture à leur Xbox qui est relié à la chaîne stéréo.</span><span class="sxs-lookup"><span data-stu-id="1ce52-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="1ce52-108">API de Services d’application permettent à une application établir un pipeline persistant entre les deux appareils par le biais duquel les messages contenant n’importe quel contenu arbitraire peuvent être envoyés.</span><span class="sxs-lookup"><span data-stu-id="1ce52-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="1ce52-109">Par exemple, une application qui s’exécute sur un appareil mobile de partage de photos peut établir une connexion avec des PC de l’utilisateur afin de récupérer les photos.</span><span class="sxs-lookup"><span data-stu-id="1ce52-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="1ce52-110">Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="1ce52-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="1ce52-111">Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter le périphérique relais fonctionnalités associées.</span><span class="sxs-lookup"><span data-stu-id="1ce52-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="1ce52-112">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="1ce52-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="1ce52-113">À l’aide de la plateforme</span><span class="sxs-lookup"><span data-stu-id="1ce52-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="1ce52-114">Découvrir les applications et des périphériques distants</span><span class="sxs-lookup"><span data-stu-id="1ce52-114">Discover remote devices and apps</span></span>

<span data-ttu-id="1ce52-115">Un **RemoteSystemWatcher** instance gère la fonctionnalité principale de cette section.</span><span class="sxs-lookup"><span data-stu-id="1ce52-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="1ce52-116">Déclarez-le dans la classe qui consiste à découvrir des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="1ce52-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="1ce52-117">Avant de créer un observateur et démarrer la découverte des périphériques, vous pouvez souhaiter ajouter des filtres de détection pour déterminer quels types de périphériques de votre application ciblera.</span><span class="sxs-lookup"><span data-stu-id="1ce52-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="1ce52-118">Ils peuvent être déterminés par l’utilisateur d’entrée ou codé en dur dans l’application, en fonction de votre cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="1ce52-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

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

<span data-ttu-id="1ce52-119">À ce stade, l’application peut initialiser l’objet de l’Observateur qui déterminent comment votre application allez-vous analyser et interagir avec les appareils qui sont détectées.</span><span class="sxs-lookup"><span data-stu-id="1ce52-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="1ce52-120">Il est recommandé que votre application conserver un ensemble de périphériques détectés (représenté par **RemoteSystem** instances) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, de type nom et le périphérique d’affichage) sur l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ce52-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="1ce52-121">Les stubs de classe suivante peuvent servir d’écouteurs d’événements pour l’instance de l’Observateur.</span><span class="sxs-lookup"><span data-stu-id="1ce52-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

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

<span data-ttu-id="1ce52-122">Une fois `mWatcher.start` est appelée, elle commencera surveille l’activité du système distant et déclenche des événements lorsque les appareils sont détectés, mis à jour ou la suppression de l’ensemble des périphériques détectés.</span><span class="sxs-lookup"><span data-stu-id="1ce52-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="1ce52-123">Il analyse en continu en arrière-plan, il est recommandé d’arrêter l’Observateur lorsque vous n’avez plus besoin afin d’éviter de drainage de communication et de la batterie inutiles sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="1ce52-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="1ce52-124">Exemple de cas d’usage : implémentation de lancement à distance et les services d’application à distance</span><span class="sxs-lookup"><span data-stu-id="1ce52-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="1ce52-125">À ce stade dans votre code, vous devez avoir une liste de travail de **RemoteSystem** les objets qui font référence à des appareils disponibles.</span><span class="sxs-lookup"><span data-stu-id="1ce52-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="1ce52-126">Ce que vous faire avec ces périphériques dépendra de la fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="1ce52-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="1ce52-127">Les principaux types d’interaction sont lancement à distance et les services d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="1ce52-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="1ce52-128">Ils sont expliqués dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="1ce52-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="1ce52-129">A) le lancement à distance</span><span class="sxs-lookup"><span data-stu-id="1ce52-129">A) Remote launching</span></span>

<span data-ttu-id="1ce52-130">Le code suivant montre comment sélectionner un de ces appareils (dans l’idéal, ceci s’effectue via un contrôle d’interface utilisateur), puis utilisez **RemoteLauncher** pour lancer une application dessus en transmettant une URI d’application compatible.</span><span class="sxs-lookup"><span data-stu-id="1ce52-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="1ce52-131">Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lancera l’URI donné avec son application par défaut pour ce modèle d’URI) _ou_ une application spécifique à distance sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="1ce52-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="1ce52-132">Comme la section précédente décrivait, détection se produit au niveau du périphérique tout d’abord (un **RemoteSystem** représente un périphérique), mais vous pouvez appeler la `getApplications` méthode sur un **RemoteSystem** instance pour obtenir une tableau de **RemoteSystemApp** objets qui représentent des applications sur l’appareil à distance qui ont été inscrits pour utiliser la plateforme d’appareils connectés (comme vous avez inscrit votre propre application dans les étapes préliminaires ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="1ce52-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="1ce52-133">Les deux **RemoteSystem** et **RemoteSystemApp** peut être utilisé pour construire un **RemoteSystemConnectionRequest**, qui est ce qui est nécessaire pour lancer un URI.</span><span class="sxs-lookup"><span data-stu-id="1ce52-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

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
<span data-ttu-id="1ce52-134">Utilisez retourné **AsyncOperation** pour gérer le résultat de la tentative de lancement.</span><span class="sxs-lookup"><span data-stu-id="1ce52-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

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
<span data-ttu-id="1ce52-135">En fonction de l’URI qui est envoyé, vous pouvez lancer une application dans un état spécifique ou la configuration sur un périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="1ce52-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="1ce52-136">Cela permet la capacité à poursuivre une tâche de l’utilisateur, telles que regarder un film, sur un autre appareil sans interruption.</span><span class="sxs-lookup"><span data-stu-id="1ce52-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="1ce52-137">Selon votre cas d’utilisation, vous devrez peut-être couvrir les cas dans lequel aucune application sur le système cible ne peut gérer l’URI, ou plusieurs applications peuvent le gérer.</span><span class="sxs-lookup"><span data-stu-id="1ce52-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="1ce52-138">Le **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** classe et **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** classe décrivent comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="1ce52-138">The **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="1ce52-139">B) services d’application à distance</span><span class="sxs-lookup"><span data-stu-id="1ce52-139">B) Remote app services</span></span>

<span data-ttu-id="1ce52-140">Votre application Android peut utiliser le portail de périphériques connectés interagir avec les services d’application sur d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="1ce52-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="1ce52-141">Cela fournit de nombreuses façons de communiquer avec d’autres appareils&mdash;tout cela sans avoir besoin de migrer une application au premier plan de l’appareil hôte.</span><span class="sxs-lookup"><span data-stu-id="1ce52-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="1ce52-142">Configurer le service d’application sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="1ce52-142">Set up the app service on the target device</span></span>
<span data-ttu-id="1ce52-143">Ce guide utilise les [Roman application Test pour Windows](http://aka.ms/romeapp) en tant que son service d’application cible.</span><span class="sxs-lookup"><span data-stu-id="1ce52-143">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="1ce52-144">Par conséquent, le code ci-dessous génère une application Android pour rechercher ce service d’application spécifique sur le système distant donné.</span><span class="sxs-lookup"><span data-stu-id="1ce52-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="1ce52-145">Si vous souhaitez tester ce scénario, téléchargez l’application de Test Roman sur un appareil Windows et vérifiez que vous êtes connecté avec le même MSA que vous avez utilisé dans les étapes préliminaires ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1ce52-145">If you wish to test this scenario,download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="1ce52-146">Pour obtenir des instructions sur la façon d’écrire votre propre service d’application UWP, consultez [créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="1ce52-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="1ce52-147">Vous devrez apporter quelques modifications afin que le service compatible avec les appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="1ce52-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="1ce52-148">Consultez le [guide UWP pour les services d’application à distance](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour obtenir des instructions sur la procédure à suivre.</span><span class="sxs-lookup"><span data-stu-id="1ce52-148">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="1ce52-149">Ouvrir une connexion de service d’application sur le périphérique client</span><span class="sxs-lookup"><span data-stu-id="1ce52-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="1ce52-150">Votre application Android doit acquérir une référence à un périphérique distant ou une application.</span><span class="sxs-lookup"><span data-stu-id="1ce52-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="1ce52-151">Comme la section de lancement, ce scénario requiert l’utilisation d’un **RemoteSystemConnectionRequest**, ce qui peut être construit à partir de l’un **RemoteSystem** ou un **RemoteSystemApp**représentant une application disponible sur le système.</span><span class="sxs-lookup"><span data-stu-id="1ce52-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="1ce52-152">En outre, votre application a besoin identifier son service d’application ciblée à l’aide de deux chaînes : le *nom app service* et *identificateur de package*.</span><span class="sxs-lookup"><span data-stu-id="1ce52-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="1ce52-153">Ceux-ci sont trouvent dans le code source du fournisseur de services d’application (consultez [créer et consommer un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations sur la façon d’obtenir ce chaînes pour les services d’application Windows).</span><span class="sxs-lookup"><span data-stu-id="1ce52-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="1ce52-154">Ces chaînes créent le **AppServiceDescription**, qui est chargé dans un **AppServiceConnection** instance.</span><span class="sxs-lookup"><span data-stu-id="1ce52-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

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

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="1ce52-155">Créer un message à envoyer au service d’application</span><span class="sxs-lookup"><span data-stu-id="1ce52-155">Create a message to send to the app service</span></span>

<span data-ttu-id="1ce52-156">Déclarez une variable pour stocker le message à envoyer.</span><span class="sxs-lookup"><span data-stu-id="1ce52-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="1ce52-157">Sur Android, les messages que vous envoyez aux services d’application à distance sera de la **carte** type.</span><span class="sxs-lookup"><span data-stu-id="1ce52-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="1ce52-158">Lorsque votre application communique avec les services d’application sur d’autres plateformes, la plateforme d’appareils connectés traduit la **carte** dans la construction de correspondance sur la plateforme de réception.</span><span class="sxs-lookup"><span data-stu-id="1ce52-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="1ce52-159">Par exemple, un **[carte](https://developer.android.com/reference/java/util/Map)** envoyé à partir de cette application à un Windows service d’application est alors traduite en une [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objet (du .NET Framework), qui peut ensuite être interprété par le service d’application.</span><span class="sxs-lookup"><span data-stu-id="1ce52-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="1ce52-160">Informations passées dans l’autre sens subit la traduction inverse.</span><span class="sxs-lookup"><span data-stu-id="1ce52-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="1ce52-161">La méthode suivante compose un message qui peut être interprété par app service l’application Test Roman pour Windows.</span><span class="sxs-lookup"><span data-stu-id="1ce52-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="1ce52-162">Le **carte**s qui sont passés entre les applications et services dans le scénario de services d’application à distance doit respecter le format suivant : Les clés doivent être des chaînes et les valeurs peuvent être : Converti (boxed) des boxed de types numériques (entiers ou points flottante), chaînes, valeurs booléennes, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, tableaux homogènes d’une de ces types, ou d’autres **carte** objets répondre à cette spécification.</span><span class="sxs-lookup"><span data-stu-id="1ce52-162">The **Map**s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="1ce52-163">Envoyer un message au service d’application</span><span class="sxs-lookup"><span data-stu-id="1ce52-163">Send message to the app service</span></span>

<span data-ttu-id="1ce52-164">Une fois la connexion de service d’application est établie et que le message est créé, envoyer vers le service d’application est simple et peut être effectuée depuis n’importe où dans l’application qui a une référence à l’instance de connexion app service et le message.</span><span class="sxs-lookup"><span data-stu-id="1ce52-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


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

<span data-ttu-id="1ce52-165">Réponse du service de l’application sera reçue et interprétée par la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="1ce52-165">The app service's response will be received and interpreted by the following method.</span></span>

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
<span data-ttu-id="1ce52-166">Dans le cas de Roman application, la réponse contient la date de que sa création, donc dans ce cas d’usage très simple, nous pouvons comparer les dates pour obtenir l’heure de transit totale de la réponse du message.</span><span class="sxs-lookup"><span data-stu-id="1ce52-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="1ce52-167">Ceci conclut un échange de messages unique avec un service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="1ce52-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="1ce52-168">Terminer la communication de service d’application</span><span class="sxs-lookup"><span data-stu-id="1ce52-168">Finish app service communication</span></span>

<span data-ttu-id="1ce52-169">Lorsque votre application est terminée interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.</span><span class="sxs-lookup"><span data-stu-id="1ce52-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="1ce52-170">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="1ce52-170">Related topics</span></span>
* [<span data-ttu-id="1ce52-171">Page de référence des API</span><span class="sxs-lookup"><span data-stu-id="1ce52-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="1ce52-172">Exemple Android d’application</span><span class="sxs-lookup"><span data-stu-id="1ce52-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="1ce52-173">Communiquer avec un service d’application à distance (UWP)</span><span class="sxs-lookup"><span data-stu-id="1ce52-173">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="1ce52-174">[Créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="1ce52-174">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
