---
title: MCDRemoteSystemStatus
description: Contient des valeurs qui décrivent la disponibilité d’un système distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907581"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="61175-104">Enum `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="61175-104">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="61175-105">Contient des valeurs qui décrivent la disponibilité d’un système distant.</span><span class="sxs-lookup"><span data-stu-id="61175-105">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="61175-106">Sur les applications iOS, une valeur de **MCDRemoteSystemStatusUnknown** surviennent toujours ; d’autres valeurs sont disponibles uniquement sur les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="61175-106">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="61175-107">Champs</span><span class="sxs-lookup"><span data-stu-id="61175-107">Fields</span></span>

| <span data-ttu-id="61175-108">Nom</span><span class="sxs-lookup"><span data-stu-id="61175-108">Name</span></span>                              | <span data-ttu-id="61175-109">Value</span><span class="sxs-lookup"><span data-stu-id="61175-109">Value</span></span> | <span data-ttu-id="61175-110">Description</span><span class="sxs-lookup"><span data-stu-id="61175-110">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="61175-111">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="61175-111">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="61175-112">0</span><span class="sxs-lookup"><span data-stu-id="61175-112">0</span></span> | <span data-ttu-id="61175-113">Le système distant est signalé comme étant indisponible.</span><span class="sxs-lookup"><span data-stu-id="61175-113">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="61175-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="61175-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="61175-115">1</span><span class="sxs-lookup"><span data-stu-id="61175-115">1</span></span> | <span data-ttu-id="61175-116">L’état du système distant est déterminé (se produit pendant le processus de découverte).</span><span class="sxs-lookup"><span data-stu-id="61175-116">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="61175-117">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="61175-117">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="61175-118">2</span><span class="sxs-lookup"><span data-stu-id="61175-118">2</span></span> | <span data-ttu-id="61175-119">Le système distant est signalé comme étant disponible.</span><span class="sxs-lookup"><span data-stu-id="61175-119">The remote system is reported as available.</span></span> |
| <span data-ttu-id="61175-120">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="61175-120">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="61175-121">3</span><span class="sxs-lookup"><span data-stu-id="61175-121">3</span></span> | <span data-ttu-id="61175-122">L’état est inconnu.</span><span class="sxs-lookup"><span data-stu-id="61175-122">The status is unknown.</span></span> |
