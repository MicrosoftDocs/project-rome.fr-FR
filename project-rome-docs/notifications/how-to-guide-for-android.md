---
title: Intégration d’applications Android à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801201"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="20df2-103">Guides pratique : Intégration à la fonctionnalité Notifications Graph (Android)</span><span class="sxs-lookup"><span data-stu-id="20df2-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="20df2-104">Les notifications Graph permettent à votre application d’envoyer et de gérer des notifications ciblant l’utilisateur sur plusieurs appareils.</span><span class="sxs-lookup"><span data-stu-id="20df2-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="20df2-105">Avec le SDK côté client Projet Rome sur Android, votre application Android peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’applications ciblant un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="20df2-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="20df2-106">Le SDK permet au client d’application de recevoir les nouvelles charges utiles de notification entrante, gérer l’état des notifications existantes et récupérer l’historique des notifications.</span><span class="sxs-lookup"><span data-stu-id="20df2-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="20df2-107">Pour plus d’informations sur la fonctionnalité Notifications et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="20df2-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="20df2-108">Toutes les fonctionnalités du SDK Projet Rome, notamment Notifications Graph, reposent sur une plateforme sous-jacente appelée « Plateforme d’appareils connectés ».</span><span class="sxs-lookup"><span data-stu-id="20df2-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="20df2-109">Ce guide est conçu de façon à vous guider tout au long des étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés et à expliquer comment utiliser les API du SDK afin d’implémenter des fonctionnalités spécifiques aux notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="20df2-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="20df2-110">Consultez la page [Informations de référence sur les API](api-reference-for-android.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="20df2-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="20df2-111">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="20df2-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="20df2-112">Initialiser un canal de notification Graph</span><span class="sxs-lookup"><span data-stu-id="20df2-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="20df2-113">Le SDK Projet Rome permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="20df2-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="20df2-114">Ils sont tous stockés et synchronisés dans **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="20df2-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="20df2-115">**UserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="20df2-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="20df2-116">Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un UserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="20df2-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="20df2-117">Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).</span><span class="sxs-lookup"><span data-stu-id="20df2-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="20df2-118">Les méthodes suivantes initialisent un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="20df2-118">The following methods initialize a **UserNotificationChannel**.</span></span>

```Java
private UserNotificationChannel mNotificationChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserNotificationFeed.
 */
public void initializeUserNotificationFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserNotificationChannel.getSyncScope() };

    // Get a reference to the UserDataFeed. This method is defined below
    mUserDataFeed = getUserDataFeed(scopes, new EventListener<UserDataFeed, Void>() {
        @Override
        public void onEvent(UserDataFeed userDataFeed, Void aVoid) {
            if (userDataFeed.getSyncStatus() == UserDataSyncStatus.SYNCHRONIZED) {
                // log synchronized.
            } else {
                // log synchronization not completed.
            }
        }
    });

    // this method is defined below
    mNotificationChannel = getUserNotificationChannel();
}

// instantiate the UserDataFeed
private UserDataFeed getUserDataFeed(SyncScope[] scopes, EventListener<UserDataFeed, Void> listener) {
    UserAccount[] accounts = AccountProviderBroker.getSignInHelper().getUserAccounts();
    if (accounts.length <= 0) {
        // notify the user that sign-in is required
        return null;
    }

    // use the initialized Platform instance, along with the cross-device app ID.
    UserDataFeed feed = UserDataFeed.getForAccount(accounts[0], PlatformBroker.getPlatform(), Secrets.APP_HOST_NAME);
    feed.addSyncStatusChangedListener(listener);
    feed.addSyncScopes(scopes);
    // sync data with the server
    feed.startSync();
    return feed;
}

// use the UserDataFeed reference to create a UserActivityChannel
@Nullable
private UserNotificationChannel getUserNotificationChannel() {
    UserNotificationChannel channel = null;
    try {
        // create a UserNotificationChannel for the signed in account
        channel = new UserNotificationChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```
<span data-ttu-id="20df2-119">À ce stade, vous devez avoir une référence à **UserNotificationChannel** dans `mNotificationChannel`.</span><span class="sxs-lookup"><span data-stu-id="20df2-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="20df2-120">Créer un UserNotificationReader pour recevoir des UserNotification entrants et accéder à l’historique des UserNotification</span><span class="sxs-lookup"><span data-stu-id="20df2-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="20df2-121">Comme nous l’avons montré précédemment, la notification Google Cloud Messaging initiale arrivant sur le client d’application contient uniquement un passage de relais, et vous devez transmettre cette charge utile en passage de relais à la Plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le serveur d’appareils connectés, lequel contient tous les UserNotifications publiés par votre serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="20df2-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="20df2-122">Cette opération extrait la charge utile de notification complète publiée par votre serveur d’applications correspondant à ce passage de relais (et dans le cas où des notifications précédentes ont été publiées mais pas reçues sur ce client d’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront également extraites).</span><span class="sxs-lookup"><span data-stu-id="20df2-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="20df2-123">Avec ces synchronisations en temps réel effectuées en permanence par le SDK, le client d’application est en mesure d’accéder à un cache local de ce flux de données UserNotification de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="20df2-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="20df2-124">Dans ce cas, un UserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments UserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="20df2-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="20df2-125">Réception de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="20df2-125">Receiving UserNotifications</span></span>
<span data-ttu-id="20df2-126">Vous devez d’abord instancier un UserNotificationReader et obtenir tous les UserNotifications existants dans le lecteur si la consommation de ces informations pour l’expérience que vous essayez d’activer vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="20df2-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="20df2-127">Étant donné que ce point de terminaison d’appareil particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé sur votre application, nous pouvons toujours présumer sans risque que le serveur d’applications a déjà publié des notifications à cet utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="20df2-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
```Java
private static UserNotificationReader mReader;
private static final ArrayList<UserNotification> mHistoricalNotifications = new ArrayList<>();
// Instantiate UserNotificationReader
UserNotificationReaderOptions options = new UserNotificationReaderOptions();
mReader = mNotificationChannel.createReaderWithOptions(options);
// Read any previously published UserNotifications that have not expired yet
mReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
    @Override
    public void accept(UserNotification[] userNotifications) throws Throwable {
        synchronized (mHistoricalNotifications) {
            for (UserNotification notification : userNotifications) {
                if (notification.getReadState() == UserNotificationReadState.UNREAD) {
                    mHistoricalNotifications.add(notification);
                }
            }
        }
 
        if (RunnableManager.getHistoryUpdated() != null) {
            activity.runOnUiThread(RunnableManager.getHistoryUpdated());
        }
    }
});

```
<span data-ttu-id="20df2-128">Maintenant, ajoutez un détecteur d’événements qui se déclenche quand la Plateforme d’appareils connectés effectue une synchronisation et qu’elle doit vous informer de nouveaux changements.</span><span class="sxs-lookup"><span data-stu-id="20df2-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="20df2-129">Dans le cas de la fonctionnalité Notifications Graph, les nouveaux changements peuvent être de nouveaux UserNotifications entrants publiés par votre serveur d’applications, ou des mises à jour, suppressions et expirations d’éléments UserNotifcation qui se sont produits à partir du serveur ou à partir d’autres points de terminaison inscrits auxquels le même utilisateur s’est connecté.</span><span class="sxs-lookup"><span data-stu-id="20df2-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="20df2-130">Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="20df2-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="20df2-131">Si vous utilisez actuellement un message de données de Google Cloud Messaging pour construire une notification visuelle dans la barre de notification au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela.</span><span class="sxs-lookup"><span data-stu-id="20df2-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
```Java
mReader.addDataChangedListener(new EventListener<UserNotificationReader, Void>() {
    @Override
    public void onEvent(UserNotificationReader userNotificationReader, Void aVoid) {
        userNotificationReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
        @Override
        public void accept(UserNotification[] userNotifications) throws Throwable {
            boolean updatedNew = false;
            boolean updatedHistorical = false;
            synchronized (sHistoricalNotifications) {
                for (final UserNotification notification : userNotifications) {
                    if (notification.getStatus() == UserNotificationStatus.ACTIVE && notification.getReadState() == UserNotificationReadState.UNREAD) {
                        switch (notification.getUserActionState()) {
                            case NO_INTERACTION:
                                // Brand new notification
                                // Insert business logic to construct a new visual notification in Android notification tray for the user to see
                                // ...
                            case DISMISSED:
                                // Existing notification that is marked as dismissed
                                // An app client receive this type of changes because another app client logged in by the same user has marked the notification as dismissed and the change is fanned-out to everywhere
                                // This state sync across app clients on different devices enable universal dismiss of notifications and other scenarios across multiple devices owned by the same user
                                // Insert business logic to dismiss the corresponding visual notification inside Android system notification tray, to make sure users don’t have to deal with redundant information across devices, and potentially insert this notification in your app’s notification history view
                                // ...
                            default:
                                // Unexpected
                        }
                    } else {
                        // ...
                    }
                }
            }
        }
    });
}
});

```
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="20df2-132">Mettre à jour l’état d’un UserNotification existant</span><span class="sxs-lookup"><span data-stu-id="20df2-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="20df2-133">Dans la section précédente, nous avons mentionné qu’un changement de UserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un UserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu).</span><span class="sxs-lookup"><span data-stu-id="20df2-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="20df2-134">Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier.</span><span class="sxs-lookup"><span data-stu-id="20df2-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="20df2-135">Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de UserNotification pour commencer.</span><span class="sxs-lookup"><span data-stu-id="20df2-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="20df2-136">Vous pouvez choisir le moment où mettre à jour l’état de vos UserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez.</span><span class="sxs-lookup"><span data-stu-id="20df2-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="20df2-137">Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="20df2-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="20df2-138">L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="20df2-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="20df2-139">Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état du UserNotification correspondant afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="20df2-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="20df2-140">Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="20df2-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="20df2-141">Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="20df2-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="20df2-142">La classe UserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="20df2-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="20df2-143">Par exemple, vous pouvez marquer UserActionState comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel.</span><span class="sxs-lookup"><span data-stu-id="20df2-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="20df2-144">Alternativement ou simultanément, vous pouvez marquer ReadState comme Read (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application.</span><span class="sxs-lookup"><span data-stu-id="20df2-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="20df2-145">L’extrait de code ci-dessous montre comment marquer le UserNotificationUserActionState d’une notification comme Dismissed (Masqué).</span><span class="sxs-lookup"><span data-stu-id="20df2-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
