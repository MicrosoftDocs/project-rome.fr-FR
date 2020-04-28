---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801801"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>Associez la Plateforme d’appareils connectés à une notification Push native pour chaque plateforme mobile. 

Comme nous l’avons vu précédemment, les clients d’application doivent faire connaître au kit SDK côté client et à la Plateforme d’appareils connectés pendant le processus d’inscription le pipeline de notification Push natif qui est utilisé pour chaque plateforme mobile, ceci pour permettre au service de notification Graph de distribuer les notifications à chaque point de terminaison client d’application quand votre serveur d’applications publie une notification ciblant l’utilisateur via les API Microsoft Graph.

Dans les étapes précédentes, vous avez initialisé la Plateforme avec un paramètre `null` *notificationProvider*. Ici, vous devez construire et transmettre un objet qui implémente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** . La principale chose à noter est que la méthode `getNotificationRegistrationAsync` doit retourner une instance de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** . **NotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.

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

Transmettez cette inscription dans votre implémentation de **NotificationProvider**. Ensuite, l’appel d’initialisation de la **Plateforme** doit fournir à la **Plateforme** locale un accès au service de notifications Push, permettant ainsi à votre application de recevoir des données de notifications Microsoft Graph côté serveur. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Transmettre les notifications Push entrantes au SDK client
À présent, étendez la classe de votre service d’écoute natif (dans ce cas, [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService), puisque ce tutoriel a utilisé Firebase Cloud Messaging) avec une surcharge spéciale de la méthode `onMessageReceived` (méthode de gestion des notifications).

Pour des raisons de conformité, de sécurité et d’optimisations potentielles, la notification entrante de Google Cloud Messaging en provenance des notifications Graph côté serveur peut être une simple indication, qui ne contient aucune des données initialement publiées par le serveur d’applications. La récupération du contenu de notification effectif publié par le serveur d’applications est occultée par les API du SDK côté client. De ce fait, le SDK peut fournir un modèle de programmation cohérent dans lequel le client d’application transmet toujours la charge utile entrante de Google Cloud Messaging au SDK. Cela permet au SDK de déterminer s’il s’agit d’une notification pour des scénarios de la Plateforme d’appareils connectés ou pas (dans le cas où le canal Google Cloud Messaging natif d’Android est utilisé par le client d’application à d’autres fins) et à quel scénario/fonctionnalité cette notification entrante correspond (notifications Graph, activité utilisateur, etc.). Après cela, des logiques spécifiques peuvent être exécutées par le client d’application pour gérer différents types de scénarios. 

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

Votre application peut maintenant gérer les notifications de la Plateforme d’appareils connectés.

