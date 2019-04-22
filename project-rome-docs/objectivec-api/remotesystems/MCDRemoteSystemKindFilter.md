---
title: MCDRemoteSystemKindFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801331"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="2f371-104">Classe `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="2f371-104">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="2f371-105">Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.</span><span class="sxs-lookup"><span data-stu-id="2f371-105">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="2f371-106">Properties</span><span class="sxs-lookup"><span data-stu-id="2f371-106">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="2f371-107">types</span><span class="sxs-lookup"><span data-stu-id="2f371-107">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="2f371-108">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="2f371-108">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="2f371-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="2f371-109">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="2f371-110">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="2f371-110">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="2f371-111">Une nouvelle instance de cette classe filtrée sur les types.</span><span class="sxs-lookup"><span data-stu-id="2f371-111">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2f371-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f371-112">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="2f371-113">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="2f371-113">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="2f371-114">Returns</span><span class="sxs-lookup"><span data-stu-id="2f371-114">Returns</span></span>
<span data-ttu-id="2f371-115">Retourne un objet MCDRemoteSystemKindFilter filtré avec des types.</span><span class="sxs-lookup"><span data-stu-id="2f371-115">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="2f371-116">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="2f371-116">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="2f371-117">Une nouvelle instance de cette classe filtrée sur les types.</span><span class="sxs-lookup"><span data-stu-id="2f371-117">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2f371-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f371-118">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="2f371-119">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="2f371-119">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="2f371-120">Returns</span><span class="sxs-lookup"><span data-stu-id="2f371-120">Returns</span></span>
<span data-ttu-id="2f371-121">Retourne un objet MCDRemoteSystemKindFilter initialisé avec les types.</span><span class="sxs-lookup"><span data-stu-id="2f371-121">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>