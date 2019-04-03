---
title: MCDRemoteSystemAuthorizationKindFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’autorisation.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907641"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="b5f82-104">Classe `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="b5f82-104">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="b5f82-105">Une classe utilisée pour filtrer les systèmes distants selon le type d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="b5f82-105">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="b5f82-106">Properties</span><span class="sxs-lookup"><span data-stu-id="b5f82-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="b5f82-107">Type</span><span class="sxs-lookup"><span data-stu-id="b5f82-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="b5f82-108">Le type d’autorisation pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b5f82-108">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="b5f82-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b5f82-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="b5f82-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="b5f82-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="b5f82-111">Une nouvelle instance de cette classe filtrée sur MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="b5f82-111">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b5f82-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5f82-112">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="b5f82-113">Le type d’autorisation pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b5f82-113">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b5f82-114">Returns</span><span class="sxs-lookup"><span data-stu-id="b5f82-114">Returns</span></span>
<span data-ttu-id="b5f82-115">Retourne un objet MCDRemoteSystemAuthorizationKindFilter avec le filtre d’autorisation fourni.</span><span class="sxs-lookup"><span data-stu-id="b5f82-115">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="b5f82-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="b5f82-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="b5f82-117">Une nouvelle instance de cette classe avec MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="b5f82-117">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b5f82-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5f82-118">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="b5f82-119">Le type d’autorisation pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b5f82-119">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b5f82-120">Returns</span><span class="sxs-lookup"><span data-stu-id="b5f82-120">Returns</span></span>
<span data-ttu-id="b5f82-121">Retourne un objet MCDRemoteSystemAuthorizationKindFilter initialisé avec l’authorizationKind.</span><span class="sxs-lookup"><span data-stu-id="b5f82-121">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>