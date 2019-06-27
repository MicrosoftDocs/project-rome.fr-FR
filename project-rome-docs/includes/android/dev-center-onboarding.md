---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907921"
---
## <a name="preliminary-setup-for-push-notifications"></a>Configuration préliminaire pour les notifications Push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour bénéficier d’une prise en charge de [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client), inscrivez votre application auprès de Google. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite. 

Une fois l’inscription effectuée, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans le Centre de développement Microsoft pour des expériences inter-appareils
Si vous avez besoin de communiquer avec votre appareil Android, vous devez inscrire votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de celle visant à inscrire une application MSA et AAD décrite plus haut.  Le principal objectif principal de ce processus est de mapper les identités d’application propres à la plateforme à une identité d’application multiplateforme qui est reconnue par la Plateforme d’appareils connectés et qui, dans le même temps, autorise la Plateforme à envoyer des notifications à l’aide des services de notification Push natifs correspondant à chaque plateforme mobile. Dans ce cas, elle permet la communication avec les points de terminaison d’application iOS via Firebase Cloud Messaging.

Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils à partir du volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils, comme illustré ci-dessous.
![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration du Centre de développement comprend les étapes suivantes :
* Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils. Vous pouvez sélectionner Windows, Android et/ou iOS.
![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournissez des ID d’application pour chaque plateforme sur laquelle votre application est présente. 
![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
> [!TIP] 
> Pour les applications Android, il s’agit du nom de package que vous avez attribué à votre application au moment de créer le projet. Vous trouverez le nom de package dans votre console Firebase sous Project Overview -> General.
![Console Firebase – Project Overview](../../notifications/media/dev_center_portal/firebase_overview.png)

* Fournissez ou sélectionnez les ID d’application des inscriptions d’application MSA et/ou AAD. Ces ID clients correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes d’inscription d’application MSA/AAD. 
![Expériences inter-appareils – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Les fonctionnalités de la Plateforme d’appareils connectés tirent parti de chacune des principales plateformes de notification natives pour envoyer des notifications aux points de terminaison clients d’application, à savoir, WNS (pour Windows UWP), GCM (pour Android) et APNS (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification pour permettre à la Plateforme de transmettre les notifications pour votre serveur d’applications, dans le cas où vous publiez des notifications ciblant l’utilisateur.
![Expériences inter-appareils – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Pour Android, l’activation du service Cloud Messaging est un prérequis pour communiquer avec un appareil Android. Pour plus d’informations, consultez [Set up a Firebase Cloud Messaging client app on Android](https://firebase.google.com/docs/cloud-messaging/android/client). Une fois que vous avez terminé l’intégration, vous pouvez fournir les informations d’identification Push à la Plateforme d’appareils connectés via le Centre de développement Windows. 
> [!TIP] 
> L’ID d’expéditeur exigé correspond à l’ID d’expéditeur Firebase Cloud Messaging et la clé d’API correspond à la clé serveur héritée. Vous pouvez trouver ces deux éléments dans Firebase Console -> Project -> Settings, sous l’onglet Cloud Messaging, comme le montre la capture d’écran.
![Console Firebase – Informations d’identification Push Android](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* La dernière étape consiste à vérifier votre domaine d’application inter-appareils, qui sert de processus de vérification pour prouver que votre application est propriétaire de ce domaine qui fait office d’identité d’application inter-appareils pour l’application que vous avez inscrite.
![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Traiter les notifications à mesure que l’application les reçoit

Une fois que l’Expérience inter-appareils a été validée dans le Centre de développement Microsoft Windows, vérifiez que votre application peut traiter les notifications à mesure qu’elles arrivent. 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
