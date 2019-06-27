---
title: Fichier include
description: Fichier include
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755766"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="c5ce8-103">Configuration de l’authentification et de la gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="c5ce8-103">Set up authentication and account management</span></span>

<span data-ttu-id="c5ce8-104">La Plateforme d’appareils connectés exige l’utilisation d’un jeton OAuth pendant l’inscription.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="c5ce8-105">Vous pouvez générer et gérer les jetons OAuth en employant la méthode qui vous convient le mieux.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="c5ce8-106">Cependant, pour aider les développeurs dans la prise en main de la plateforme, nous avons inclus un fournisseur d’authentification dans l’[exemple d’application iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que vous pouvez utiliser pour générer et gérer des jetons d’actualisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="c5ce8-107">Si vous n’utilisez pas le code fourni, vous devez vous-même implémenter l’interface **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** .</span><span class="sxs-lookup"><span data-stu-id="c5ce8-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="c5ce8-108">Si vous utilisez un compte MSA, incluez les étendues suivantes dans votre demande de connexion : `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` et `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

> [!NOTE]
> <span data-ttu-id="c5ce8-109">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-109">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="c5ce8-110">Si vous utilisez un compte AAD, vous devrez demander les audiences suivantes : `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` et `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="c5ce8-110">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="c5ce8-111">Que vous utilisiez l’implémentation **MCDConnectedDevicesAccountManager** fournie ou non, si vous utilisez AAD, vous devrez spécifier les autorisations suivantes dans l’inscription de votre application sur le portail Azure (portal.azure.com > Azure Active Directory > Inscriptions des applications) :</span><span class="sxs-lookup"><span data-stu-id="c5ce8-111">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="c5ce8-112">Service de flux d’activités Microsoft</span><span class="sxs-lookup"><span data-stu-id="c5ce8-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="c5ce8-113">Remettez et modifiez les notifications utilisateur pour cette application</span><span class="sxs-lookup"><span data-stu-id="c5ce8-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="c5ce8-114">Lisez et écrivez l’activité de l’application dans le flux d’activités des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c5ce8-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="c5ce8-115">Services de notifications Windows</span><span class="sxs-lookup"><span data-stu-id="c5ce8-115">Windows Notification Service</span></span>
  * <span data-ttu-id="c5ce8-116">Connectez votre appareil au service de notification Windows</span><span class="sxs-lookup"><span data-stu-id="c5ce8-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="c5ce8-117">Service d’annuaire d’appareils Microsoft</span><span class="sxs-lookup"><span data-stu-id="c5ce8-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="c5ce8-118">Consultez votre liste d’appareils</span><span class="sxs-lookup"><span data-stu-id="c5ce8-118">See your list of devices</span></span>
  * <span data-ttu-id="c5ce8-119">Faites-vous ajouter à votre liste d’appareils et d’applications</span><span class="sxs-lookup"><span data-stu-id="c5ce8-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="c5ce8-120">Service de commande Microsoft</span><span class="sxs-lookup"><span data-stu-id="c5ce8-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="c5ce8-121">Communiquez avec les appareils utilisateur</span><span class="sxs-lookup"><span data-stu-id="c5ce8-121">Communicate with user devices</span></span>
  * <span data-ttu-id="c5ce8-122">Lisez les appareils utilisateur</span><span class="sxs-lookup"><span data-stu-id="c5ce8-122">Read user devices</span></span>
