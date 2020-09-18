---
title: MCDRemoteSystemAuthorizationKindFilter
description: En savoir plus sur la classe MCDRemoteSystemAuthorizationKindFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type d’autorisation.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760703"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="c7c60-105">type `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="c7c60-105">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="c7c60-106">Classe utilisée pour filtrer les systèmes distants en fonction du type d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="c7c60-106">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="c7c60-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c7c60-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="c7c60-108">kind</span><span class="sxs-lookup"><span data-stu-id="c7c60-108">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="c7c60-109">Type d’autorisation à filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c60-109">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="c7c60-110">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="c7c60-110">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="c7c60-111">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="c7c60-111">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="c7c60-112">Nouvelle instance de cette classe filtrée sur MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="c7c60-112">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c7c60-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7c60-113">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="c7c60-114">Type d’autorisation à filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c60-114">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c7c60-115">Retours</span><span class="sxs-lookup"><span data-stu-id="c7c60-115">Returns</span></span>
<span data-ttu-id="c7c60-116">Retourne un objet MCDRemoteSystemAuthorizationKindFilter avec le filtre d’autorisation fourni.</span><span class="sxs-lookup"><span data-stu-id="c7c60-116">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="c7c60-117">initWithKind</span><span class="sxs-lookup"><span data-stu-id="c7c60-117">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="c7c60-118">Nouvelle instance de cette classe avec MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="c7c60-118">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c7c60-119">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7c60-119">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="c7c60-120">Type d’autorisation à filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c60-120">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c7c60-121">Retours</span><span class="sxs-lookup"><span data-stu-id="c7c60-121">Returns</span></span>
<span data-ttu-id="c7c60-122">Retourne un objet MCDRemoteSystemAuthorizationKindFilter initialisé avec authorizationKind.</span><span class="sxs-lookup"><span data-stu-id="c7c60-122">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>