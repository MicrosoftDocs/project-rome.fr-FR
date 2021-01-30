---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 5b565b3eeaffb350f9296e38bf8bf9d46a58a64d
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98947676"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="e92e6-103">Associez la Plateforme d’appareils connectés à une notification Push native pour chaque plateforme mobile.</span><span class="sxs-lookup"><span data-stu-id="e92e6-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="e92e6-104">Comme nous l’avons vu précédemment, les clients d’application doivent faire connaître au kit SDK côté client et à la Plateforme d’appareils connectés pendant le processus d’inscription le pipeline de notification Push natif qui est utilisé pour chaque plateforme mobile, ceci pour permettre au service de notification Graph de distribuer les notifications à chaque point de terminaison client d’application quand votre serveur d’applications publie une notification ciblant l’utilisateur via les API Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="e92e6-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="e92e6-105">Dans les étapes précédentes, vous avez initialisé la Plateforme avec un paramètre `null` *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="e92e6-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="e92e6-106">Ici, vous devez construire et transmettre un objet qui implémente **[NotificationProvider](/java/api/com.microsoft.connecteddevices.core._notification_provider)** .</span><span class="sxs-lookup"><span data-stu-id="e92e6-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="e92e6-107">La principale chose à noter est que la méthode `getNotificationRegistrationAsync` doit retourner une instance de **[NotificationRegistration](/java/api/com.microsoft.connecteddevices.core._notification_registration)** .</span><span class="sxs-lookup"><span data-stu-id="e92e6-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="e92e6-108">**NotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="e92e6-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

```java
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

<span data-ttu-id="e92e6-109">Transmettez cette inscription dans votre implémentation de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="e92e6-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="e92e6-110">Ensuite, l’appel d’initialisation de la **Plateforme** doit fournir à la **Plateforme** locale un accès au service de notifications Push, permettant ainsi à votre application de recevoir des données de notifications Microsoft Graph côté serveur.</span><span class="sxs-lookup"><span data-stu-id="e92e6-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="e92e6-111">Transmettre les notifications Push entrantes au SDK client</span><span class="sxs-lookup"><span data-stu-id="e92e6-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="e92e6-112">À présent, étendez la classe de votre service d’écoute natif (dans ce cas, [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService), puisque ce tutoriel a utilisé Firebase Cloud Messaging) avec une surcharge spéciale de la méthode `onMessageReceived` (méthode de gestion des notifications).</span><span class="sxs-lookup"><span data-stu-id="e92e6-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="e92e6-113">Pour des raisons de conformité, de sécurité et d’optimisations potentielles, la notification entrante de Google Cloud Messaging en provenance des notifications Graph côté serveur peut être une simple indication, qui ne contient aucune des données initialement publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="e92e6-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="e92e6-114">La récupération du contenu de notification effectif publié par le serveur d’applications est occultée par les API du SDK côté client.</span><span class="sxs-lookup"><span data-stu-id="e92e6-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="e92e6-115">De ce fait, le SDK peut fournir un modèle de programmation cohérent dans lequel le client d’application transmet toujours la charge utile entrante de Google Cloud Messaging au SDK.</span><span class="sxs-lookup"><span data-stu-id="e92e6-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="e92e6-116">Cela permet au SDK de déterminer s’il s’agit d’une notification pour des scénarios de la Plateforme d’appareils connectés ou pas (dans le cas où le canal Google Cloud Messaging natif d’Android est utilisé par le client d’application à d’autres fins) et à quel scénario/fonctionnalité cette notification entrante correspond (notifications Graph, activité utilisateur, etc.).</span><span class="sxs-lookup"><span data-stu-id="e92e6-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="e92e6-117">Après cela, des logiques spécifiques peuvent être exécutées par le client d’application pour gérer différents types de scénarios.</span><span class="sxs-lookup"><span data-stu-id="e92e6-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

```java
/**
* Check whether it's a Connected Devices Platform notification or not.
* If it is a Connected Devices Platform notification, it will notify the apps with the information in the notification.
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

<span data-ttu-id="e92e6-118">Votre application peut maintenant gérer les notifications de la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="e92e6-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>