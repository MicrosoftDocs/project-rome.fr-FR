---
title: MCDRemoteSystemDiscoveryTypeFilter
description: En savoir plus sur la classe MCDRemoteSystemDiscoveryTypeFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type de découverte.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760693"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="b43f4-105">type `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="b43f4-105">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="b43f4-106">Classe utilisée pour filtrer les systèmes distants en fonction du type de découverte.</span><span class="sxs-lookup"><span data-stu-id="b43f4-106">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="b43f4-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b43f4-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="b43f4-108">type</span><span class="sxs-lookup"><span data-stu-id="b43f4-108">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="b43f4-109">Type de découverte à filtrer.</span><span class="sxs-lookup"><span data-stu-id="b43f4-109">The discovery type to filter for.</span></span>

> <span data-ttu-id="b43f4-110">Remarque : sur Android, la plateforme appareils connectés peut uniquement utiliser Bluetooth sur les systèmes qui exécutent Android 8,0 (Oreo) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b43f4-110">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="b43f4-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b43f4-111">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="b43f4-112">filterWithType</span><span class="sxs-lookup"><span data-stu-id="b43f4-112">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="b43f4-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b43f4-113">Parameters</span></span> 
* <span data-ttu-id="b43f4-114">`discoveryType` Type de découverte à filtrer.</span><span class="sxs-lookup"><span data-stu-id="b43f4-114">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b43f4-115">Retours</span><span class="sxs-lookup"><span data-stu-id="b43f4-115">Returns</span></span>
<span data-ttu-id="b43f4-116">Nouvelle instance de cette classe avec la valeur de type donnée.</span><span class="sxs-lookup"><span data-stu-id="b43f4-116">A new instance of this class with the given type value.</span></span> <span data-ttu-id="b43f4-117">Les valeurs peuvent être AND’ed ensemble pour appliquer plusieurs filtres à la fois.</span><span class="sxs-lookup"><span data-stu-id="b43f4-117">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="b43f4-118">initWithType</span><span class="sxs-lookup"><span data-stu-id="b43f4-118">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="b43f4-119">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b43f4-119">Parameters</span></span> 
* <span data-ttu-id="b43f4-120">`discoveryType` Type de découverte à filtrer.</span><span class="sxs-lookup"><span data-stu-id="b43f4-120">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b43f4-121">Retours</span><span class="sxs-lookup"><span data-stu-id="b43f4-121">Returns</span></span>
<span data-ttu-id="b43f4-122">Nouvelle instance de cette classe avec la valeur de type donnée.</span><span class="sxs-lookup"><span data-stu-id="b43f4-122">A new instance of this class with the given type value.</span></span> <span data-ttu-id="b43f4-123">Les valeurs peuvent être AND’ed ensemble pour appliquer plusieurs filtres à la fois.</span><span class="sxs-lookup"><span data-stu-id="b43f4-123">Values can be AND'ed together to apply multiple filters at once.</span></span>