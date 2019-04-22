---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907601"
---
## <a name="preliminary-setup-for-push-notifications"></a>Programme d’installation préliminaire pour les notifications push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application auprès d’Apple pour [Apns](https://developer.apple.com/notifications/) prennent en charge. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard. 

Une fois inscrit, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans Microsoft Windows Dev Center pour des expériences entre les périphériques
Si vous avez besoin de communication sur votre appareil iOS, vous devrez inscrire avec le Microsoft Windows Dev Center.  Ensuite, vous devez inscrire votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une autre procédure à partir du compte de service administré et AAD inscription d’application ci-dessus. L’objectif principal de ce processus consiste à mapper les identités d’application spécifiques de plateforme avec une identité d’application multiplateforme qui est reconnu par la plateforme de périphériques connectés et en même temps autorise la plateforme pour envoyer des notifications à l’aide de la notification push native services correspondant à chaque plate-forme mobile. Dans ce cas, il permet la communication aux points de terminaison iOS app via APNs, Apple Push Notification Service. Accédez au tableau de bord de centre de développement, accédez à des expériences entre les périphériques à partir du volet de navigation de gauche et sélectionnez la configuration d’une nouvelle application entre les périphériques.
![Tableau de bord de centre de développement, des expériences entre les périphériques](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration de centre de développement requièrent les étapes suivantes :
* Sélectionnez les plateformes prises en charge : sélectionnez les plateformes où votre application aura une présence et être activée pour des expériences entre les périphériques. Vous pouvez sélectionner à partir de Windows, Android ou iOS.
![Expériences inter-périphériques – plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournir l’ID d’application : fournit un ID d’application pour chacun de la plateforme où votre application a une présence.
![Expériences inter-périphériques – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Vous pouvez ajouter des ID différents (jusqu'à dix) par plateforme, c'est-à-dire au cas où vous avez plusieurs versions de la même application, ou même différentes applications, que vous souhaitez être en mesure de recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
> [!TIP] 
> Pour les applications iOS, ceci est le nom du Package affecté à votre application lorsque vous avez créé le projet. 

* Fournir ou sélectionnez l’ID d’application à partir des inscriptions MSA et/ou AAD. Ces ID de client correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes de l’inscription app MSA/AAD ci-dessus.
![Expériences inter-périphériques – MSA et les inscriptions d’application AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Connecté la plateforme d’appareils fonctionnalités tire parti chaque des plateformes de notification native sur les principales plateformes pour envoyer des notifications au client de l’application points de terminaison, à savoir, WNS (pour Windows UWP), GCM (pour Android) et APNs (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification activer la plateforme d’envoyer des notifications pour le serveur de votre application, lorsque vous publiez des notifications ciblées de l’utilisateur. 
![Expériences inter-périphériques – informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Pour iOS, l’activation de APNs est une condition préalable à la communication sur un appareil iOS. Consultez [vue d’ensemble de l’APNs](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) pour plus d’informations. Une fois que vous avez terminé l’intégration, vous pouvez ensuite fournir les informations d’identification push via le centre de développement Windows pour la plateforme d’appareils connectés. 
* La dernière étape consiste à vérifier votre domaine inter-périphériques app, qui sert d’un processus de vérification pour prouver que votre application est propriétaire de ce domaine qui agit comme une identité d’application d’entre les périphériques de l’application que vous avez inscrit.
![Expériences inter-périphériques – vérification du domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Traiter les notifications telles qu’elles sont reçues par l’application

Une fois que l’expérience entre les périphériques dans le Microsoft Windows Dev Center a été validé, assurez-vous que votre application peut traiter les notifications qu’ils vous parviennent. 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```