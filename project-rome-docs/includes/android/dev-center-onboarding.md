---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907921"
---
## <a name="preliminary-setup-for-push-notifications"></a>Programme d’installation préliminaire pour les notifications push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application avec Google pour [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) prennent en charge. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard. 

Une fois inscrit, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.

```Java
notificationRegistration = new ConnectedDevicesNotificationRegistration();
notificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
notificationRegistration.setToken(token);
notificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
notificationRegistration.setAppDisplayName("SampleApp");

mConnectedDevicesPlatform.getNotificationRegistrationManager().registerForAccountAsync(mConnectedDevicesAccount).whenComplete(() -> {
  // Now that notifications are registered, this account can receive replies to commands and incoming commands.
});
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans Microsoft Windows Dev Center pour des expériences entre les périphériques
Si vous avez besoin de communication sur votre appareil Android, vous devez inscrire votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une autre procédure à partir du compte de service administré et AAD inscription d’application ci-dessus.  L’objectif principal de ce processus consiste à mapper les identités d’application spécifiques de plateforme avec une identité d’application multiplateforme qui est reconnu par la plateforme de périphériques connectés et en même temps autorise la plateforme pour envoyer des notifications à l’aide de la notification push native services correspondant à chaque plate-forme mobile. Dans ce cas, il l’Active assure la communication aux points de terminaison iOS application par le biais de Firebase Cloud Messaging.

Accédez au tableau de bord de centre de développement, accédez à des expériences entre les périphériques à partir du volet de navigation de gauche et sélectionnez la configuration d’une nouvelle application entre les périphériques, indiquée comme suit.
![Tableau de bord de centre de développement, des expériences entre les périphériques](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration de centre de développement nécessite les étapes suivantes :
* Sélectionnez les plateformes prises en charge : sélectionnez les plateformes où votre application aura une présence et être activée pour des expériences entre les périphériques. Vous pouvez sélectionner à partir de Windows, Android ou iOS.
![Expériences inter-périphériques – plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournir l’ID d’application : fournit un ID d’application pour chacun de la plateforme où votre application a une présence. 
![Expériences inter-périphériques – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Vous pouvez ajouter des ID différents (jusqu'à dix) par plateforme, c'est-à-dire au cas où vous avez plusieurs versions de la même application, ou même différentes applications, que vous souhaitez être en mesure de recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
> [!TIP] 
> Pour les applications Android, ceci est le nom du Package affecté à votre application lorsque vous avez créé le projet. Vous trouverez le nom du Package dans votre console Firebase sous vue d’ensemble du projet -> Général.
![Console firebase – vue d’ensemble du projet](../../notifications/media/dev_center_portal/firebase_overview.png)

* Fournir ou sélectionnez l’ID d’application à partir des inscriptions MSA et/ou AAD. Ces ID de client correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes de l’inscription app MSA/AAD ci-dessus. 
![Expériences inter-périphériques – MSA et les inscriptions d’application AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Connecté la plateforme d’appareils fonctionnalités tirent parti chaque des plateformes de notification native sur les principales plateformes pour envoyer des notifications au client de l’application points de terminaison, à savoir, WNS (pour Windows UWP), GCM (pour Android) et APNS (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification activer la plateforme d’envoyer des notifications pour le serveur de votre application, lorsque vous publiez des notifications ciblées de l’utilisateur.
![Expériences inter-périphériques – informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Pour Android, l’activation de service de messagerie de Cloud est un composant requis pour communiquer avec un appareil Android. Consultez [défini d’un Firebase Cloud Messaging Application cliente sur Android](https://firebase.google.com/docs/cloud-messaging/android/client) pour plus d’informations. Une fois que vous avez terminé l’intégration, vous pouvez ensuite fournir les informations d’identification push via le centre de développement Windows pour la plateforme d’appareils connectés. 
> [!TIP] 
> L’ID d’expéditeur correspond à Firebase Cloud Messaging Sender ID et la clé d’API correspond à la clé du serveur hérité. Les deux peuvent être trouvés dans la Console Firebase -> projet -> Paramètres, sous l’onglet Cloud Messaging, comme illustré dans la capture d’écran.
![Console firebase – informations d’identification Push Android](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* La dernière étape consiste à vérifier votre domaine inter-périphériques app, qui sert d’un processus de vérification pour prouver que votre application est propriétaire de ce domaine qui agit comme une identité d’application d’entre les périphériques de l’application que vous avez inscrit.
![Expériences inter-périphériques – vérification du domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Traiter les notifications telles qu’elles sont reçues par l’application

Une fois que l’expérience entre les périphériques dans le Microsoft Windows Dev Center a été validé, assurez-vous que votre application peut traiter les notifications qu’ils vous parviennent. 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
