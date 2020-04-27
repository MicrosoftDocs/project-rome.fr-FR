---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909291"
---
### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour assurer une prise en charge d’[Apple Push Notification](https://developer.apple.com/notifications/), inscrivez votre application auprès d’Apple. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez, car vous en aurez besoin par la suite.

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

> [!WARNING]
> Cette étape n’est nécessaire que si vous souhaitez utiliser les fonctionnalités du projet Rome pour accéder à des données ou effectuer des demandes à partir d’appareils non Windows. Si vous ciblez uniquement des appareils Windows, vous n’avez pas besoin d’effectuer cette étape.

Inscrivez votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de celle visant à inscrire une application MSA et AAD décrite plus haut. L’objectif principal de ce processus est de mapper les identités d’application d’une plateforme spécifique à une identité d’application multiplateforme qui est reconnue par la Plateforme d’appareils connectés. Cette étape permettra aussi l’envoi de notifications à l’aide des services de notification Push natifs correspondant aux plateformes mobiles utilises par votre application. Dans le cas d’iOS, elle permet l’envoi de notifications aux points de terminaison d’application iOS via APNS (Apple Push Notification Service).

Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils dans le volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils.
![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration du Centre de développement comprend les étapes suivantes :

* Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils. Dans le cas de l’intégration des notifications Graph, vous pouvez sélectionner Windows, Android et/ou iOS, selon les plateformes que vous utilisez. ![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournissez des ID d’application pour chaque plateforme utilisée. Pour les applications iOS, il s’agit du nom de package que vous avez attribué à votre application au moment de créer le projet. Notez que vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. ![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Fournissez ou sélectionnez les ID d’application des inscriptions d’application MSA et/ou AAD obtenus aux étapes d’inscription d’application MSA/AAD précédentes. ![Expériences inter-périphériques – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Fournissez vos informations d’identification pour les plateformes de notification natives correspondant à votre application (c’est-à-dire, WNS pour Windows, FCM pour Android et/ou APNS pour iOS) pour permettre à votre serveur d’applications de transmettre les notifications ciblant l’utilisateur, dans le cas où vous en publiez. ![Expériences inter-périphériques – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* Enfin, vérifiez votre domaine d’application inter-appareils pour être certain que votre application en est propriétaire et que vous pouvez l’utiliser comme identité inter-appareils pour votre application. ![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
