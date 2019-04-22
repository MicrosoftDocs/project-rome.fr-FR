---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909291"
---
### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application auprès d’Apple pour [Apns](https://developer.apple.com/notifications/) prennent en charge. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez comme vous en aurez besoin plus tard.

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

> [!WARNING]
> Cette étape est uniquement nécessaire si vous souhaitez utiliser les fonctionnalités de Project Rome pour accéder aux données à partir d’ou effectuer des demandes des appareils non Windows. Si vous ciblez uniquement les appareils Windows, il est inutile d’effectuer cette étape.

Inscrire votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une autre procédure à partir du compte de service administré et AAD inscription d’application ci-dessus. L’objectif principal de ce processus consiste à mapper les identités d’application spécifiques de plateforme avec une identité d’application multiplateforme qui est reconnu par la plateforme de périphériques connectés. Cette étape active également l’envoi de notifications à l’aide de correspondant pour les plateformes mobiles que votre application utilise les services de notification push natif. Pour iOS, il active les notifications à envoyer aux points de terminaison iOS app via APNS, Apple Push Notification Service.

Accédez au tableau de bord de centre de développement, accédez à des expériences entre les périphériques à partir du volet de navigation de gauche et sélectionnez la configuration d’une nouvelle application entre les périphériques.
![Tableau de bord de centre de développement, des expériences entre les périphériques](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration de centre de développement requièrent les étapes suivantes :

* Sélectionnez les plateformes prises en charge : sélectionnez les plateformes où votre application aura une présence et être activée pour des expériences entre les périphériques. Dans le cas d’intégration de Notifications de graphique, vous pouvez sélectionner à partir de Windows, Android ou iOS, en fonction des plateformes que vous utilisez. ![Expériences inter-périphériques – plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournir l’ID d’application – permet de fournir des ID d’application pour chaque plateforme que vous utilisez. Pour les applications iOS, ceci est le nom du package affecté à votre application lorsque vous avez créé le projet. Notez que vous pouvez ajouter des ID différents (jusqu'à dix) par plateforme, c'est-à-dire au cas où vous avez plusieurs versions de la même application, ou même différentes applications, que vous souhaitez être en mesure de recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. ![Expériences inter-périphériques – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Fournir ou sélectionnez l’ID d’application à partir des inscriptions d’application MSA et/ou AAD obtenues dans les cours MSA/AAD application d’enregistrement des étapes ci-dessus. ![Expériences inter-périphériques – MSA et les inscriptions d’application AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Fournissez vos informations d’identification pour les plateformes de notification native pertinentes pour votre application (WNS pour Windows, FCM pour Android ou APNS pour iOS) pour activer la remise des notifications à partir de votre serveur d’applications lorsque vous publiez des notifications ciblées de l’utilisateur. ![Expériences inter-périphériques – informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* Enfin, vérifiez votre domaine d’application d’entre les périphériques pour vous assurer que votre application est propriétaire du domaine et pouvez l’utiliser comme une identité entre les périphériques pour votre application. ![Expériences inter-périphériques – vérification du domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
