---
title: MCDRemoteSystemKindFilter
description: En savoir plus sur la classe MCDRemoteSystemKindFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type d’appareil.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760673"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="1969c-105">type `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="1969c-105">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="1969c-106">Classe utilisée pour filtrer les systèmes distants en fonction du type d’appareil.</span><span class="sxs-lookup"><span data-stu-id="1969c-106">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="1969c-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1969c-107">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="1969c-108">catégories</span><span class="sxs-lookup"><span data-stu-id="1969c-108">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="1969c-109">Tableau de chaînes indiquant les genres de périphériques à filtrer.</span><span class="sxs-lookup"><span data-stu-id="1969c-109">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="1969c-110">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="1969c-110">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="1969c-111">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="1969c-111">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="1969c-112">Nouvelle instance de cette classe filtrée sur des genres.</span><span class="sxs-lookup"><span data-stu-id="1969c-112">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1969c-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1969c-113">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="1969c-114">Tableau de chaînes indiquant les genres de périphériques à filtrer.</span><span class="sxs-lookup"><span data-stu-id="1969c-114">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="1969c-115">Retours</span><span class="sxs-lookup"><span data-stu-id="1969c-115">Returns</span></span>
<span data-ttu-id="1969c-116">Retourne un objet MCDRemoteSystemKindFilter filtré avec des genres.</span><span class="sxs-lookup"><span data-stu-id="1969c-116">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="1969c-117">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="1969c-117">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="1969c-118">Nouvelle instance de cette classe filtrée sur des genres.</span><span class="sxs-lookup"><span data-stu-id="1969c-118">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1969c-119">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1969c-119">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="1969c-120">Tableau de chaînes indiquant les genres de périphériques à filtrer.</span><span class="sxs-lookup"><span data-stu-id="1969c-120">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="1969c-121">Retours</span><span class="sxs-lookup"><span data-stu-id="1969c-121">Returns</span></span>
<span data-ttu-id="1969c-122">Retourne un objet MCDRemoteSystemKindFilter initialisé avec des genres.</span><span class="sxs-lookup"><span data-stu-id="1969c-122">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>