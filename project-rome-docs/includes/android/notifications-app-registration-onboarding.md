---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: bbef84bf-a6b7-44be-879d-0fa6065e37b1
ms.localizationpriority: medium
ms.openlocfilehash: 598807ac37079456ac28948a9f5bc419e65095a3
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907511"
---
### <a name="msa-and-aad-authentication-registration"></a>Compte de service administré et l’inscription de l’authentification AAD

Inscription de l’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour toutes les fonctionnalités du Kit de développement, y compris les Notifications, à l’exception de partage de Nearby API. 

Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).

Ensuite, si vous utilisez un compte de service administré en tant que l’authentification et l’infrastructure d’identité pour vos utilisateurs, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas de Microsoft compte de développeur, vous devez en créer un premier). Vous devez recevoir une chaîne d’ID client pour votre application ; Veillez à mémoriser l’emplacement ou l’enregistrer. Cela sera ultérieurement utilisé pendant l’intégration de Notifications de graphique. Notez qu’une application à l’aide de l’authentification MSA doit être enregistré comme une application Live SDK comme indiqué ci-dessous.
![Portail d’inscription des applications](../../notifications/media/msa_app_registration/app_registration_portal.png)

Si vous écrivez une application qui utilise AAD en tant que compte professionnel ou d’une authentification de compte scolaire et d’infrastructure d’identité, vous devez inscrire votre application via [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) afin d’obtenir l’ID client, comme indiqué ci-dessous. 
 ![Portail de l’enregistrement AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) lorsque vous créez une nouvelle inscription d’application, il existe quelques autorisations requises pour pouvoir utiliser les Notifications de graphique et d’autres fonctionnalités de plateforme d’appareil connecté. Consultez les informations ci-dessous. 
![Autorisations AAD d’inscription portail – définition – requis](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* Ajouter un utilisateur connectez-vous autorisation, affiché comme suit.
![Autorisations requises : profil d’utilisateur AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* Ajouter des autorisations de Service de commande pour les informations de périphérique, indiqué comme suit.
![Autorisations requises : les appareils](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* Ajoutez l’autorisation de Notifications de graphique sous l’activité Service API de flux, indiqué comme suit.
![Autorisations requises : les appareils](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* À la fin, si vous écrivez des applications inter-plateformes, y compris une application UWP en cours d’exécution sur Windows, veillez à ajouter l’autorisation, le Service de Notification Windows, affiché comme suit. 
![Autorisations requises – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
