---
title: Fichier Include
description: Fichier Include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: 1aa6b0d971feb7d2f9f8d31708fda31d05b5aca9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907901"
---
### <a name="set-up-authentication-and-account-management"></a>Configurer l’authentification et gestion des comptes

La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.  Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.  Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [iOS exemple d’application](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que vous pouvez utiliser pour générer et gérer des jetons d’actualisation dans votre application.

Si vous n’utilisez pas le code fourni, vous devez implémenter le **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface vous-même.

Si vous utilisez un compte de service administré, inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.

Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.

Si vous utilisez fourni **MCDConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) :
* Activité de Microsoft Service de flux 
  * Fournir et modifier des notifications à l’utilisateur pour cette application
  * Lire et écrire l’activité de l’application dans les flux d’activités des utilisateurs
* Service de Notification de Windows
  * Connecter votre appareil au Service de Notification de Windows 
* Service d’annuaire Microsoft Device
  * Afficher la liste des appareils
  * Ajouter à votre liste d’appareils et applications 
* Service de commande de Microsoft
  * Communiquer avec les appareils des utilisateurs
  * Lire des appareils des utilisateurs
