---
title: MCDRemoteSystemStatusTypeFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’état de disponibilité.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907121"
---
# <a name="class-mcdremotesystemstatustypefilter"></a><span data-ttu-id="a140e-104">Classe `MCDRemoteSystemStatusTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="a140e-104">class `MCDRemoteSystemStatusTypeFilter`</span></span>

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

<span data-ttu-id="a140e-105">Une classe utilisée pour filtrer les systèmes distants selon le type d’état de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="a140e-105">A class used to filter remote systems based on availability status type.</span></span>

## <a name="properties"></a><span data-ttu-id="a140e-106">Properties</span><span class="sxs-lookup"><span data-stu-id="a140e-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="a140e-107">Type</span><span class="sxs-lookup"><span data-stu-id="a140e-107">type</span></span>
<span data-ttu-id="a140e-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` Le type d’état du système distant de cette instance de filtre.</span><span class="sxs-lookup"><span data-stu-id="a140e-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` The remote system status type of this filter instance.</span></span>

## <a name="constructors"></a><span data-ttu-id="a140e-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a140e-109">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="a140e-110">filterWithType</span><span class="sxs-lookup"><span data-stu-id="a140e-110">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="a140e-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a140e-111">Parameters</span></span> 
* <span data-ttu-id="a140e-112">`statusType` Une valeur indiquant le type d’état de disponibilité pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="a140e-112">`statusType` A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="a140e-113">Returns</span><span class="sxs-lookup"><span data-stu-id="a140e-113">Returns</span></span>
<span data-ttu-id="a140e-114">Retourne un objet MCDRemoteSystemStatusTypeFilter filtré par type.</span><span class="sxs-lookup"><span data-stu-id="a140e-114">Returns an MCDRemoteSystemStatusTypeFilter object filtered by type.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="a140e-115">initWithType</span><span class="sxs-lookup"><span data-stu-id="a140e-115">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="a140e-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a140e-116">Parameters</span></span> 
* `statusType` 

<span data-ttu-id="a140e-117">Une valeur indiquant le type d’état de disponibilité pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="a140e-117">A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="a140e-118">Returns</span><span class="sxs-lookup"><span data-stu-id="a140e-118">Returns</span></span>
<span data-ttu-id="a140e-119">Retourne un objet MCDRemoteSystemStatusTypeFilter initialisé avec le type.</span><span class="sxs-lookup"><span data-stu-id="a140e-119">Returns an MCDRemoteSystemStatusTypeFilter object initialized with the type.</span></span>