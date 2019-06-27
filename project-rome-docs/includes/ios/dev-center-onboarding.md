---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907601"
---
## <a name="preliminary-setup-for-push-notifications"></a>Configuration préliminaire pour les notifications Push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour assurer une prise en charge d’[Apple Push Notification](https://developer.apple.com/notifications/), inscrivez votre application auprès d’Apple. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite. 

Une fois l’inscription effectuée, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans le Centre de développement Microsoft pour des expériences inter-appareils
Si vous avez besoin de communiquer avec votre appareil iOS, une inscription sur le Centre de développement Microsoft Windows s’avère nécessaire.  Ensuite, vous devez inscrire votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de celle visant à inscrire une application MSA et AAD décrite plus haut. Le principal objectif principal de ce processus est de mapper les identités d’application propres à la plateforme à une identité d’application multiplateforme qui est reconnue par la Plateforme d’appareils connectés et qui, dans le même temps, autorise la Plateforme à envoyer des notifications à l’aide des services de notification Push natifs correspondant à chaque plateforme mobile. Dans ce cas, elle permet la communication avec les points de terminaison d’application iOS via APNs (Apple Push Notification Service). Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils dans le volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils.
![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration du Centre de développement comprend les étapes suivantes :
* Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils. Vous pouvez sélectionner Windows, Android et/ou iOS.
![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournissez des ID d’application pour chaque plateforme sur laquelle votre application est présente.
![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
> [!TIP] 
> Pour les applications iOS, il s’agit du nom de package que vous avez attribué à votre application au moment de créer le projet. 

* Fournissez ou sélectionnez les ID d’application des inscriptions d’application MSA et/ou AAD. Ces ID clients correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes d’inscription d’application MSA/AAD.
![Expériences inter-appareils – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Les fonctionnalités de la Plateforme d’appareils connectés tirent parti de chacune des principales plateformes de notification natives pour envoyer des notifications aux points de terminaison clients d’application, à savoir, WNS (pour Windows UWP), GCM (pour Android) et APNs (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification pour permettre à la Plateforme de transmettre les notifications pour votre serveur d’applications, dans le cas où vous publiez des notifications ciblant l’utilisateur. 
![Expériences inter-appareils – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Pour iOS, l’activation d’APNs est un prérequis pour la communication avec un appareil iOS. Consultez [APNs Overview](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) pour plus d’informations. Une fois que vous avez terminé l’intégration, vous pouvez fournir les informations d’identification Push à la Plateforme d’appareils connectés via le Centre de développement Windows. 
* La dernière étape consiste à vérifier votre domaine d’application inter-appareils, qui sert de processus de vérification pour prouver que votre application est propriétaire de ce domaine qui fait office d’identité d’application inter-appareils pour l’application que vous avez inscrite.
![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Traiter les notifications à mesure que l’application les reçoit

Une fois que l’Expérience inter-appareils a été validée dans le Centre de développement Microsoft Windows, vérifiez que votre application peut traiter les notifications à mesure qu’elles arrivent. 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```