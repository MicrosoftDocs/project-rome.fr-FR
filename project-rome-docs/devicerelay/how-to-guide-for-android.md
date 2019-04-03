---
title: Commandes appareils distants et les applications (Android)
description: Ce guide explique comment découvrir des applications et des appareils à distance et lancer des applications ou interagir avec les services d’application.
ms.topic: article
keywords: Microsoft, windows, project rome, exécution des commandes, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 78cb712d3b1cbbd3d613a45cd42af491eaa33afc
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907761"
---
# <a name="implementing-device-relay-for-android"></a>Implémentation de relais d’appareil pour Android

La fonctionnalité de relais de l’appareil de Project Rome se compose d’un ensemble d’API qui prennent en charge les deux fonctionnalités principales : lancement à distance (également appelés commandes) et les services d’application.

API de lancement à distance prennent en charge les scénarios où un processus sur un appareil distant est démarré à partir d’un périphérique local. Par exemple, un utilisateur peut écouter la radio sur leur téléphone dans la voiture, mais quand ils obtiennent accueil ils utilisent leur téléphone pour transférer la lecture à leur Xbox qui est relié à la chaîne stéréo.

API de Services d’application permettent à une application établir un pipeline persistant entre les deux appareils par le biais duquel les messages contenant n’importe quel contenu arbitraire peuvent être envoyés. Par exemple, une application qui s’exécute sur un appareil mobile de partage de photos peut établir une connexion avec des PC de l’utilisateur afin de récupérer les photos.

Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter le périphérique relais fonctionnalités associées.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>À l’aide de la plateforme

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Découvrir les applications et des périphériques distants

Un **RemoteSystemWatcher** instance gère la fonctionnalité principale de cette section. Déclarez-le dans la classe qui consiste à découvrir des systèmes distants.

```Java
private RemoteSystemWatcher mWatcher = null;
```

Avant de créer un observateur et démarrer la découverte des périphériques, vous pouvez souhaiter ajouter des filtres de détection pour déterminer quels types de périphériques de votre application ciblera. Ils peuvent être déterminés par l’utilisateur d’entrée ou codé en dur dans l’application, en fonction de votre cas d’utilisation.

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

À ce stade, l’application peut initialiser l’objet de l’Observateur qui déterminent comment votre application allez-vous analyser et interagir avec les appareils qui sont détectées.

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

Il est recommandé que votre application conserver un ensemble de périphériques détectés (représenté par **RemoteSystem** instances) et afficher des informations sur les appareils disponibles et leurs applications (par exemple, de type nom et le périphérique d’affichage) sur l’interface utilisateur. 

Les stubs de classe suivante peuvent servir d’écouteurs d’événements pour l’instance de l’Observateur.

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

Une fois `mWatcher.start` est appelée, elle commencera surveille l’activité du système distant et déclenche des événements lorsque les appareils sont détectés, mis à jour ou la suppression de l’ensemble des périphériques détectés. Il analyse en continu en arrière-plan, il est recommandé d’arrêter l’Observateur lorsque vous n’avez plus besoin afin d’éviter de drainage de communication et de la batterie inutiles sur le réseau.

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Exemple de cas d’usage : implémentation de lancement à distance et les services d’application à distance

À ce stade dans votre code, vous devez avoir une liste de travail de **RemoteSystem** les objets qui font référence à des appareils disponibles. Ce que vous faire avec ces périphériques dépendra de la fonction de votre application. Les principaux types d’interaction sont lancement à distance et les services d’application à distance. Ils sont expliqués dans les sections suivantes.

### <a name="a-remote-launching"></a>A) le lancement à distance

Le code suivant montre comment sélectionner un de ces appareils (dans l’idéal, ceci s’effectue via un contrôle d’interface utilisateur), puis utilisez **RemoteLauncher** pour lancer une application dessus en transmettant une URI d’application compatible. 

Il est important de noter qu’un lancement à distance peut cibler un appareil distant (auquel cas l’appareil hôte lancera l’URI donné avec son application par défaut pour ce modèle d’URI) _ou_ une application spécifique à distance sur cet appareil. 

Comme la section précédente décrivait, détection se produit au niveau du périphérique tout d’abord (un **RemoteSystem** représente un périphérique), mais vous pouvez appeler la `getApplications` méthode sur un **RemoteSystem** instance pour obtenir une tableau de **RemoteSystemApp** objets qui représentent des applications sur l’appareil à distance qui ont été inscrits pour utiliser la plateforme d’appareils connectés (comme vous avez inscrit votre propre application dans les étapes préliminaires ci-dessus). Les deux **RemoteSystem** et **RemoteSystemApp** peut être utilisé pour construire un **RemoteSystemConnectionRequest**, qui est ce qui est nécessaire pour lancer un URI.

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
Utilisez retourné **AsyncOperation** pour gérer le résultat de la tentative de lancement.

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
En fonction de l’URI qui est envoyé, vous pouvez lancer une application dans un état spécifique ou la configuration sur un périphérique distant. Cela permet la capacité à poursuivre une tâche de l’utilisateur, telles que regarder un film, sur un autre appareil sans interruption. 

Selon votre cas d’utilisation, vous devrez peut-être couvrir les cas dans lequel aucune application sur le système cible ne peut gérer l’URI, ou plusieurs applications peuvent le gérer. Le **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** classe et **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** classe décrivent comment effectuer cette opération.

### <a name="b-remote-app-services"></a>B) services d’application à distance

Votre application Android peut utiliser le portail de périphériques connectés interagir avec les services d’application sur d’autres appareils. Cela fournit de nombreuses façons de communiquer avec d’autres appareils&mdash;tout cela sans avoir besoin de migrer une application au premier plan de l’appareil hôte. 

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurer le service d’application sur l’appareil cible
Ce guide utilise les [Roman application Test pour Windows](http://aka.ms/romeapp) en tant que son service d’application cible. Par conséquent, le code ci-dessous génère une application Android pour rechercher ce service d’application spécifique sur le système distant donné. Si vous souhaitez tester ce scénario, téléchargez l’application de Test Roman sur un appareil Windows et assurez-vous que vous êtes connecté avec le même compte de service administré ou AAD que vous avez utilisé dans les étapes préliminaires ci-dessus. 

Pour obtenir des instructions sur la façon d’écrire votre propre service d’application UWP, consultez [créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Vous devrez apporter quelques modifications afin que le service compatible avec les appareils connectés. Consultez le [guide UWP pour les services d’application à distance](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) pour obtenir des instructions sur la procédure à suivre. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Ouvrir une connexion de service d’application sur le périphérique client
Votre application Android doit acquérir une référence à un périphérique distant ou une application. Comme la section de lancement, ce scénario requiert l’utilisation d’un **RemoteSystemConnectionRequest**, ce qui peut être construit à partir de l’un **RemoteSystem** ou un **RemoteSystemApp**représentant une application disponible sur le système.


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
En outre, votre application a besoin identifier son service d’application ciblée à l’aide de deux chaînes : le *nom app service* et *identificateur de package*. Ceux-ci sont trouvent dans le code source du fournisseur de services d’application (consultez [créer et consommer un service d’application (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations sur la façon d’obtenir ce chaînes pour les services d’application Windows). Ces chaînes créent le **AppServiceDescription**, qui est chargé dans un **AppServiceConnection** instance.

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

Déclarez une variable pour stocker le message à envoyer. Sur Android, les messages que vous envoyez aux services d’application à distance sera de la **carte** type.

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> Lorsque votre application communique avec les services d’application sur d’autres plateformes, la plateforme d’appareils connectés traduit la **carte** dans la construction de correspondance sur la plateforme de réception. Par exemple, un **[carte](https://developer.android.com/reference/java/util/Map)** envoyé à partir de cette application à un Windows service d’application est alors traduite en une [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objet (du .NET Framework), qui peut ensuite être interprété par le service d’application. Informations passées dans l’autre sens subit la traduction inverse.

La méthode suivante compose un message qui peut être interprété par app service l’application Test Roman pour Windows.

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
> Le **carte**s qui sont passés entre les applications et services dans le scénario de services d’application à distance doit respecter le format suivant : Les clés doivent être des chaînes et les valeurs peuvent être : Converti (boxed) des boxed de types numériques (entiers ou points flottante), chaînes, valeurs booléennes, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, tableaux homogènes d’une de ces types, ou d’autres **carte** objets répondre à cette spécification.

#### <a name="send-message-to-the-app-service"></a>Envoyer un message au service d’application

Une fois la connexion de service d’application est établie et que le message est créé, envoyer vers le service d’application est simple et peut être effectuée depuis n’importe où dans l’application qui a une référence à l’instance de connexion app service et le message.


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

Réponse du service de l’application sera reçue et interprétée par la méthode suivante.

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
Dans le cas de Roman application, la réponse contient la date de que sa création, donc dans ce cas d’usage très simple, nous pouvons comparer les dates pour obtenir l’heure de transit totale de la réponse du message.

Ceci conclut un échange de messages unique avec un service d’application à distance.

#### <a name="finish-app-service-communication"></a>Terminer la communication de service d’application

Lorsque votre application est terminée interaction avec le service d’application de l’appareil cible, fermez la connexion entre les deux appareils.

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a>Rubriques connexes
* [Page de référence des API](api-reference-for-android.md) 
* [Exemple Android d’application](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [Communiquer avec un service d’application à distance (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Créer et consommer un service d’application (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).
