---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "58907301"
---
### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour bénéficier d’une prise en charge de [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client), inscrivez votre application auprès de Google. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite.

Une fois l’inscription effectuée, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans le Centre de développement Microsoft pour des expériences inter-appareils

> [!IMPORTANT]
> Cette étape n’est nécessaire que si vous souhaitez utiliser les fonctionnalités du projet Rome pour accéder à des données ou effectuer des demandes à partir d’appareils non Windows. Si vous ciblez uniquement des appareils Windows, vous n’avez pas besoin d’effectuer cette étape.

Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils à partir du volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils, comme illustré ci-dessous.
![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration du Centre de développement comprend les étapes suivantes :
* Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils. Dans le cas de l’intégration des notifications Graph, vous pouvez sélectionner Windows, Android et/ou iOS.
![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournissez des ID d’application pour chaque plateforme sur laquelle votre application est présente. Pour les applications Android, il s’agit du nom de package que vous avez attribué à votre application au moment de créer le projet. Vous trouverez le nom de package dans votre console Firebase sous Project Overview -> General. Vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 
![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Fournissez ou sélectionnez les ID d’application des inscriptions d’application MSA et/ou AAD. Ces ID clients correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes d’inscription d’application MSA/AAD. 
![Expériences inter-appareils – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Les notifications Graph et les autres fonctionnalités de la Plateforme d’appareils connectés tirent parti de chacune des principales plateformes de notification natives pour envoyer des notifications aux points de terminaison clients d’application, à savoir, WNS (pour Windows UWP), FCM (pour Android) et APNS (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification pour permettre aux notifications Graph de transmettre les notifications pour votre serveur d’applications, dans le cas où vous publiez des notifications ciblant l’utilisateur. Pour Android, l’[activation du service Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) est un prérequis pour l’utilisation les notifications Microsoft Graph. De même, notez que l’ID d’expéditeur exigé correspond à l’ID d’expéditeur Firebase Cloud Messaging et que la clé d’API correspond à la clé serveur héritée. Vous pouvez trouver ces deux éléments dans Firebase Console -> Project -> Settings, sous l’onglet Cloud Messaging, comme le montre la capture d’écran.
![Expériences inter-appareils – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* La dernière étape consiste à vérifier votre domaine d’application inter-appareils, qui sert de processus de vérification pour prouver que votre application est propriétaire de ce domaine qui fait office d’identité d’application inter-appareils pour l’application que vous avez inscrite.
![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
