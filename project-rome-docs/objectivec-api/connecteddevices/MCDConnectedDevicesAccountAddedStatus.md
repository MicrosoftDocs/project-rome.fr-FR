---
title: MCDConnectedDevicesAccountAddedStatus
description: En savoir plus sur l’énumération MCDConnectedDevicesAccountAddedStatus. Cette énumération contient des valeurs qui décrivent l’état de l’opération d’ajout de compte.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761033"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="6fb0a-105">variables `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="6fb0a-105">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="6fb0a-106">Contient les valeurs qui décrivent l’état de l’opération d’ajout d’un compte.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-106">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="6fb0a-107">Champs</span><span class="sxs-lookup"><span data-stu-id="6fb0a-107">Fields</span></span>

| <span data-ttu-id="6fb0a-108">Nom</span><span class="sxs-lookup"><span data-stu-id="6fb0a-108">Name</span></span>                              |   <span data-ttu-id="6fb0a-109">Value</span><span class="sxs-lookup"><span data-stu-id="6fb0a-109">Value</span></span>     | <span data-ttu-id="6fb0a-110">Description</span><span class="sxs-lookup"><span data-stu-id="6fb0a-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="6fb0a-111">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="6fb0a-111">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="6fb0a-112">0</span><span class="sxs-lookup"><span data-stu-id="6fb0a-112">0</span></span> | <span data-ttu-id="6fb0a-113">Le compte a été correctement ajouté à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-113">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="6fb0a-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="6fb0a-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="6fb0a-115">1</span><span class="sxs-lookup"><span data-stu-id="6fb0a-115">1</span></span> | <span data-ttu-id="6fb0a-116">Échec de l’opération de compte, car Rome n’a détecté aucun accès réseau.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-116">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="6fb0a-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="6fb0a-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="6fb0a-118">2</span><span class="sxs-lookup"><span data-stu-id="6fb0a-118">2</span></span> | <span data-ttu-id="6fb0a-119">Échec de l’opération de compte, car Rome n’a pas pu contacter les services Web.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-119">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="6fb0a-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="6fb0a-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="6fb0a-121">3</span><span class="sxs-lookup"><span data-stu-id="6fb0a-121">3</span></span> | <span data-ttu-id="6fb0a-122">L’opération de compte a échoué, car l’application n’est pas abonnée à l’événement AccessTokenRequested.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-122">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="6fb0a-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="6fb0a-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="6fb0a-124">4</span><span class="sxs-lookup"><span data-stu-id="6fb0a-124">4</span></span> | <span data-ttu-id="6fb0a-125">L’opération de compte a échoué, car l’application n’a pas réussi à retourner un jeton lors de la demande.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-125">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="6fb0a-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="6fb0a-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="6fb0a-127">5</span><span class="sxs-lookup"><span data-stu-id="6fb0a-127">5</span></span> | <span data-ttu-id="6fb0a-128">L’opération de compte a échoué pour des raisons inconnues.</span><span class="sxs-lookup"><span data-stu-id="6fb0a-128">The account operation failed for unknown reasons.</span></span> |
