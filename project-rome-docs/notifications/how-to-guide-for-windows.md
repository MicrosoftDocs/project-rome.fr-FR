---
title: L’intégration d’applications UWP avec des Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801301"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="0cc3a-103">Guide pratique : L’intégration à MS Graph Notifications (Windows UWP)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="0cc3a-104">Avec le SDK côté client graphique Notifications sur Windows, votre application UWP de Windows peut effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception qui reçoit des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="0cc3a-105">Le SDK est ensuite utilisé pour gérer les notifications sur le côté client, y compris la réception des notifications de nouvelles charges utiles est arrivé sur ce client, la gestion de l’état des notifications et récupération de l’historique de notification.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="0cc3a-106">Pour plus d’informations sur MS Graph Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="0cc3a-107">Consultez le [référence de l’API](api-reference-for-windows/index.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="0cc3a-108">Programme d’installation préliminaire pour accéder à la plateforme d’appareils connectés pour pouvoir utiliser les Notifications de graphique</span><span class="sxs-lookup"><span data-stu-id="0cc3a-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="0cc3a-109">Il existe quelques étapes à suivre pour intégrer des Notifications de graphique</span><span class="sxs-lookup"><span data-stu-id="0cc3a-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="0cc3a-110">Compte de service administré ou inscription d’application AAD</span><span class="sxs-lookup"><span data-stu-id="0cc3a-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="0cc3a-111">L’intégration du centre de développement pour fournir l’identité de l’application multiplateforme et transmettre les informations d’identification de la Notification</span><span class="sxs-lookup"><span data-stu-id="0cc3a-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="0cc3a-112">Ajouter le Kit de développement et l’initialisation de la plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="0cc3a-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="0cc3a-113">Associer le Service de Notification de plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="0cc3a-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="0cc3a-114">Tout d’abord, vous devez effectuer le MSA et/ou l’inscription de l’application AAD.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="0cc3a-115">Si vous avez déjà fait cela, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="0cc3a-116">Ensuite, vous devez intégrer avec Microsoft Windows Dev Center pour accéder à la plateforme d’appareils connectés afin de s’intégrer avec des expériences entre les périphériques, y compris l’utilisation de Notifications de graphique.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="0cc3a-117">Si vous avez déjà fait cela, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="0cc3a-118">Ensuite, vous devez ajouter le Kit de développement logiciel Project Rome à votre projet et initialiser la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="0cc3a-119">Si vous avez déjà fait cela, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="0cc3a-120">Enfin, vous devez activer votre application recevoir des notifications push.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="0cc3a-121">Si vous avez déjà fait cela, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="0cc3a-122">Initialiser un canal de Notification de graphique</span><span class="sxs-lookup"><span data-stu-id="0cc3a-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="0cc3a-123">À un niveau élevé, le SDK permet à votre application pour vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="0cc3a-124">Il s’agit tout stockée et synchronisé dans **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="0cc3a-125">**UserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="0cc3a-126">Pour intégrer avec Notification de graphique et recevoir des UserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="0cc3a-127">Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).</span><span class="sxs-lookup"><span data-stu-id="0cc3a-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="0cc3a-128">Créer un UserNotificationReader pour recevoir des UserNotifications entrantes et accéder à l’historique UserNotification</span><span class="sxs-lookup"><span data-stu-id="0cc3a-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="0cc3a-129">Une fois que vous avez un **UserNotificationChannel** référence, vous devez un **UserNotificationReader** afin de permettre au SDK extraire le contenu de la notification à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="0cc3a-130">Dans ce cas un UserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection UserNotification complète qui peut être utilisée en tant que modèle de vue de l’historique de notification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="0cc3a-131">Le code suivant montre comment instancier un canal de notification utilisateur, créer un lecteur de la notification utilisateur et ajouter un gestionnaire d’événements sur le lecteur de notification utilisateur qui se déclenche quand la plateforme d’appareils connectés se termine chaque synchronisation et a des modifications apportées à vous en informer.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

```C#

public async Task SetupChannel()
{
    var account = m_accoutProvider.SignedInAccount;

    if (m_feed == null)
    {
        await Task.Run(() =>
        {
            lock (this)
            {
                if (m_feed == null)
                {
                    m_platform = new ConnectedDevicesPlatform(m_accoutProvider, this);

                    Logger.Instance.LogMessage($"Create feed for {account.Id} {account.Type}");
                    m_feed = new UserDataFeed(account, m_platform, "graphnotifications.sample.windows.com");
                    m_feed.SyncStatusChanged += Feed_SyncStatusChanged;
                    m_feed.AddSyncScopes(new List<IUserDataFeedSyncScope>
                    {
                        UserNotificationChannel.SyncScope
                    });

                    m_channel = new UserNotificationChannel(m_feed);
                    m_reader = m_channel.CreateReader();
                    m_reader.DataChanged += Reader_DataChanged;
                }
            }
        });
    }
}

```

### <a name="receiving-usernotifications"></a><span data-ttu-id="0cc3a-132">Réception UserNotifications</span><span class="sxs-lookup"><span data-stu-id="0cc3a-132">Receiving UserNotifications</span></span>

<span data-ttu-id="0cc3a-133">Dans la section ci-dessus, nous voyons qu’un écouteur d’événement du est ajouté au lecteur de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="0cc3a-134">Vous devez implémenter cet écouteur d’événement pour lire toutes les nouvelles notifications et les mises à jour de la notification à partir du lecteur et implémenter votre propre logique métier pour gérer chacun de ces modifications.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="0cc3a-135">Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="0cc3a-136">Si vous utilisez actuellement notification brute de WNS pour construire une notification toast local dans le centre de maintenance au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="0cc3a-137">Le code suivant vous montre comment l’exemple d’application choisit de déclencher une notification toast local pour tous les UserNotification entrante qui sont actifs et supprimer la notification correspondante de l’interface utilisateur dans la vue dans l’application si une notification est supprimée.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

```C#

private void Reader_DataChanged(UserNotificationReader sender, object args)
{
    ReadNotifications(sender, true);
}

private async void ReadNotifications(UserNotificationReader reader, bool showToast)
{
    var notifications = await reader.ReadBatchAsync(UInt32.MaxValue);

    foreach (var notification in notifications)
    {

        if (notification.Status == UserNotificationStatus.Active)
        {
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            if (notification.UserActionState == UserNotificationUserActionState.NoInteraction)
            {
                // new notification, show this to user using the Windows local toast notification APIs
                m_newNotifications.Add(notification);
                if (!string.IsNullOrEmpty(notification.Content) && showToast)
                {
                    ShowToastNotification(BuildToastNotification(notification.Id, notification.Content));
                }
            }

            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.Insert(0, notification);
        }
        else
        {
            // Existing notification is marked as deleted, remove from display
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            RemoveToastNotification(notification.Id);
        }
    }
}

```
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="0cc3a-138">Mettre à jour l’état d’une UserNotification existante</span><span class="sxs-lookup"><span data-stu-id="0cc3a-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="0cc3a-139">Dans la section précédente, nous avons mentionné que parfois une modification UserNotification reçue via le lecteur peut être une mise à jour de l’état sur une UserNotification existante – si marquée comme dismissed ou marqués comme lus.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="0cc3a-140">Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="0cc3a-141">Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification UserNotification pour commencer : à partir d’un autre appareil.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="0cc3a-142">Vous pouvez choisir le moment pour mettre à jour l’état de votre UserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application que vous activez .</span><span class="sxs-lookup"><span data-stu-id="0cc3a-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="0cc3a-143">Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="0cc3a-144">L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="0cc3a-145">Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de le correspondante UserNotification afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="0cc3a-146">Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="0cc3a-147">Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="0cc3a-148">Classe de UserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="0cc3a-149">Par exemple, vous pouvez marquer UserActionState pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="0cc3a-150">Vous pouvez également, ou en même temps vous pouvez marquer état ReadState comme lu ou non lu et en fonction de qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="0cc3a-151">Code ci-dessous extrait de code montre comment marquer le UserNotificationUserActionState d’une notification en tant qu’ignoré.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```C#
public async void Dismiss(string id)
{
    var notification = m_newNotifications.Find((n) => { return (n.Id == id); });
    if (notification != null)
    {
        notification.UserActionState = UserNotificationUserActionState.Dismissed;
        await notification.SaveAsync();
    }
}

```
