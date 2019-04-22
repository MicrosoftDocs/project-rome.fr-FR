---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801801"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>Associer la plateforme d’appareils connectés à la notification push native pour chaque plateforme mobile. 

Comme mentionné précédemment, les clients d’application doivent apportent des informations sur le pipeline de notification push natif utilisé pour chaque plateforme mobile pour le Kit de développement côté client et la plateforme d’appareils connectés pendant le processus d’inscription, pour permettre à Graph service de notification pour les notifications de sortance pour chaque point de terminaison du client d’application lors de votre serveur d’applications publie une notification de multi-ciblage utilisateur via l’API Microsoft Graph.

Dans les étapes ci-dessus, vous avez initialisé la plateforme avec un `null` *notificationProvider* paramètre. Ici, vous devez construire et passez un objet qui implémente  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**. La principale chose à noter est la `getNotificationRegistrationAsync` (méthode), qui doit retourner un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance. Le **NotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.

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

Fournir cette inscription dans votre implémentation de **NotificationProvider**. Ensuite, le **plateforme** appel d’initialisation doit fournir local **plateforme** avec un accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir de Notifications Microsoft Graph côté serveur. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Transmettre des notifications push entrantes pour le SDK du client
À présent, étendre votre écouteur natif classe de service ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) dans ce cas, étant donné que ce didacticiel utilise Firebase Cloud Messaging) avec une surcharge particulière de la `onMessageReceived` (méthode) (la notification-gestion méthode).

En raison de la conformité, la sécurité et les optimisations potentielles, la notification de Google Cloud Messaging entrante en provenance de Notifications de graphique côté serveur peut être un drainage de l’épaule, qui ne contient pas toutes les données qui sont initialement publiées par le serveur d’application. La récupération de la notification de contenu réelle publiée par le serveur d’applications est masquée derrière les API du Kit de développement logiciel côté client. Pour cette raison, le Kit de développement peut fournir un modèle de programmation cohérent dans lequel le client de l’application transmet toujours la charge utile entrante de Google Cloud Messaging au kit SDK. Ainsi, le Kit de développement logiciel déterminer s’il s’agit d’une notification pour les scénarios de plateforme d’appareils connectés ou pas (en cas de Android natif Google Cloud Messaging canal est utilisé par le client d’application à d’autres fins) et quelle entrants de ce scénario/fonctionnalité notification correspond à (Notifications de Graph, l’activité des utilisateurs, etc.). Logiques spécifiques sur un type différent de scénarios de gestion peuvent ensuite être exécutées par le client app après cela. 

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

Votre application peut désormais gérer les notifications à partir de la plateforme d’appareils connectés.

