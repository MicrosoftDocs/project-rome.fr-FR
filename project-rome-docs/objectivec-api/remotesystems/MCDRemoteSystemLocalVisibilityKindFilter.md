---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: Une classe utilisée pour définir la préférence de visibilité application (appelant) local lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909571"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a><span data-ttu-id="22252-104">Classe `MCDRemoteSystemLocalVisibilityKindFilter`</span><span class="sxs-lookup"><span data-stu-id="22252-104">class `MCDRemoteSystemLocalVisibilityKindFilter`</span></span> 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="22252-105">Une classe utilisée pour définir la préférence de visibilité application (appelant) local lors de la découverte des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="22252-105">A class used to set the local (calling) application visibility preference when discovering remote systems.</span></span>

## <a name="properties"></a><span data-ttu-id="22252-106">Properties</span><span class="sxs-lookup"><span data-stu-id="22252-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="22252-107">Type</span><span class="sxs-lookup"><span data-stu-id="22252-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

<span data-ttu-id="22252-108">Le paramètre de visibilité à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="22252-108">The visibility setting to filter with.</span></span>

## <a name="constructors"></a><span data-ttu-id="22252-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="22252-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="22252-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="22252-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="22252-111">Crée et initialise une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="22252-111">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="22252-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22252-112">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="22252-113">Une valeur MCDRemoteSystemLocalVisibilityKind indiquant le paramètre de visibilité de l’application locale à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="22252-113">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="22252-114">Returns</span><span class="sxs-lookup"><span data-stu-id="22252-114">Returns</span></span>
<span data-ttu-id="22252-115">Retourne un objet MCDRemoteSystemLocalVisibilityKind filtré par type.</span><span class="sxs-lookup"><span data-stu-id="22252-115">Returns an MCDRemoteSystemLocalVisibilityKind object filtered by kind.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="22252-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="22252-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="22252-117">Crée et initialise une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="22252-117">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="22252-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22252-118">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="22252-119">Une valeur MCDRemoteSystemLocalVisibilityKind indiquant le paramètre de visibilité de l’application locale à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="22252-119">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="22252-120">Returns</span><span class="sxs-lookup"><span data-stu-id="22252-120">Returns</span></span>
<span data-ttu-id="22252-121">Retourne un objet MCDRemoteSystemLocalVisibilityKind initialisé avec le type.</span><span class="sxs-lookup"><span data-stu-id="22252-121">Returns an MCDRemoteSystemLocalVisibilityKind object initialized with kind.</span></span>