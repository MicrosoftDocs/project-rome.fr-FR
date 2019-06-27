---
ms.openlocfilehash: 6c87f1a68699de7852af56d7536f08b1a5f9bc14
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907561"
---
### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Inscrire votre application dans le Centre de développement Microsoft pour des expériences inter-appareils
Ensuite, vous devez inscrire votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de celle visant à inscrire une application MSA et AA, qui a été abordée dans les étapes précédentes. Le principal objectif principal de ce processus est de mapper les identités d’application propres à la plateforme à une identité d’application multiplateforme qui est reconnue par la Plateforme d’appareils connectés et qui, dans le même temps, autorise la fonctionnalités de notifications Microsoft Graph à envoyer des notifications à l’aide des services de notification Push natifs correspondant à chaque plateforme de système d’exploitation. Dans ce cas, il permet à la fonctionnalité de notifications Graph d’envoyer des notifications aux points de terminaison d’application Windows UWP via le service de notification Windows (WNS). Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils à partir du volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils, comme illustré ci-dessous.
![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

Le processus d’intégration du Centre de développement comprend les étapes suivantes :
* Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils. Dans le cas de l’intégration des notifications Graph, vous pouvez sélectionner Windows, Android et/ou iOS. Illustré ci-dessous.
![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Fournissez des ID d’application pour chaque plateforme sur laquelle votre application est présente. Illustré ci-dessous.
![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur. 

* Fournissez ou sélectionnez les ID d’application à partir des inscriptions d’application MSA et/ou AAD. Ces ID clients correspondant à l’inscription d’application MSA ou AAD ont été obtenus aux étapes précédentes d’inscription d’application MSA/AAD. Illustré ci-dessous. 
![Expériences inter-périphériques – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Les notifications Graph et les autres fonctionnalités de la Plateforme d’appareils connectés tirent parti de chacune des principales plateformes de notification natives pour envoyer des notifications aux points de terminaison clients d’application, à savoir, WNS (pour Windows UWP), GCM (pour Android) et APNS (pour iOS). Fournissez vos informations d’identification pour ces plateformes de notification pour permettre aux notifications Graph de transmettre les notifications pour votre serveur d’applications, dans le cas où vous publiez des notifications ciblant l’utilisateur. Illustré ci-dessous. 
![Expériences inter-périphériques – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Pour les applications Windows UWP, l’activation des notifications Push WNS est un prérequis pour l’utilisation des notifications Microsoft Graph. Consultez [Vue d’ensemble de WNS](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview) pour plus d’informations. Une fois que vous avez terminé l’intégration, vous pouvez fournir les informations d’identification Push à la Plateforme d’appareils connectés via le Centre de développement Windows. 
* La dernière étape consiste à vérifier votre domaine d’application inter-appareils, qui sert de processus de vérification pour prouver que votre application est propriétaire de ce domaine qui fait office d’identité d’application inter-appareils pour l’application que vous avez inscrite. Illustré ci-dessous.  
![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png) Maintenant, vous êtes prêt pour l’intégration ! Passez à la section suivante. 


