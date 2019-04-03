---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907221"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="3761a-103">Associer la plateforme d’appareils connectés à la notification push native pour chaque plateforme mobile.</span><span class="sxs-lookup"><span data-stu-id="3761a-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="3761a-104">Comme mentionné précédemment, les clients d’application doivent apportent des informations sur le pipeline de notification push natif utilisé pour chaque plateforme mobile pour le Kit de développement côté client et la plateforme d’appareils connectés pendant le processus d’inscription, pour permettre à Graph service de notification pour les notifications de sortance pour chaque point de terminaison du client d’application lors de votre serveur d’applications publie une notification de multi-ciblage utilisateur via l’API Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="3761a-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="3761a-105">Dans les étapes ci-dessus, vous avez initialisé la plateforme avec un `null` *notificationProvider* paramètre.</span><span class="sxs-lookup"><span data-stu-id="3761a-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="3761a-106">Ici, vous devez construire et passez un objet qui implémente  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span><span class="sxs-lookup"><span data-stu-id="3761a-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="3761a-107">La principale chose à noter est la `getNotificationRegistrationAsync` (méthode), qui doit retourner un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span><span class="sxs-lookup"><span data-stu-id="3761a-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="3761a-108">Le **NotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="3761a-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

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

<span data-ttu-id="3761a-109">Fournir cette inscription dans votre implémentation de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="3761a-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="3761a-110">Ensuite, le **plateforme** appel d’initialisation doit fournir local **plateforme** avec un accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir de Notifications Microsoft Graph côté serveur.</span><span class="sxs-lookup"><span data-stu-id="3761a-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="3761a-111">Transmettre des notifications push entrantes pour le SDK du client</span><span class="sxs-lookup"><span data-stu-id="3761a-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="3761a-112">À présent, étendre votre écouteur natif classe de service ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) dans ce cas, étant donné que ce didacticiel utilise Firebase Cloud Messaging) avec une surcharge particulière de la `onMessageReceived` (méthode) (la notification-gestion méthode).</span><span class="sxs-lookup"><span data-stu-id="3761a-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="3761a-113">En raison de la conformité, la sécurité et les optimisations potentielles, la notification de Google Cloud Messaging entrante en provenance de Notifications de graphique côté serveur peut être un drainage de l’épaule, qui ne contient pas toutes les données qui sont initialement publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="3761a-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="3761a-114">La récupération de la notification de contenu réelle publiée par le serveur d’applications est masquée derrière les API du Kit de développement logiciel côté client.</span><span class="sxs-lookup"><span data-stu-id="3761a-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="3761a-115">Pour cette raison, le Kit de développement peut fournir un modèle de programmation cohérent dans lequel le client de l’application transmet toujours la charge utile entrante de Google Cloud Messaging au kit SDK.</span><span class="sxs-lookup"><span data-stu-id="3761a-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="3761a-116">Ainsi, le Kit de développement logiciel déterminer s’il s’agit d’une notification pour les scénarios de plateforme d’appareils connectés ou pas (en cas de Android natif Google Cloud Messaging canal est utilisé par le client d’application à d’autres fins) et quelle entrants de ce scénario/fonctionnalité notification correspond à (Notifications de Graph, l’activité des utilisateurs, etc.).</span><span class="sxs-lookup"><span data-stu-id="3761a-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="3761a-117">Logiques spécifiques sur un type différent de scénarios de gestion peuvent ensuite être exécutées par le client app après cela.</span><span class="sxs-lookup"><span data-stu-id="3761a-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

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

<span data-ttu-id="3761a-118">Votre application peut désormais gérer les notifications à partir de la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="3761a-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>

