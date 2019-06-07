---
title: Fichier Include
description: Fichier Include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: a6e92df6114443827b22dc85cf877d631e5fcfdf
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755781"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="1fb95-103">Configurer l’authentification et gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="1fb95-103">Set up authentication and account management</span></span>

<span data-ttu-id="1fb95-104">La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="1fb95-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="1fb95-105">Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.</span><span class="sxs-lookup"><span data-stu-id="1fb95-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="1fb95-106">Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [Android exemple d’application](https://github.com/Microsoft/project-rome/tree/master/Android/samples) qui génère et gère les jetons d’actualisation pour votre commodité.</span><span class="sxs-lookup"><span data-stu-id="1fb95-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="1fb95-107">Si vous souhaitez implémenter le **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** vous-même l’interface, prenez note des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1fb95-107">If you wish to implement the **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="1fb95-108">Si vous utilisez un compte de service administré, vous devez inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="1fb95-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="1fb95-109">Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="1fb95-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

> [!NOTE]
> <span data-ttu-id="1fb95-110">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.</span><span class="sxs-lookup"><span data-stu-id="1fb95-110">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="1fb95-111">Si vous utilisez fourni **ConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) :</span><span class="sxs-lookup"><span data-stu-id="1fb95-111">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="1fb95-112">Activité de Microsoft Service de flux</span><span class="sxs-lookup"><span data-stu-id="1fb95-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="1fb95-113">Fournir et modifier des notifications à l’utilisateur pour cette application</span><span class="sxs-lookup"><span data-stu-id="1fb95-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="1fb95-114">Lire et écrire l’activité de l’application dans les flux d’activités des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1fb95-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="1fb95-115">Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="1fb95-115">Windows Notification Service</span></span>
  * <span data-ttu-id="1fb95-116">Connecter votre appareil au Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="1fb95-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="1fb95-117">Service d’annuaire Microsoft Device</span><span class="sxs-lookup"><span data-stu-id="1fb95-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="1fb95-118">Afficher la liste des appareils</span><span class="sxs-lookup"><span data-stu-id="1fb95-118">See your list of devices</span></span>
  * <span data-ttu-id="1fb95-119">Ajouter à votre liste d’appareils et applications</span><span class="sxs-lookup"><span data-stu-id="1fb95-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="1fb95-120">Service de commande de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1fb95-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="1fb95-121">Communiquer avec les appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1fb95-121">Communicate with user devices</span></span>
  * <span data-ttu-id="1fb95-122">Lire des appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1fb95-122">Read user devices</span></span>
