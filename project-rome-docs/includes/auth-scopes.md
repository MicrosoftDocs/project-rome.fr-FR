---
title: Fichier include
description: Fichier include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b81da462f97569d322b76ebff36f800c970c06cc
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901554"
---
### <a name="set-up-authentication-and-account-management"></a>Configuration de l’authentification et de la gestion des comptes

La Plateforme d’appareils connectés exige l’utilisation d’un jeton OAuth pendant l’inscription.  Vous pouvez générer et gérer les jetons OAuth en employant la méthode qui vous convient le mieux.  Cependant, pour aider les développeurs à commencer à utiliser la plateforme, nous avons inclus un fournisseur d’authentification dans l’[exemple d’application Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) qui génère et gère des jetons d’actualisation dans votre application pour vous faciliter la tâche.

Si vous souhaitez implémenter l’interface **[ConnectedDevicesAccountManager](/java/api/com.microsoft.connecteddevices.core._user_account_provider)** par vous-même, tenez compte des points suivants : 

Si vous utilisez un compte MSA, vous devez inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`. 

Si vous utilisez un compte AAD, vous devrez demander les audiences suivantes : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` et `"https://activity.microsoft.com"`.

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.

Que vous utilisiez l’implémentation **ConnectedDevicesAccountManager** fournie ou non, si vous utilisez AAD, vous devrez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > Inscriptions des applications) : 
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