---
title: L’intégration d’applications Android avec les Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801201"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="78529-103">Guide pratique : L’intégration avec les Notifications de graphique (Android)</span><span class="sxs-lookup"><span data-stu-id="78529-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="78529-104">Notifications de graphique activer votre application envoyer et gérer les notifications de ciblage d’utilisateur sur plusieurs appareils.</span><span class="sxs-lookup"><span data-stu-id="78529-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="78529-105">Avec le SDK côté client de Project Rome sur Android, votre application Android peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="78529-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="78529-106">Le Kit de développement permet au client de l’application recevoir les nouvelles charges utiles de notification entrant, gérer l’état des notifications existantes et récupérer l’historique de la notification.</span><span class="sxs-lookup"><span data-stu-id="78529-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="78529-107">Pour plus d’informations sur les Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="78529-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="78529-108">Toutes les fonctionnalités dans le SDK de Rome projet includng graphique Notifications et bien plus encore, sont appuient sur une plateforme sous-jacente, appelée la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="78529-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="78529-109">Ce guide est conçu pour vous guider à travers les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés et d’expliquer comment utiliser des API dans le Kit de développement pour implémenter des Notifications de graphique-fonctionnalités spécifiques.</span><span class="sxs-lookup"><span data-stu-id="78529-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="78529-110">Consultez le [référence de l’API](api-reference-for-android.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="78529-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="78529-111">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="78529-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="78529-112">Initialiser un canal de Notification de graphique</span><span class="sxs-lookup"><span data-stu-id="78529-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="78529-113">Le Kit de développement logiciel Project Rome permet à votre application pour vous abonner à différents canaux afin de recevoir et gérer les différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="78529-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="78529-114">Il s’agit tout stockée et synchronisé dans **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="78529-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="78529-115">**UserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique.</span><span class="sxs-lookup"><span data-stu-id="78529-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="78529-116">Pour intégrer avec Notification de graphique et recevoir des UserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="78529-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="78529-117">Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).</span><span class="sxs-lookup"><span data-stu-id="78529-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="78529-118">Les méthodes suivantes d’initialiser un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="78529-118">The following methods initialize a **UserNotificationChannel**.</span></span>

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
<span data-ttu-id="78529-119">À ce stade, vous devez avoir un **UserNotificationChannel** référencer dans `mNotificationChannel`.</span><span class="sxs-lookup"><span data-stu-id="78529-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="78529-120">Créer un UserNotificationReader pour recevoir des UserNotifications entrantes et accéder à l’historique UserNotification</span><span class="sxs-lookup"><span data-stu-id="78529-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="78529-121">Comme nous vous avons montré précédemment, la notification initiale Google Cloud Messaging arrivant sur l’application client contient uniquement un drainage de l’épaule, et vous devez transmettre cette charge utile tap d’épaule à la plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le Appareil serveur relié, qui contient tous les UserNotifications publiées par le serveur de votre application.</span><span class="sxs-lookup"><span data-stu-id="78529-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="78529-122">Cela abaisse la charge utile de notification complète publiée par votre serveur d’application correspondant à cette tap épaule (et dans le cas si les notifications précédentes ont été publiées mais pas reçues sur ce client de l’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront extrait vers le bas également).</span><span class="sxs-lookup"><span data-stu-id="78529-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="78529-123">Avec ces synchronisations en temps réel en permanence effectuées par le Kit de développement, le client de l’application est en mesure d’accéder à un cache local des flux de données UserNotification connecté l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78529-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="78529-124">Dans ce cas un UserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection UserNotification complète qui peut être utilisée en tant que modèle de vue de l’historique de notification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78529-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="78529-125">Réception UserNotifications</span><span class="sxs-lookup"><span data-stu-id="78529-125">Receiving UserNotifications</span></span>
<span data-ttu-id="78529-126">Vous devez d’abord instancier un UserNotificationReader et obtenir toutes les UserNotifications existantes déjà dans le lecteur si vous vous intéressez lors de la consommation de ces informations pour l’expérience que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="78529-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="78529-127">Il est recommandé de toujours supposer que le serveur d’application a déjà publié des notifications à celui-ci connecté utilisateur, étant donné que ce point de terminaison de périphérique particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé votre application.</span><span class="sxs-lookup"><span data-stu-id="78529-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
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
<span data-ttu-id="78529-128">Maintenant, ajoutez un écouteur d’événements qui se déclenche quand la plateforme d’appareils connectés se termine une synchronisation et a des modifications apportées à vous en informer.</span><span class="sxs-lookup"><span data-stu-id="78529-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="78529-129">Dans le cas des Notifications de graphique, les nouvelles modifications peut être nouveau UserNotifications entrantes publiées par votre suppressions du serveur ou les mises à jour UserNotifcation, application et délais d’expiration qui se sont produits à partir du serveur ou des autres inscrit les points de terminaison qui a le même utilisateur connecté dans.</span><span class="sxs-lookup"><span data-stu-id="78529-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="78529-130">Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="78529-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="78529-131">Si vous utilisez actuellement un message de données de Google Cloud Messaging pour construire une notification visual dans la barre d’état de la notification au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="78529-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="78529-132">Mettre à jour l’état d’une UserNotification existante</span><span class="sxs-lookup"><span data-stu-id="78529-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="78529-133">Dans la section précédente, nous avons mentionné que parfois une modification UserNotification reçue via le lecteur peut être une mise à jour de l’état sur une UserNotification existante – si marquée comme dismissed ou marqués comme lus.</span><span class="sxs-lookup"><span data-stu-id="78529-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="78529-134">Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique.</span><span class="sxs-lookup"><span data-stu-id="78529-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="78529-135">Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification UserNotification pour commencer : à partir d’un autre appareil.</span><span class="sxs-lookup"><span data-stu-id="78529-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="78529-136">Vous pouvez choisir le moment pour mettre à jour l’état de votre UserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application que vous activez .</span><span class="sxs-lookup"><span data-stu-id="78529-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="78529-137">Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="78529-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="78529-138">L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="78529-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="78529-139">Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de le correspondante UserNotification afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78529-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="78529-140">Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action.</span><span class="sxs-lookup"><span data-stu-id="78529-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="78529-141">Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78529-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="78529-142">Classe de UserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="78529-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="78529-143">Par exemple, vous pouvez marquer UserActionState pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel.</span><span class="sxs-lookup"><span data-stu-id="78529-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="78529-144">Vous pouvez également, ou en même temps vous pouvez marquer état ReadState comme lu ou non lu et en fonction de qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application.</span><span class="sxs-lookup"><span data-stu-id="78529-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="78529-145">Code ci-dessous extrait de code montre comment marquer le UserNotificationUserActionState d’une notification en tant qu’ignoré.</span><span class="sxs-lookup"><span data-stu-id="78529-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
