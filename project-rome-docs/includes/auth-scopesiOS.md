---
title: Fichier Include
description: Fichier Include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755766"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="a69d4-103">Configurer l’authentification et gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="a69d4-103">Set up authentication and account management</span></span>

<span data-ttu-id="a69d4-104">La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="a69d4-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="a69d4-105">Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.</span><span class="sxs-lookup"><span data-stu-id="a69d4-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="a69d4-106">Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [iOS exemple d’application](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que vous pouvez utiliser pour générer et gérer des jetons d’actualisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a69d4-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="a69d4-107">Si vous n’utilisez pas le code fourni, vous devez implémenter le **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface vous-même.</span><span class="sxs-lookup"><span data-stu-id="a69d4-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="a69d4-108">Si vous utilisez un compte de service administré, inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="a69d4-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

> [!NOTE]
> <span data-ttu-id="a69d4-109">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.</span><span class="sxs-lookup"><span data-stu-id="a69d4-109">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="a69d4-110">Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="a69d4-110">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="a69d4-111">Si vous utilisez fourni **MCDConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) :</span><span class="sxs-lookup"><span data-stu-id="a69d4-111">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="a69d4-112">Activité de Microsoft Service de flux</span><span class="sxs-lookup"><span data-stu-id="a69d4-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="a69d4-113">Fournir et modifier des notifications à l’utilisateur pour cette application</span><span class="sxs-lookup"><span data-stu-id="a69d4-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="a69d4-114">Lire et écrire l’activité de l’application dans les flux d’activités des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a69d4-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="a69d4-115">Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="a69d4-115">Windows Notification Service</span></span>
  * <span data-ttu-id="a69d4-116">Connecter votre appareil au Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="a69d4-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="a69d4-117">Service d’annuaire Microsoft Device</span><span class="sxs-lookup"><span data-stu-id="a69d4-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="a69d4-118">Afficher la liste des appareils</span><span class="sxs-lookup"><span data-stu-id="a69d4-118">See your list of devices</span></span>
  * <span data-ttu-id="a69d4-119">Ajouter à votre liste d’appareils et applications</span><span class="sxs-lookup"><span data-stu-id="a69d4-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="a69d4-120">Service de commande de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a69d4-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="a69d4-121">Communiquer avec les appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a69d4-121">Communicate with user devices</span></span>
  * <span data-ttu-id="a69d4-122">Lire des appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a69d4-122">Read user devices</span></span>
