---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Une classe utilisée pour filtrer en fonction de type de découverte de systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907521"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="c703a-104">Classe `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="c703a-104">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="c703a-105">Une classe utilisée pour filtrer en fonction de type de découverte de systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="c703a-105">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="c703a-106">Properties</span><span class="sxs-lookup"><span data-stu-id="c703a-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="c703a-107">Type</span><span class="sxs-lookup"><span data-stu-id="c703a-107">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="c703a-108">Le type de découverte pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c703a-108">The discovery type to filter for.</span></span>

> <span data-ttu-id="c703a-109">Remarque: Sur Android, la plateforme d’appareils connectés peuvent uniquement utiliser Bluetooth sur les systèmes exécutant Android 8.0 (Oreo) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c703a-109">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="c703a-110">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="c703a-110">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="c703a-111">filterWithType</span><span class="sxs-lookup"><span data-stu-id="c703a-111">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="c703a-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c703a-112">Parameters</span></span> 
* <span data-ttu-id="c703a-113">`discoveryType` Le type de découverte pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c703a-113">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c703a-114">Returns</span><span class="sxs-lookup"><span data-stu-id="c703a-114">Returns</span></span>
<span data-ttu-id="c703a-115">Une nouvelle instance de cette classe avec la valeur du type donné.</span><span class="sxs-lookup"><span data-stu-id="c703a-115">A new instance of this class with the given type value.</span></span> <span data-ttu-id="c703a-116">Valeurs peuvent être liées par and ensemble pour appliquer plusieurs filtres à la fois.</span><span class="sxs-lookup"><span data-stu-id="c703a-116">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="c703a-117">initWithType</span><span class="sxs-lookup"><span data-stu-id="c703a-117">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="c703a-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c703a-118">Parameters</span></span> 
* <span data-ttu-id="c703a-119">`discoveryType` Le type de découverte pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c703a-119">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c703a-120">Returns</span><span class="sxs-lookup"><span data-stu-id="c703a-120">Returns</span></span>
<span data-ttu-id="c703a-121">Une nouvelle instance de cette classe avec la valeur du type donné.</span><span class="sxs-lookup"><span data-stu-id="c703a-121">A new instance of this class with the given type value.</span></span> <span data-ttu-id="c703a-122">Valeurs peuvent être liées par and ensemble pour appliquer plusieurs filtres à la fois.</span><span class="sxs-lookup"><span data-stu-id="c703a-122">Values can be AND'ed together to apply multiple filters at once.</span></span>