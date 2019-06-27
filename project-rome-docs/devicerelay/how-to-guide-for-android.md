---
title: Commander des appareils et des applications distants (Android)
description: Ce guide vous explique comment découvrir des appareils et des applications distants et comment lancer ensuite des applications ou interagir avec des services d’application.
ms.topic: article
keywords: microsoft, windows, projet rome, commandes, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 9ca9caf60c59c619d1f7ec4e7b3af529acbb2ffc
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755751"
---
# <a name="implementing-device-relay-for-android"></a>Implémentation de relais d’appareils pour Android

La fonctionnalité Relais d’appareils du projet Rome se compose d’un ensemble d’API qui prennent en charge les deux principales fonctionnalités : le lancement à distance (aussi appelé commandes) et les services d’application distants.

Les API de lancement à distance prennent en charge les scénarios dans lesquels un processus est démarré sur un appareil distant à partir d’un appareil local. Par exemple, un utilisateur écoute la radio sur son téléphone en voiture, mais une fois à la maison, il bascule la lecture de son téléphone vers sa Xbox qui est raccordée à sa chaîne stéréo.

Les API App Services permettent à une application d’établir un pipeline persistant entre deux appareils qui permet l’envoi de messages comportant du contenu arbitraire. Par exemple, l’utilisateur pourrait établir une connexion entre l’application de partage de photos qui s’exécute sur son appareil mobile et son PC en vue de récupérer des photos.

Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées au relais d’appareils à l’aide de la plateforme.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Utilisation de la plateforme

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Découvrir les appareils et les applications distants

Une instance de **RemoteSystemWatcher** gérera la principale fonctionnalité de cette section. Déclarez-la dans la classe qui doit découvrir les systèmes distants.

```Java
private RemoteSystemWatcher mWatcher = null;
```

Avant de créer un observateur et de lancer la découverte d’appareils, vous pouvez souhaiter ajouter des filtres de découverte pour déterminer les types d’appareil que votre application doit cibler. Ils peuvent être déterminés par entrée utilisateur ou codés en dur dans l’application, selon votre cas d’utilisation.

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

À ce stade, l’application peut initialiser l’objet observateur qui détermine la façon dont votre application analyse et interagit avec les appareils découverts.

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

De préférence, votre application doit tenir à jour un ensemble d’appareils découverts (représentés par des instances de **RemoteSystem**) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, le nom d’affichage et le type d’appareil) dans l’interface utilisateur. 

Les stubs de classe suivants peuvent servir d’écouteurs d’événements pour l’instance d’observateur.

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

Une fois `mWatcher.start` appelé, il se met à observer l’activité du système distant et déclenche des événements quand des appareils sont découverts, mis à jour ou supprimés de l’ensemble d’appareils découverts. Sachant que l’observateur poursuit son analyse en arrière-plan, il est recommandé de l’arrêter dès que cela n’est plus nécessaire pour éviter de consommer des ressources de communication réseau et de batterie.

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Exemple de cas d’utilisation : implémentation du lancement à distance et de services d’application distants

À ce stade, votre code doit comporter une liste opérationnelle d’objets **RemoteSystem** qui font référence aux appareils disponibles. Ce à quoi vont vous servir ces appareils dépend de la fonction de votre application. Les principaux types d’interaction sont le lancement à distance et les services d’application distants. Ils vous sont expliqués dans les sections suivantes.

### <a name="a-remote-launching"></a>A) Lancement à distance

Le code suivant montre comment sélectionner un de ces appareils (dans l’idéal, via un contrôle d’interface utilisateur) et utilise ensuite **RemoteLauncher** pour lancer une application sur cet appareil en lui transmettant un URI compatible avec l’application. 

Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lance l’URI donné avec son application par défaut pour ce schéma d’URI) _ou_ une application distante spécifique sur cet appareil. 

Comme nous l’avons vu dans la section précédente, la découverte se produit d’abord au niveau de l’appareil (un objet **RemoteSystem** représente un appareil), mais vous pouvez appeler la méthode `getApplications` sur une instance de **RemoteSystem** pour obtenir un tableau d’objets **RemoteSystemApp**, qui représentent les applications de l’appareil distant qui ont été inscrites pour utiliser la Plateforme d’appareils connectés (de la même façon que vous avez inscrit votre propre application dans les étapes préliminaires décrites plus haut). Les objets **RemoteSystem** et **RemoteSystemApp** peuvent servir à construire un **RemoteSystemConnectionRequest**, qui est nécessaire au lancement d’un URI.

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
Utilisez l’**AsyncOperation** retourné pour traiter le résultat de la tentative de lancement.

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
Selon l’URI qui est envoyé, vous pouvez lancer une application dans un état ou une configuration spécifiques sur un appareil distant. Cela donne la possibilité de poursuivre une tâche d’utilisateur, comme regarder un film, sur un autre appareil sans interruption. 

Selon votre cas d’utilisation, vous devrez peut-être prévoir les cas où aucune application du système ciblé ne peut gérer l’URI et ceux où plusieurs applications peuvent le gérer. Les classes **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** et **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** décrivent comment faire.

### <a name="b-remote-app-services"></a>B) Services d’application distants

Votre application Android peut utiliser le portail Appareils connectés pour interagir avec des services d’application sur d’autres appareils. Cela donne la possibilité de communiquer de diverses façons avec d’autres appareils, tout cela sans qu’il soit nécessaire de placer une application au premier plan de l’appareil hôte. 

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurer le service d’application sur l’appareil cible
Ce guide utilise l’[application de test Roman pour Windows](http://aka.ms/romeapp) comme service d’application cible. Par conséquent, le code ci-dessous conduit une application Android à rechercher ce service d’application spécifique sur le système distant donné. Si vous souhaitez tester ce scénario, téléchargez l’application de test Roman sur un appareil Windows et veillez à vous connecter avec le compte MSA que vous avez utilisé dans les étapes préliminaires décrites plus haut. 

Pour savoir comment écrire votre propre service d’application UWP, consultez [Créer et utiliser un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Vous devrez apporter quelques modifications pour rendre le service compatible avec Appareils connectés. Consultez le [Guide UWP pour les services d’application distants](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour savoir comment procéder. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Ouvrir une connexion de service d’application sur l’appareil client
Votre application Android doit acquérir une référence à un appareil ou une application distants. Comme dans la section relative au lancement, ce scénario nécessite l’utilisation d’un objet **RemoteSystemConnectionRequest**, qui peut être construit à partir d’un objet **RemoteSystem** ou **RemoteSystemApp** représentant une application disponible sur le système.


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
De plus, votre application devra identifier son service d’application cible avec deux chaînes : le *nom du service d’application* et l’*identificateur de package*. Celles-ci se trouvent dans le code source du fournisseur de service d’application (consultez [Créer et utiliser un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour savoir comment obtenir ces chaînes pour les services d’application Windows). Ensemble, ces chaînes constituent **AppServiceDescription**, qui est chargé dans une instance de **AppServiceConnection**.

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

#### <a name="create-a-message-to-send-to-the-app-service"></a>Créer un message à envoyer au service d’application

Déclarez une variable pour y stocker le message à envoyer. Sur Android, les messages que vous envoyez à des services d’application distants sont de type **Map**.

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> Quand votre application communique avec les services d’application d’autres plateformes, la Plateforme d’appareils connectés traduit l’objet **Map** en construction correspondante sur la plateforme de réception. Par exemple, un objet **[Map](https://developer.android.com/reference/java/util/Map)** envoyé à un service d’application Windows à partir de cette application est traduit en objet [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (du .NET Framework), qui peut ensuite être interprété par le service d’application. Les informations transmises dans l’autre direction font l’objet de la traduction inverse.

La méthode suivante compose un message qui peut être interprété par le service d’application de l’application de test Roman pour Windows.

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
> Les objets **Map** qui sont transmis entre les applications et les services dans le scénario de services d’application distants doivent respecter le format suivant : Les clés doivent être des chaînes (Strings) et les valeurs peuvent être les suivantes : chaînes (Strings), types numériques convertis (boxed) (entiers ou virgules flottantes), valeurs booléennes converties (boxed), android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, tableaux homogènes d’un de ces types ou autres objets **Map** respectant cette spécification.

#### <a name="send-message-to-the-app-service"></a>Envoyer le message au service d’application

Une fois que la connexion au service d’application est établie et que le message est créé, il est facile de l’envoyer au service d’application n’importe où dans l’application où figure une référence à l’instance de connexion au service d’application et le message.


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

La réponse du service d’application est reçue et interprétée par la méthode suivante.

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
Dans le cas de l’application Roman, la réponse contient la date de sa création. S’agissant d’un cas d’utilisation très simple, nous pouvons comparer les dates pour obtenir la durée totale de transit de la réponse au message.

Cela met fin à un échange de messages unique avec un service d’application distant.

#### <a name="finish-app-service-communication"></a>Terminer la communication du service d’application

Une fois que votre application a achevé son interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a>Rubriques connexes
* [Page de référence des API](api-reference-for-android.md) 
* [Exemple d’application Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [Communiquer avec un service d’application distant (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Créer et utiliser un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
