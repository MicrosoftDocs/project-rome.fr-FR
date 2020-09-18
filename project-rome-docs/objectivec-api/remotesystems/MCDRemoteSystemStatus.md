---
title: MCDRemoteSystemStatus
description: En savoir plus sur l’énumération MCDRemoteSystemStatus. Cette énumération contient des valeurs qui décrivent la disponibilité d’un système distant.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760653"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="3e5d1-105">variables `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="3e5d1-105">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="3e5d1-106">Contient des valeurs qui décrivent la disponibilité d’un système distant.</span><span class="sxs-lookup"><span data-stu-id="3e5d1-106">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="3e5d1-107">Sur les applications iOS, la valeur **MCDRemoteSystemStatusUnknown** est toujours rencontrée. les autres valeurs sont disponibles uniquement sur les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="3e5d1-107">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="3e5d1-108">Champs</span><span class="sxs-lookup"><span data-stu-id="3e5d1-108">Fields</span></span>

| <span data-ttu-id="3e5d1-109">Nom</span><span class="sxs-lookup"><span data-stu-id="3e5d1-109">Name</span></span>                              | <span data-ttu-id="3e5d1-110">Value</span><span class="sxs-lookup"><span data-stu-id="3e5d1-110">Value</span></span> | <span data-ttu-id="3e5d1-111">Description</span><span class="sxs-lookup"><span data-stu-id="3e5d1-111">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="3e5d1-112">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="3e5d1-112">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="3e5d1-113">0</span><span class="sxs-lookup"><span data-stu-id="3e5d1-113">0</span></span> | <span data-ttu-id="3e5d1-114">Le système distant est signalé comme étant non disponible.</span><span class="sxs-lookup"><span data-stu-id="3e5d1-114">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="3e5d1-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="3e5d1-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="3e5d1-116">1</span><span class="sxs-lookup"><span data-stu-id="3e5d1-116">1</span></span> | <span data-ttu-id="3e5d1-117">L’état du système distant est en cours de détermination (se produit pendant le processus de découverte).</span><span class="sxs-lookup"><span data-stu-id="3e5d1-117">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="3e5d1-118">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="3e5d1-118">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="3e5d1-119">2</span><span class="sxs-lookup"><span data-stu-id="3e5d1-119">2</span></span> | <span data-ttu-id="3e5d1-120">Le système distant est signalé comme étant disponible.</span><span class="sxs-lookup"><span data-stu-id="3e5d1-120">The remote system is reported as available.</span></span> |
| <span data-ttu-id="3e5d1-121">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="3e5d1-121">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="3e5d1-122">3</span><span class="sxs-lookup"><span data-stu-id="3e5d1-122">3</span></span> | <span data-ttu-id="3e5d1-123">L’État est inconnu.</span><span class="sxs-lookup"><span data-stu-id="3e5d1-123">The status is unknown.</span></span> |
