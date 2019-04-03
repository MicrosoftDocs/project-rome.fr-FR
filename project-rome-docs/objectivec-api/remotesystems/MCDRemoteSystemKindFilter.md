---
title: MCDRemoteSystemKindFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907261"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="b2092-104">Classe `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="b2092-104">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="b2092-105">Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.</span><span class="sxs-lookup"><span data-stu-id="b2092-105">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="b2092-106">Properties</span><span class="sxs-lookup"><span data-stu-id="b2092-106">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="b2092-107">types</span><span class="sxs-lookup"><span data-stu-id="b2092-107">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="b2092-108">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b2092-108">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="b2092-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b2092-109">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="b2092-110">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="b2092-110">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="b2092-111">Une nouvelle instance de cette classe filtrée sur les types.</span><span class="sxs-lookup"><span data-stu-id="b2092-111">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b2092-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2092-112">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="b2092-113">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b2092-113">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b2092-114">Returns</span><span class="sxs-lookup"><span data-stu-id="b2092-114">Returns</span></span>
<span data-ttu-id="b2092-115">Retourne un objet MCDRemoteSystemKindFilter filtré avec des types.</span><span class="sxs-lookup"><span data-stu-id="b2092-115">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="b2092-116">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="b2092-116">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="b2092-117">Une nouvelle instance de cette classe filtrée sur les types.</span><span class="sxs-lookup"><span data-stu-id="b2092-117">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b2092-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2092-118">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="b2092-119">Un tableau de chaînes indiquant les types d’appareil pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="b2092-119">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="b2092-120">Returns</span><span class="sxs-lookup"><span data-stu-id="b2092-120">Returns</span></span>
<span data-ttu-id="b2092-121">Retourne un objet MCDRemoteSystemKindFilter initialisé avec les types.</span><span class="sxs-lookup"><span data-stu-id="b2092-121">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>