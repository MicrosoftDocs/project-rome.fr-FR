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
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="a6796-103">Configurer l’authentification et gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="a6796-103">Set up authentication and account management</span></span>

<span data-ttu-id="a6796-104">La plateforme d’appareils connectés requiert un jeton OAuth valide à utiliser dans le processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="a6796-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="a6796-105">Vous pouvez utiliser votre méthode préférée de génération et la gestion des jetons OAuth.</span><span class="sxs-lookup"><span data-stu-id="a6796-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="a6796-106">Toutefois, pour aider les développeurs prise en main à l’aide de la plateforme, nous avons inclus un fournisseur d’authentification dans le cadre de la [iOS exemple d’application](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que vous pouvez utiliser pour générer et gérer des jetons d’actualisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a6796-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="a6796-107">Si vous n’utilisez pas le code fourni, vous devez implémenter le **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface vous-même.</span><span class="sxs-lookup"><span data-stu-id="a6796-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="a6796-108">Si vous utilisez un compte de service administré, inclure les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="a6796-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

<span data-ttu-id="a6796-109">Si vous utilisez un compte AAD, vous devrez demander aux publics suivants : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, et `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="a6796-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="a6796-110">Si vous utilisez fourni **MCDConnectedDevicesAccountManager** implémentation ou non, si vous utilisez AAD, vous devez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > inscriptions d’application) :</span><span class="sxs-lookup"><span data-stu-id="a6796-110">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="a6796-111">Activité de Microsoft Service de flux</span><span class="sxs-lookup"><span data-stu-id="a6796-111">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="a6796-112">Fournir et modifier des notifications à l’utilisateur pour cette application</span><span class="sxs-lookup"><span data-stu-id="a6796-112">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="a6796-113">Lire et écrire l’activité de l’application dans les flux d’activités des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a6796-113">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="a6796-114">Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="a6796-114">Windows Notification Service</span></span>
  * <span data-ttu-id="a6796-115">Connecter votre appareil au Service de Notification de Windows</span><span class="sxs-lookup"><span data-stu-id="a6796-115">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="a6796-116">Service d’annuaire Microsoft Device</span><span class="sxs-lookup"><span data-stu-id="a6796-116">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="a6796-117">Afficher la liste des appareils</span><span class="sxs-lookup"><span data-stu-id="a6796-117">See your list of devices</span></span>
  * <span data-ttu-id="a6796-118">Ajouter à votre liste d’appareils et applications</span><span class="sxs-lookup"><span data-stu-id="a6796-118">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="a6796-119">Service de commande de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a6796-119">Microsoft Command Service</span></span>
  * <span data-ttu-id="a6796-120">Communiquer avec les appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a6796-120">Communicate with user devices</span></span>
  * <span data-ttu-id="a6796-121">Lire des appareils des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a6796-121">Read user devices</span></span>
