---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909451"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="6834f-103">Programme d’installation préliminaire pour les notifications push</span><span class="sxs-lookup"><span data-stu-id="6834f-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="6834f-104">Inscrire votre application pour les notifications push</span><span class="sxs-lookup"><span data-stu-id="6834f-104">Register your app for push notifications</span></span>

<span data-ttu-id="6834f-105">Inscrire votre application avec Google pour la prise en charge de la notification.</span><span class="sxs-lookup"><span data-stu-id="6834f-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="6834f-106">Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="6834f-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="6834f-107">Inscrire votre application pour l’accès entre les périphériques connectés la plateforme de périphériques</span><span class="sxs-lookup"><span data-stu-id="6834f-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="6834f-108">Ensuite, enregistrez votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="6834f-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="6834f-109">Il s’agit d’une autre procédure de s’inscrire sur le centre de développement Windows, qui a été abordé dans les étapes préliminaires ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="6834f-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="6834f-110">Elle autorise la plateforme d’appareils connectés pour envoyer des notifications à l’aide du service de notifications push natif.</span><span class="sxs-lookup"><span data-stu-id="6834f-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="6834f-111">Le centre de développement nécessitera des processus d’intégration :</span><span class="sxs-lookup"><span data-stu-id="6834f-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="6834f-112">ID de client. de votre application</span><span class="sxs-lookup"><span data-stu-id="6834f-112">Your app's client ID.</span></span>
* <span data-ttu-id="6834f-113">La clé Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="6834f-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="6834f-114">Cela est nécessaire pour fournir des données et des commandes à l’application (sur un appareil qui peut être verrouillé ou en veille) sous la forme de notifications push.</span><span class="sxs-lookup"><span data-stu-id="6834f-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="6834f-115">Configurer votre application pour être compatible avec notification</span><span class="sxs-lookup"><span data-stu-id="6834f-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="6834f-116">Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour le rendre capable de recevoir des notifications push.</span><span class="sxs-lookup"><span data-stu-id="6834f-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="6834f-117">Consultez [défini d’un Firebase Cloud Messaging Application cliente sur Android](https://firebase.google.com/docs/cloud-messaging/android/client) si vous ne savez pas comment procéder.</span><span class="sxs-lookup"><span data-stu-id="6834f-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="6834f-118">Associer le service de notification de la plateforme locale</span><span class="sxs-lookup"><span data-stu-id="6834f-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="6834f-119">Enfin, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="6834f-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="6834f-120">Dans les étapes ci-dessus, vous avez initialisé la plateforme avec un `null` *notificationProvider* paramètre.</span><span class="sxs-lookup"><span data-stu-id="6834f-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="6834f-121">Ici, vous devez construire et passez un objet qui implémente  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span><span class="sxs-lookup"><span data-stu-id="6834f-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="6834f-122">La principale chose à noter est la `getNotificationRegistrationAsync` (méthode), qui doit retourner un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span><span class="sxs-lookup"><span data-stu-id="6834f-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="6834f-123">Le **NotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="6834f-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


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

<span data-ttu-id="6834f-124">Fournir cette inscription dans votre implémentation de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="6834f-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="6834f-125">Ensuite, le **plateforme** appel d’initialisation doit fournir local **plateforme** avec un accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir des appareils connectés côté serveur Plateforme, qui relaie les demandes de lancement et les messages de service d’application à partir d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="6834f-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="6834f-126">Il vous suffit maintenant est d’étendre votre écouteur natif classe de service ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) dans ce cas, étant donné que ce guide utilisé Firebase Cloud Messaging) avec une surcharge particulière de la `onMessageReceived` (méthode) (le méthode de gestion de la notification).</span><span class="sxs-lookup"><span data-stu-id="6834f-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

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

<span data-ttu-id="6834f-127">Votre application est maintenant en mesure de gérer les notifications à partir de la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="6834f-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
