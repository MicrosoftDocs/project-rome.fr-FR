---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907301"
---
### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application avec Google pour [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) prennent en charge. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard.

Une fois inscrit, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans Microsoft Windows Dev Center pour des expériences entre les périphériques

> [!IMPORTANT]
> Cette étape est uniquement nécessaire si vous souhaitez utiliser les fonctionnalités de Project Rome pour accéder aux données à partir d’ou effectuer des demandes des appareils non Windows. Si vous ciblez uniquement les appareils Windows, il est inutile d’effectuer cette étape.

Accédez au tableau de bord de centre de développement, accédez à des expériences entre les périphériques à partir du volet de navigation de gauche et sélectionnez la configuration d’une nouvelle application entre les périphériques, indiquée comme suit.
![Tableau de bord de centre de développement, des expériences entre les périphériques](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration de centre de développement nécessite les étapes suivantes :
* Sélectionnez les plateformes prises en charge : sélectionnez les plateformes où votre application aura une présence et être activée pour des expériences entre les périphériques. Dans le cas d’intégration de Notifications de graphique, vous pouvez sélectionner à partir de Windows, Android ou iOS.
![Expériences inter-périphériques – plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournir l’ID d’application : fournit un ID d’application pour chacun de la plateforme où votre application a une présence. Pour les applications Android, ceci est le nom du Package affecté à votre application lorsque vous avez créé le projet. Vous trouverez le nom du Package dans votre console Firebase sous vue d’ensemble du projet -> Général. Vous pouvez ajouter des ID différents (jusqu'à dix) par plateforme, c'est-à-dire au cas où vous avez plusieurs versions de la même application, ou même différentes applications, que vous souhaitez être en mesure de recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
![Expériences inter-périphériques – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Fournir ou sélectionnez l’ID d’application à partir des inscriptions MSA et/ou AAD. Ces ID de client correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes de l’inscription app MSA/AAD ci-dessus. 
![Expériences inter-périphériques – MSA et les inscriptions d’application AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Notifications de graphique et d’autres fonctionnalités de plateforme de périphériques connectés tirer parti de chacune des plateformes de notification native sur les principales plateformes pour envoyer des notifications à l’application points de terminaison clients, à savoir, WNS (pour Windows UWP), FCM (pour Android) et APNS (pour iOS) . Fournissez vos informations d’identification pour ces plateformes de notification activer les Notifications de graphique d’envoyer des notifications pour le serveur de votre application, lorsque vous publiez des notifications ciblées de l’utilisateur. Pour Android, [activer le service Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) est une condition préalable à l’aide de Microsoft Graph Notifications. En outre, notez que l’ID d’expéditeur correspond à l’ID d’expéditeur Firebase Cloud Messaging, et la clé d’API correspond à la clé du serveur hérité. Les deux peuvent être trouvés dans la Console Firebase -> projet -> Paramètres, sous l’onglet Cloud Messaging, comme illustré dans la capture d’écran.
![Expériences inter-périphériques – informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* La dernière étape consiste à vérifier votre domaine inter-périphériques app, qui sert d’un processus de vérification pour prouver que votre application est propriétaire de ce domaine qui agit comme une identité d’application d’entre les périphériques de l’application que vous avez inscrit.
![Expériences inter-périphériques – vérification du domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
