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
## <a name="preliminary-setup-for-push-notifications"></a>Configuration préliminaire pour les notifications Push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour assurer une prise en charge des notifications, inscrivez votre application auprès de Google. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite. 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>Inscrire votre application pour l’accès à la Plateforme d’appareils connectés inter-appareils

Inscrivez ensuite votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de celle qui consiste à s’inscrire sur le Centre de développement Windows, qui a été abordée précédemment dans les étapes préliminaires. Elle autorise la Plateforme d’appareils connectés à envoyer des notifications à l’aide du service de notification Push natif. Le processus d’intégration du Centre de développement nécessite les éléments suivants :
* L’ID client de votre application.
* La clé Google Cloud Messaging. Ces informations sont nécessaires pour remettre les données et les commandes à l’application (sur un appareil qui est peut-être verrouillé ou en veille) sous forme de notifications Push. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configurer votre application pour la rendre compatible avec les notifications

Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour le rendre apte à recevoir des notifications Push. Si vous avez des doutes quant à la façon de procéder, consultez [Set up a Firebase Cloud Messaging client app on Android](https://firebase.google.com/docs/cloud-messaging/android/client).

### <a name="associate-the-notification-service-with-the-local-platform"></a>Associer le service de notification à la Plateforme locale

Enfin, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application. Dans les étapes précédentes, vous avez initialisé la Plateforme avec un paramètre `null` *notificationProvider*. Ici, vous devez construire et transmettre un objet qui implémente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** . La principale chose à noter est que la méthode `getNotificationRegistrationAsync` doit retourner une instance de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** . **NotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.


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

Transmettez cette inscription dans votre implémentation de **NotificationProvider**. Ensuite, l’appel d’initialisation de la **Plateforme** doit fournir à la **Plateforme** locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données de la Plateforme d’appareils connectés côté serveur, qui relaie les demandes de lancement et les messages de service d’application d’autres appareils. 

Il ne vous reste plus maintenant qu’à étendre la classe de votre service d’écoute natif (dans ce cas, [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService), puisque ce guide a utilisé Firebase Cloud Messaging) avec une surcharge spéciale de la méthode `onMessageReceived` (méthode de gestion des notifications).

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

Votre application est désormais capable de gérer les notifications à partir de la Plateforme d’appareils connectés.
