---
title: Intégration d’applications UWP à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801301"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="31510-103">Guides pratique : Intégration à la fonctionnalité Notifications MS Graph (Windows UWP)</span><span class="sxs-lookup"><span data-stu-id="31510-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="31510-104">Avec le SDK côté client Notifications Graph sur Windows, votre application UWP Windows peut effectuer les étapes d’inscription nécessaires pour devenir un point de terminaison de réception qui reçoit des notifications publiées à partir de votre serveur d’application ciblant un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31510-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="31510-105">Le SDK est ensuite utilisé pour gérer les notifications côté client, notamment la réception des nouvelles charges utiles de notification arrivées sur ce client, la gestion de l’état des notifications et la récupération de l’historique des notifications.</span><span class="sxs-lookup"><span data-stu-id="31510-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="31510-106">Pour plus d’informations sur la fonctionnalité Notifications MS Graph et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="31510-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="31510-107">Consultez la page [Informations de référence sur les API](api-reference-for-windows/index.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.</span><span class="sxs-lookup"><span data-stu-id="31510-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="31510-108">Configuration préliminaire de l’accès à la Plateforme d’appareils connectés pour pouvoir utiliser les notifications Graph</span><span class="sxs-lookup"><span data-stu-id="31510-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="31510-109">La procédure d’intégration de la fonctionnalité Notifications Graph comprend quelques étapes.</span><span class="sxs-lookup"><span data-stu-id="31510-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="31510-110">Inscription d’application MSA ou AAD</span><span class="sxs-lookup"><span data-stu-id="31510-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="31510-111">Intégration au Centre de développement pour fournir une identité d’application multiplateforme et envoie (par push) les informations d’identification de notification</span><span class="sxs-lookup"><span data-stu-id="31510-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="31510-112">Ajout du SDK et initialisation de la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="31510-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="31510-113">Associer le service de notification à la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="31510-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="31510-114">Tout d’abord, vous devez effectuer l’inscription d’application MSA et/ou AAD.</span><span class="sxs-lookup"><span data-stu-id="31510-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="31510-115">Si vous l’avez déjà fait, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="31510-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="31510-116">Ensuite, vous devez effectuer une intégration au Centre de développement Microsoft Windows pour pouvoir accéder à la Plateforme d’appareils connectés pour une intégration à des expériences inter-appareils, notamment l’utilisation de la fonctionnalité Notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="31510-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="31510-117">Si vous l’avez déjà fait, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="31510-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="31510-118">Ensuite, vous devez ajouter le SDK Projet Rome à votre projet et initialiser la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="31510-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="31510-119">Si vous l’avez déjà fait, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="31510-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="31510-120">Enfin, vous devez permettre à votre application de recevoir les notifications Push.</span><span class="sxs-lookup"><span data-stu-id="31510-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="31510-121">Si vous l’avez déjà fait, passez à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="31510-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="31510-122">Initialiser un canal de notification Graph</span><span class="sxs-lookup"><span data-stu-id="31510-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="31510-123">De manière générale, le SDK permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="31510-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="31510-124">Ils sont tous stockés et synchronisés dans **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="31510-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="31510-125">**UserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph.</span><span class="sxs-lookup"><span data-stu-id="31510-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="31510-126">Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un UserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="31510-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="31510-127">Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).</span><span class="sxs-lookup"><span data-stu-id="31510-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="31510-128">Créer un UserNotificationReader pour recevoir des UserNotification entrants et accéder à l’historique des UserNotification</span><span class="sxs-lookup"><span data-stu-id="31510-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="31510-129">Une fois que vous avez une référence à **UserNotificationChannel**, vous avez besoin d’un **UserNotificationReader** afin de permettre au SDK d’extraire le contenu de notification réel à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="31510-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="31510-130">Dans ce cas, un UserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments UserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="31510-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="31510-131">Le code ci-dessous montre les étapes à suivre pour instancier un canal de notification utilisateur, créer un lecteur de notification utilisateur et ajouter un gestionnaire d’événements sur le lecteur de notification utilisateur qui se déclenche quand la Plateforme d’appareils connectés effectue chaque synchronisation et qu’elle doit vous informer de nouveaux changements.</span><span class="sxs-lookup"><span data-stu-id="31510-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

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

### <a name="receiving-usernotifications"></a><span data-ttu-id="31510-132">Réception de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="31510-132">Receiving UserNotifications</span></span>

<span data-ttu-id="31510-133">Dans la section ci-dessus, nous voyons qu’un détecteur d’événements est ajouté au lecteur de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31510-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="31510-134">Vous devez implémenter ce détecteur d’événements pour lire toutes les nouvelles notifications et les mises à jour de notification à partir du lecteur, et implémenter votre propre logique métier pour gérer chacun de ces nouveaux changements.</span><span class="sxs-lookup"><span data-stu-id="31510-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="31510-135">Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="31510-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="31510-136">Si vous utilisez actuellement une notification brute de WNS pour construire une notification toast locale dans le centre de notifications au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela.</span><span class="sxs-lookup"><span data-stu-id="31510-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="31510-137">Le code ci-dessous vous montre comment l’exemple d’application choisit de déclencher une notification toast locale pour tous les éléments UserNotification entrants qui sont actifs et de supprimer l’interface utilisateur de notification correspondante dans la vue dans l’application si une notification est supprimée.</span><span class="sxs-lookup"><span data-stu-id="31510-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="31510-138">Mettre à jour l’état d’un UserNotification existant</span><span class="sxs-lookup"><span data-stu-id="31510-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="31510-139">Dans la section précédente, nous avons mentionné qu’un changement de UserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un UserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu).</span><span class="sxs-lookup"><span data-stu-id="31510-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="31510-140">Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier.</span><span class="sxs-lookup"><span data-stu-id="31510-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="31510-141">Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de UserNotification pour commencer.</span><span class="sxs-lookup"><span data-stu-id="31510-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="31510-142">Vous pouvez choisir le moment où mettre à jour l’état de vos UserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez.</span><span class="sxs-lookup"><span data-stu-id="31510-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="31510-143">Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés.</span><span class="sxs-lookup"><span data-stu-id="31510-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="31510-144">L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante.</span><span class="sxs-lookup"><span data-stu-id="31510-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="31510-145">Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état du UserNotification correspondant afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31510-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="31510-146">Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="31510-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="31510-147">Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31510-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="31510-148">La classe UserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="31510-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="31510-149">Par exemple, vous pouvez marquer UserActionState comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel.</span><span class="sxs-lookup"><span data-stu-id="31510-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="31510-150">Alternativement ou simultanément, vous pouvez marquer ReadState comme Read (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application.</span><span class="sxs-lookup"><span data-stu-id="31510-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="31510-151">L’extrait de code ci-dessous montre comment marquer le UserNotificationUserActionState d’une notification comme Dismissed (Masqué).</span><span class="sxs-lookup"><span data-stu-id="31510-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

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
