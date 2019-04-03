---
title: MCDRemoteSystemPlatformFilter
description: Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908751"
---
# <a name="class-mcdremotesystemplatformfilter"></a><span data-ttu-id="8831e-104">Classe `MCDRemoteSystemPlatformFilter`</span><span class="sxs-lookup"><span data-stu-id="8831e-104">class `MCDRemoteSystemPlatformFilter`</span></span> 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

<span data-ttu-id="8831e-105">Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8831e-105">A class used to filter remote systems based on the OS platform they are running.</span></span>

## <a name="properties"></a><span data-ttu-id="8831e-106">Properties</span><span class="sxs-lookup"><span data-stu-id="8831e-106">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="8831e-107">Plateforme</span><span class="sxs-lookup"><span data-stu-id="8831e-107">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="8831e-108">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="8831e-108">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="8831e-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="8831e-109">Constructors</span></span>

### <a name="filterwithplatform"></a><span data-ttu-id="8831e-110">filterWithPlatform</span><span class="sxs-lookup"><span data-stu-id="8831e-110">filterWithPlatform</span></span>
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="8831e-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8831e-111">Parameters</span></span> 
* `platform` 

<span data-ttu-id="8831e-112">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="8831e-112">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="8831e-113">Returns</span><span class="sxs-lookup"><span data-stu-id="8831e-113">Returns</span></span>
<span data-ttu-id="8831e-114">Retourne un objet MCDRemoteSystemPlatformFilter filtré par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="8831e-114">Returns an MCDRemoteSystemPlatformFilter object filtered by platform.</span></span>

### <a name="initwithplatform"></a><span data-ttu-id="8831e-115">initWithPlatform</span><span class="sxs-lookup"><span data-stu-id="8831e-115">initWithPlatform</span></span>
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="8831e-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8831e-116">Parameters</span></span> 
* `platform` 

<span data-ttu-id="8831e-117">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="8831e-117">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="8831e-118">Returns</span><span class="sxs-lookup"><span data-stu-id="8831e-118">Returns</span></span>
<span data-ttu-id="8831e-119">Retourne un objet MCDRemoteSystemPlatformFilter initialisé avec un filtre par plateforme.</span><span class="sxs-lookup"><span data-stu-id="8831e-119">Returns an MCDRemoteSystemPlatformFilter object initialized with a filter by platform.</span></span>