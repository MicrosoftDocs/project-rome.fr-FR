---
title: Fichier Include
description: Fichier Include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: d94808ae1e97d12649f24ed89ad17a7962665d5e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803973"
---
### <a name="set-up-authentication-and-account-management"></a>Configurer l’authentification et gestion des comptes

La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.  Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.  Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [Android exemple d’application](https://github.com/Microsoft/project-rome/tree/master/Android/samples) qui génère et gère les jetons d’actualisation pour votre commodité.

Si vous souhaitez implémenter le **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** vous-même l’interface, prenez note des informations suivantes : 

Si vous utilisez un compte de service administré, vous devez inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`. 

Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.

Si vous utilisez fourni **ConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) : 
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
