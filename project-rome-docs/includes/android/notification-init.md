---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801571"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="8b247-103">Configuration préliminaire pour les notifications Push</span><span class="sxs-lookup"><span data-stu-id="8b247-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="8b247-104">Inscrire votre application aux notifications Push</span><span class="sxs-lookup"><span data-stu-id="8b247-104">Register your app for push notifications</span></span>

<span data-ttu-id="8b247-105">Pour assurer une prise en charge des notifications, inscrivez votre application auprès de Google.</span><span class="sxs-lookup"><span data-stu-id="8b247-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="8b247-106">Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite.</span><span class="sxs-lookup"><span data-stu-id="8b247-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="8b247-107">Inscrire votre application pour l’accès à la Plateforme d’appareils connectés inter-appareils</span><span class="sxs-lookup"><span data-stu-id="8b247-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="8b247-108">Inscrivez ensuite votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="8b247-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="8b247-109">Il s’agit d’une procédure différente de celle qui consiste à s’inscrire sur le Centre de développement Windows, qui a été abordée précédemment dans les étapes préliminaires.</span><span class="sxs-lookup"><span data-stu-id="8b247-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="8b247-110">Elle autorise la Plateforme d’appareils connectés à envoyer des notifications à l’aide du service de notification Push natif.</span><span class="sxs-lookup"><span data-stu-id="8b247-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="8b247-111">Le processus d’intégration du Centre de développement nécessite les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8b247-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="8b247-112">L’ID client de votre application.</span><span class="sxs-lookup"><span data-stu-id="8b247-112">Your app's client ID.</span></span>
* <span data-ttu-id="8b247-113">La clé Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="8b247-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="8b247-114">Ces informations sont nécessaires pour remettre les données et les commandes à l’application (sur un appareil qui est peut-être verrouillé ou en veille) sous forme de notifications Push.</span><span class="sxs-lookup"><span data-stu-id="8b247-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="8b247-115">Configurer votre application pour la rendre compatible avec les notifications</span><span class="sxs-lookup"><span data-stu-id="8b247-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="8b247-116">Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour le rendre apte à recevoir des notifications Push.</span><span class="sxs-lookup"><span data-stu-id="8b247-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="8b247-117">Si vous avez des doutes quant à la façon de procéder, consultez [Set up a Firebase Cloud Messaging client app on Android](https://firebase.google.com/docs/cloud-messaging/android/client).</span><span class="sxs-lookup"><span data-stu-id="8b247-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="8b247-118">Associer le service de notification à la Plateforme locale</span><span class="sxs-lookup"><span data-stu-id="8b247-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="8b247-119">Enfin, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="8b247-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="8b247-120">Dans les étapes précédentes, vous avez initialisé la Plateforme avec un paramètre `null` *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="8b247-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="8b247-121">Ici, vous devez construire et transmettre un objet qui implémente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** .</span><span class="sxs-lookup"><span data-stu-id="8b247-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="8b247-122">La principale chose à noter est que la méthode `getNotificationRegistrationAsync` doit retourner une instance de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** .</span><span class="sxs-lookup"><span data-stu-id="8b247-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="8b247-123">**NotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="8b247-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


```Java
private NotificationRegistration mNotificationRegistration;

// ...

/**
* NotificationRegistration is constructed with four parameters:
* Type: This is the notification platform type.
* Token: This is the string that GCM or FCM sends to your registration intent service.
* SenderId: This is the numeric Sender ID that you received when you registered your app for push notifications.
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
mNotificationRegistration = new NotificationRegistration(NotificationType.FCM, token, FCM_SENDER_ID, "MyAppName");
```

<span data-ttu-id="8b247-124">Transmettez cette inscription dans votre implémentation de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="8b247-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="8b247-125">Ensuite, l’appel d’initialisation de la **Plateforme** doit fournir à la **Plateforme** locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données de la Plateforme d’appareils connectés côté serveur, qui relaie les demandes de lancement et les messages de service d’application d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="8b247-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="8b247-126">Il ne vous reste plus maintenant qu’à étendre la classe de votre service d’écoute natif (dans ce cas, [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService), puisque ce guide a utilisé Firebase Cloud Messaging) avec une surcharge spéciale de la méthode `onMessageReceived` (méthode de gestion des notifications).</span><span class="sxs-lookup"><span data-stu-id="8b247-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

```Java
/**
* Check whether it's a rome notification or not.
* If it is a rome notification, it will notify the apps with the information in the notification.
* @param from describes message sender.
* @param data message data as String key/value pairs.
*/
@Override
public void onMessageReceived(String from, Bundle data) {
    Log.d(TAG, "From: " + from);

    // Ensure that the Platform is initialized here before going on
    // ...

    // This method passes the data to the Connected Devices Platform if is compatible.
    if (!NotificationReceiver.Receive(data)) {
        // a value of false indicates a non-Rome notification
        Log.d(TAG, "GCM client received a message that was not a Rome notification");
    }
}
```

<span data-ttu-id="8b247-127">Votre application est désormais capable de gérer les notifications à partir de la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="8b247-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
