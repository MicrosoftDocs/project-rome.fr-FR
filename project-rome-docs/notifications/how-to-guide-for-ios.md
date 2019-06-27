---
title: Intégration d’applications iOS à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801311"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="ea9ae-103">Guides pratique : Intégration à la fonctionnalité Notifications Graph (iOS)</span><span class="sxs-lookup"><span data-stu-id="ea9ae-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="ea9ae-104">Les notifications Graph permettent à votre application d’envoyer et de gérer des notifications ciblant l’utilisateur sur plusieurs appareils.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="ea9ae-105">Avec le SDK côté client Projet Rome sur iOS, votre application iOS peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’applications ciblant un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="ea9ae-106">Le SDK permet au client d’application de recevoir les nouvelles charges utiles de notification entrante, gérer l’état des notifications existantes et récupérer l’historique des notifications.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="ea9ae-107">Pour plus d’informations sur la fonctionnalité Notifications et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="ea9ae-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="ea9ae-108">Toutes les fonctionnalités du SDK Projet Rome, notamment Notifications Graph, reposent sur une plateforme sous-jacente appelée « Plateforme d’appareils connectés ».</span><span class="sxs-lookup"><span data-stu-id="ea9ae-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="ea9ae-109">Ce guide est conçu de façon à vous guider tout au long des étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés et à expliquer comment utiliser les API du SDK afin d’implémenter des fonctionnalités spécifiques aux notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="ea9ae-110">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="ea9ae-111">Consultez la page [Informations de référence sur les API](api-reference-for-ios/index.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="ea9ae-112">Configuration de la Plateforme d’appareils connectés et des notifications</span><span class="sxs-lookup"><span data-stu-id="ea9ae-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="ea9ae-113">Utilisation de la plateforme</span><span class="sxs-lookup"><span data-stu-id="ea9ae-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="ea9ae-114">Initialiser un canal de notification Graph</span><span class="sxs-lookup"><span data-stu-id="ea9ae-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="ea9ae-115">Le SDK Projet Rome permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="ea9ae-116">Ils sont tous stockés et synchronisés dans **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="ea9ae-117">**MCDUserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="ea9ae-118">Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un MCDUserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="ea9ae-119">Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).</span><span class="sxs-lookup"><span data-stu-id="ea9ae-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="ea9ae-120">Les méthodes suivantes initialisent un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
```ObjectiveC
// You must be logged in to use UserNotifications
NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
if (accounts.count > 0)
{
    // Get a UserNotification channel, getting the default channel
    NSLog(@"Creating UserNotificationChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserNotificationChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must log in to receive notifications for the logged in user!");
    self.createNotificationStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="ea9ae-121">À ce stade, vous devez avoir une référence à **MCDUserNotificationChannel** dans `channel`.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="ea9ae-122">Créer un MCDUserNotificationReader pour recevoir des MCDUserNotification entrants et accéder à l’historique des MCDUserNotification</span><span class="sxs-lookup"><span data-stu-id="ea9ae-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="ea9ae-123">Comme nous l’avons montré précédemment, le message silencieux APNS initial arrivant sur le client d’application contient uniquement un passage de relais, et vous devez transmettre cette charge utile en passage de relais à la Plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le serveur d’appareils connectés, lequel contient tous les MCDUserNotifications publiés par votre serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="ea9ae-124">Cette opération extrait la charge utile de notification complète publiée par votre serveur d’applications correspondant à ce passage de relais (et dans le cas où des notifications précédentes ont été publiées mais pas reçues sur ce client d’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront également extraites).</span><span class="sxs-lookup"><span data-stu-id="ea9ae-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="ea9ae-125">Avec ces synchronisations en temps réel effectuées en permanence par le SDK, le client d’application est en mesure d’accéder à un cache local de ce flux de données MCDUserNotification de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="ea9ae-126">Dans ce cas, un MCDUserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments MCDUserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="ea9ae-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="ea9ae-127">Réception de MCDUserNotifications</span><span class="sxs-lookup"><span data-stu-id="ea9ae-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="ea9ae-128">Vous devez d’abord instancier un MCDUserNotificationReader et obtenir tous les MCDUserNotifications existants dans le lecteur si la consommation de ces informations pour l’expérience que vous essayez d’activer vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="ea9ae-129">Étant donné que ce point de terminaison d’appareil particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé sur votre application, nous pouvons toujours présumer sans risque que le serveur d’applications a déjà publié des notifications à cet utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="ea9ae-130">Ajoutez alors un détecteur d’événements qui se déclenche quand la Plateforme d’appareils connectés effectue une synchronisation et qu’elle doit vous informer de nouveaux changements.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="ea9ae-131">Dans le cas de la fonctionnalité Notifications Graph, les nouveaux changements peuvent être de nouveaux MCDUserNotifications entrants publiés par votre serveur d’applications, ou des mises à jour, suppressions et expirations d’éléments MCDUserNotifcation qui se sont produits à partir du serveur ou à partir d’autres points de terminaison inscrits auxquels le même utilisateur s’est connecté.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="ea9ae-132">Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="ea9ae-133">Si vous utilisez actuellement une notification silencieuse APNS pour construire une notification visuelle dans le centre de notifications au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification silencieuse pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

```ObjectiveC
// Instantiate the reader from a MCDUserNotificationChannel
// Add a data change listener to subscribe to new changes when new notifications or notification updates are received
- (void)setupWithAccount:(MCDUserAccount*)account {
    dispatch_async(dispatch_get_global_queue(QOS_CLASS_DEFAULT, 0), ^{
        @synchronized (self) {
            MCDUserDataFeed* dataFeed = [MCDUserDataFeed userDataFeedForAccount:account platform:_platform activitySourceHost:@"graphnotifications.sample.windows.com"];
            [dataFeed addSyncScopes:@[[MCDUserNotificationChannel syncScope]]];
            self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:dataFeed];
            self.reader = [self.channel createReader];
            
            __weak typeof(self) weakSelf = self;
            _readerRegistrationToken = [self.reader addDataChangedListener:^(__unused MCDUserNotificationReader* source) {
                NSLog(@"ME123 Got a change!");
                if (weakSelf) {
                    [weakSelf forceRead];
                } else {
                    NSLog(@"ME123 WEAKSELF FOR CHANGES IS NULL!!!");
                }
            }];
            
            [self forceRead];
        }
    });
}

// this is your own business logic when the event listener is fired
// In this case, the app reads the existing batch of notifications in the store and handle any new incoming notifications or notification updates after that
- (void)forceRead {
    NSLog(@"ME123 Forced to read!");
    [self.reader readBatchAsyncWithMaxSize:NSUIntegerMax completion:^(NSArray<MCDUserNotification *> * _Nullable notifications, NSError * _Nullable error) {
        if (error) {
            NSLog(@"ME123 Failed to read batch with error %@", error);
        } else {
            [self _handleNotifications:notifications];
            NSLog(@"ME123 Have %ld listeners", self.listenerMap.count);
            for (void (^listener)(void) in self.listenerMap.allValues) {
                NSLog(@"ME123 Calling a listener about an update!");
                listener();
            }
        }
    }];
}

```

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="ea9ae-134">Mettre à jour l’état d’un MCDUserNotification existant</span><span class="sxs-lookup"><span data-stu-id="ea9ae-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="ea9ae-135">Dans la section précédente, nous avons mentionné qu’un changement de MCDUserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un MCDUserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu).</span><span class="sxs-lookup"><span data-stu-id="ea9ae-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="ea9ae-136">Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="ea9ae-137">Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de MCDUserNotification pour commencer.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="ea9ae-138">Vous pouvez choisir le moment où mettre à jour l’état de vos MCDUserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="ea9ae-139">Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="ea9ae-140">L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="ea9ae-141">Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état de la notification utilisateur correspondante afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="ea9ae-142">Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="ea9ae-143">Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="ea9ae-144">La classe MCDUserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le MCDUserNotificationReadState ou le MCDUserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="ea9ae-145">Par exemple, vous pouvez marquer l’état d’action comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="ea9ae-146">Alternativement ou simultanément, vous pouvez marquer l’état de lecture comme Unread (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application.</span><span class="sxs-lookup"><span data-stu-id="ea9ae-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

```ObjectiveC
- (void)dismissNotification:(MCDUserNotification*)notification {
    @synchronized (self) {
        notification.userActionState = MCDUserNotificationUserActionStateDismissed;
        [notification saveAsync:^(__unused MCDUserNotificationUpdateResult * _Nullable result, __unused NSError * _Nullable err) {
            NSLog(@"ME123 Dismiss notification with result %d error %@", result.succeeded, err);
        }];
    }
}

```
