---
title: Fichier include
description: Fichier include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755766"
---
### <a name="set-up-authentication-and-account-management"></a>Configuration de l’authentification et de la gestion des comptes

La Plateforme d’appareils connectés exige l’utilisation d’un jeton OAuth pendant l’inscription.  Vous pouvez générer et gérer les jetons OAuth en employant la méthode qui vous convient le mieux.  Cependant, pour aider les développeurs dans la prise en main de la plateforme, nous avons inclus un fournisseur d’authentification dans l’[exemple d’application iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que vous pouvez utiliser pour générer et gérer des jetons d’actualisation dans votre application.

Si vous n’utilisez pas le code fourni, vous devez vous-même implémenter l’interface **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** .

Si vous utilisez un compte MSA, incluez les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.

Si vous utilisez un compte AAD, vous devrez demander les audiences suivantes : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` et `"https://activity.microsoft.com"`.

Que vous utilisiez l’implémentation **MCDConnectedDevicesAccountManager** fournie ou non, si vous utilisez AAD, vous devrez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > Inscriptions des applications) :
* Service de flux d’activités Microsoft 
  * Remettez et modifiez les notifications utilisateur pour cette application
  * Lisez et écrivez l’activité de l’application dans le flux d’activités des utilisateurs
* Services de notifications Windows
  * Connectez votre appareil au service de notification Windows 
* Service d’annuaire d’appareils Microsoft
  * Consultez votre liste d’appareils
  * Faites-vous ajouter à votre liste d’appareils et d’applications 
* Service de commande Microsoft
  * Communiquez avec les appareils utilisateur
  * Lisez les appareils utilisateur
