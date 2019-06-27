---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 57a5f2a1e7c40ace95656f9b08994f861b8cc9af
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755712"
---
### <a name="msa-and-aad-authentication-registration"></a>Inscription à l’authentification MSA et AAD

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.

Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).

Ensuite, si vous utilisez MSA comme framework d’authentification et d’identité pour vos utilisateurs, vous devez inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas de compte de développeur Microsoft, vous devez d’abord en créer un). Vous devez recevoir une chaîne d’ID client pour votre application ; veillez à mémoriser son emplacement ou à l’enregistrer. Elle sera utilisée par la suite durant l’intégration des notifications Graph. Notez qu’une application utilisant l’authentification MSA doit être inscrite en tant qu’application SDK Live.
![Portail d’inscription des applications](../../notifications/media/msa_app_registration/app_registration_portal.png)

Si vous écrivez une application qui utilise AAD comme framework d’authentification et d’identité de compte professionnel ou scolaire, vous devez inscrire votre application via les [Bibliothèques d’authentification d’Azure Active Directory Authentication](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) afin d’obtenir l’ID client. 
 ![Portail d’inscription AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) Au moment de créer une inscription d’application, quelques autorisations sont nécessaires pour utiliser les notifications Graph et d’autres fonctionnalités de la Plateforme d’appareils connectés. Voir ci-dessous. 
![Portail d’inscription AAD – Paramètres – Autorisations nécessaires](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* Ajoutez une autorisation de connexion utilisateur.
![Autorisations nécessaires – Profil utilisateur AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* Ajoutez des autorisations Service de commande pour les informations d’appareil.
![Autorisations nécessaires – Appareils](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* Ajoutez l’autorisation Notifications Graph sous les API de service de flux d’activités.
![Autorisations nécessaires – Appareils](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* Enfin, si vous écrivez une application multiplateforme, notamment une application UWP s’exécutant sur Windows, veillez à ajouter l’autorisation Service de notification Windows (WNS).
![Autorisations nécessaires – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
