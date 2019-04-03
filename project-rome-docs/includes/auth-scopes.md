---
title: Fichier Include
description: Fichier Include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: d94808ae1e97d12649f24ed89ad17a7962665d5e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907861"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="0c773-103">Configurer l’authentification et gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="0c773-103">Set up authentication and account management</span></span>

<span data-ttu-id="0c773-104">La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="0c773-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="0c773-105">Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.</span><span class="sxs-lookup"><span data-stu-id="0c773-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="0c773-106">Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [Android exemple d’application](https://github.com/Microsoft/project-rome/tree/master/Android/samples) qui génère et gère les jetons d’actualisation pour votre commodité.</span><span class="sxs-lookup"><span data-stu-id="0c773-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="0c773-107">Si vous souhaitez implémenter le **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** vous-même l’interface, prenez note des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c773-107">If you wish to implement the **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="0c773-108">Si vous utilisez un compte de service administré, vous devez inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="0c773-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="0c773-109">Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="0c773-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="0c773-110">Si vous utilisez fourni **ConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) :</span><span class="sxs-lookup"><span data-stu-id="0c773-110">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="0c773-111">Activité de Microsoft Service de flux</span><span class="sxs-lookup"><span data-stu-id="0c773-111">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="0c773-112">Fournir et modifier des notifications à l’utilisateur pour cette application</span><span class="sxs-lookup"><span data-stu-id="0c773-112">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="0c773-113">Lire et écrire l’activité de l’application dans les flux d’activités des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="0c773-113">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="0c773-114">Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="0c773-114">Windows Notification Service</span></span>
  * <span data-ttu-id="0c773-115">Connecter votre appareil au Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="0c773-115">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="0c773-116">Service d’annuaire Microsoft Device</span><span class="sxs-lookup"><span data-stu-id="0c773-116">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="0c773-117">Afficher la liste des appareils</span><span class="sxs-lookup"><span data-stu-id="0c773-117">See your list of devices</span></span>
  * <span data-ttu-id="0c773-118">Ajouter à votre liste d’appareils et applications</span><span class="sxs-lookup"><span data-stu-id="0c773-118">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="0c773-119">Service de commande de Microsoft</span><span class="sxs-lookup"><span data-stu-id="0c773-119">Microsoft Command Service</span></span>
  * <span data-ttu-id="0c773-120">Communiquer avec les appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="0c773-120">Communicate with user devices</span></span>
  * <span data-ttu-id="0c773-121">Lire des appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="0c773-121">Read user devices</span></span>
