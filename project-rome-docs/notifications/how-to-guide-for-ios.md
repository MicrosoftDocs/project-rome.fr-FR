---
title: L’intégration des applications IOs avec les Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909621"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="7a9d8-103">Guide pratique : L’intégration avec les Notifications de graphique (iOS)</span><span class="sxs-lookup"><span data-stu-id="7a9d8-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="7a9d8-104">Notifications de graphique activer votre application envoyer et gérer les notifications de ciblage d’utilisateur sur plusieurs appareils.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="7a9d8-105">Avec le SDK côté client de Project Rome sur iOS, votre application iOS peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="7a9d8-106">Le Kit de développement permet au client de l’application recevoir les nouvelles charges utiles de notification entrant, gérer l’état des notifications existantes et récupérer l’historique de la notification.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="7a9d8-107">Pour plus d’informations sur les Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="7a9d8-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="7a9d8-108">Toutes les fonctionnalités dans le SDK de Rome projet includng graphique Notifications et bien plus encore, sont appuient sur une plateforme sous-jacente, appelée la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="7a9d8-109">Ce guide est conçu pour vous guider à travers les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés et d’expliquer comment utiliser des API dans le Kit de développement pour implémenter des Notifications de graphique-fonctionnalités spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="7a9d8-110">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="7a9d8-111">Consultez le [référence de l’API](api-reference-for-ios/index.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="7a9d8-112">Configuration de la plateforme de périphériques connectés et les Notifications</span><span class="sxs-lookup"><span data-stu-id="7a9d8-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="7a9d8-113">À l’aide de la plateforme</span><span class="sxs-lookup"><span data-stu-id="7a9d8-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="7a9d8-114">Initialiser un canal de Notification de graphique</span><span class="sxs-lookup"><span data-stu-id="7a9d8-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="7a9d8-115">Le Kit de développement logiciel Project Rome permet à votre application pour vous abonner à différents canaux afin de recevoir et gérer les différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="7a9d8-116">Il s’agit tout stockée et synchronisé dans **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="7a9d8-117">**MCDUserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="7a9d8-118">Pour intégrer avec Notification de graphique et recevoir des MCDUserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="7a9d8-119">Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).</span><span class="sxs-lookup"><span data-stu-id="7a9d8-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="7a9d8-120">Les méthodes suivantes d’initialiser un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
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
<span data-ttu-id="7a9d8-121">À ce stade, vous devez avoir un **MCDUserNotificationChannel** référencer dans `channel`.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="7a9d8-122">Créer un MCDUserNotificationReader pour recevoir des MCDUserNotifications entrantes et accéder à l’historique MCDUserNotification</span><span class="sxs-lookup"><span data-stu-id="7a9d8-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="7a9d8-123">Comme nous vous avons montré précédemment, le certificat APNS initial sans assistance message arrivant sur le client d’application uniquement contient un drainage de l’épaule, et vous devez transmettre cette charge utile tap d’épaule à la plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le périphérique connecté serveur, qui contient tous les MCDUserNotifications publiées par le serveur de votre application.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="7a9d8-124">Cela abaisse la charge utile de notification complète publiée par votre serveur d’application correspondant à cette tap épaule (et dans le cas si les notifications précédentes ont été publiées mais pas reçues sur ce client de l’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront extrait vers le bas également).</span><span class="sxs-lookup"><span data-stu-id="7a9d8-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="7a9d8-125">Avec ces synchronisations en temps réel en permanence effectuées par le Kit de développement, le client de l’application est en mesure d’accéder à un cache local des flux de données MCDUserNotification connecté l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="7a9d8-126">Dans ce cas un MCDUserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection MCDUserNotification complète qui peut être utilisée en tant que modèle de vue de la notification de l’utilisateur historique.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="7a9d8-127">Réception MCDUserNotifications</span><span class="sxs-lookup"><span data-stu-id="7a9d8-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="7a9d8-128">Vous devez d’abord instancier un MCDUserNotificationReader et obtenir toutes les MCDUserNotifications existantes déjà dans le lecteur si vous vous intéressez lors de la consommation de ces informations pour l’expérience que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="7a9d8-129">Il est recommandé de toujours supposer que le serveur d’application a déjà publié des notifications à celui-ci connecté utilisateur, étant donné que ce point de terminaison de périphérique particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé votre application.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="7a9d8-130">Ensuite, ajoutez un écouteur d’événements qui se déclenche quand la plateforme d’appareils connectés se termine une synchronisation et a des modifications apportées à vous en informer.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="7a9d8-131">Dans le cas des Notifications de graphique, les nouvelles modifications peut être nouveau MCDUserNotifications entrantes publiées par votre suppressions du serveur ou les mises à jour MCDUserNotifcation, application et points de terminaison inscrits de délais d’expiration qui se sont produits à partir du serveur ou des autres que le même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="7a9d8-132">Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="7a9d8-133">Si vous utilisez actuellement la notification en mode silencieux APNS pour construire une notification visuelle dans le centre de notification au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification en mode silencieux pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="7a9d8-134">Mettre à jour l’état d’une MCDUserNotification existante</span><span class="sxs-lookup"><span data-stu-id="7a9d8-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="7a9d8-135">Dans la section précédente, nous avons mentionné que parfois une modification MCDUserNotification reçue via le lecteur peut être une mise à jour de l’état sur une MCDUserNotification existante – si marquée comme dismissed ou marqués comme lus.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="7a9d8-136">Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="7a9d8-137">Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification MCDUserNotification pour commencer : à partir d’un autre appareil.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="7a9d8-138">Vous pouvez choisir le moment pour mettre à jour l’état de votre MCDUserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application vous Activer.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="7a9d8-139">Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="7a9d8-140">L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="7a9d8-141">Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de la Notification utilisateur correspondante afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="7a9d8-142">Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="7a9d8-143">Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="7a9d8-144">Classe de MCDUserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le MCDUserNotificationReadState ou le MCDUserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="7a9d8-145">Par exemple, vous pouvez marquer les États d’action pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="7a9d8-146">Vous pouvez également, ou en même temps, vous pouvez marquer lire l’état de lecture ou non lu et selon qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application.</span><span class="sxs-lookup"><span data-stu-id="7a9d8-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

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
