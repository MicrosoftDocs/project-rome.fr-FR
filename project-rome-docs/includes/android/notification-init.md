---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801571"
---
## <a name="preliminary-setup-for-push-notifications"></a>Programme d’installation préliminaire pour les notifications push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application avec Google pour la prise en charge de la notification. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard. 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>Inscrire votre application pour l’accès entre les périphériques connectés la plateforme de périphériques

Ensuite, enregistrez votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une autre procédure de s’inscrire sur le centre de développement Windows, qui a été abordé dans les étapes préliminaires ci-dessus. Elle autorise la plateforme d’appareils connectés pour envoyer des notifications à l’aide du service de notifications push natif. Le centre de développement nécessitera des processus d’intégration :
* ID de client. de votre application
* La clé Google Cloud Messaging. Cela est nécessaire pour fournir des données et des commandes à l’application (sur un appareil qui peut être verrouillé ou en veille) sous la forme de notifications push. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configurer votre application pour être compatible avec notification

Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour le rendre capable de recevoir des notifications push. Consultez [défini d’un Firebase Cloud Messaging Application cliente sur Android](https://firebase.google.com/docs/cloud-messaging/android/client) si vous ne savez pas comment procéder.

### <a name="associate-the-notification-service-with-the-local-platform"></a>Associer le service de notification de la plateforme locale

Enfin, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application. Dans les étapes ci-dessus, vous avez initialisé la plateforme avec un `null` *notificationProvider* paramètre. Ici, vous devez construire et passez un objet qui implémente  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**. La principale chose à noter est la `getNotificationRegistrationAsync` (méthode), qui doit retourner un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance. Le **NotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.


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

Fournir cette inscription dans votre implémentation de **NotificationProvider**. Ensuite, le **plateforme** appel d’initialisation doit fournir local **plateforme** avec un accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir des appareils connectés côté serveur Plateforme, qui relaie les demandes de lancement et les messages de service d’application à partir d’autres appareils. 

Il vous suffit maintenant est d’étendre votre écouteur natif classe de service ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) dans ce cas, étant donné que ce guide utilisé Firebase Cloud Messaging) avec une surcharge particulière de la `onMessageReceived` (méthode) (le méthode de gestion de la notification).

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

Votre application est maintenant en mesure de gérer les notifications à partir de la plateforme d’appareils connectés.
