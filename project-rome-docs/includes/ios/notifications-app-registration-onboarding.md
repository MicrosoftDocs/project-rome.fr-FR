---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 57a5f2a1e7c40ace95656f9b08994f861b8cc9af
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755712"
---
### <a name="msa-and-aad-authentication-registration"></a>Compte de service administré et l’inscription de l’authentification AAD

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.

Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).

Ensuite, si vous utilisez un compte de service administré en tant que l’authentification et l’infrastructure d’identité pour vos utilisateurs, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas de Microsoft compte de développeur, vous devez en créer un premier). Vous devez recevoir une chaîne d’ID client pour votre application ; Veillez à mémoriser l’emplacement ou l’enregistrer. Cela sera ultérieurement utilisé pendant l’intégration de Notifications de graphique. Notez qu’une application à l’aide de l’authentification MSA doit être enregistré comme une application Live SDK.
![Portail d’inscription des applications](../../notifications/media/msa_app_registration/app_registration_portal.png)

Si vous écrivez une application qui utilise AAD en tant que compte professionnel ou d’une authentification de compte scolaire et d’infrastructure d’identité, vous devez inscrire votre application via [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) afin d’obtenir l’ID client. 
 ![Portail de l’enregistrement AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) lorsque vous créez une nouvelle inscription d’application, il existe quelques autorisations requises pour pouvoir utiliser les Notifications de graphique et d’autres fonctionnalités de plateforme d’appareil connecté. Consultez les informations ci-dessous. 
![Autorisations AAD d’inscription portail – définition – requis](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* Ajoutez l’autorisation de connexion de l’utilisateur.
![Autorisations requises : profil d’utilisateur AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* Ajouter des autorisations de Service de commande pour des informations sur l’appareil.
![Autorisations requises : les appareils](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* Ajoutez l’autorisation de Notifications de graphique sous l’activité de flux des API de Service.
![Autorisations requises : les appareils](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* À la fin, si vous écrivez des applications inter-plateformes, y compris une application UWP en cours d’exécution sur Windows, veillez à ajouter l’autorisation de Service de Notification Windows.
![Autorisations requises – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
