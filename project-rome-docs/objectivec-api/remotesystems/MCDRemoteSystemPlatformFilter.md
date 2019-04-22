---
title: MCDRemoteSystemPlatformFilter
description: Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801217"
---
# <a name="class-mcdremotesystemplatformfilter"></a><span data-ttu-id="c7c56-104">Classe `MCDRemoteSystemPlatformFilter`</span><span class="sxs-lookup"><span data-stu-id="c7c56-104">class `MCDRemoteSystemPlatformFilter`</span></span> 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

<span data-ttu-id="c7c56-105">Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c7c56-105">A class used to filter remote systems based on the OS platform they are running.</span></span>

## <a name="properties"></a><span data-ttu-id="c7c56-106">Properties</span><span class="sxs-lookup"><span data-stu-id="c7c56-106">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="c7c56-107">Plateforme</span><span class="sxs-lookup"><span data-stu-id="c7c56-107">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="c7c56-108">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c56-108">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="c7c56-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="c7c56-109">Constructors</span></span>

### <a name="filterwithplatform"></a><span data-ttu-id="c7c56-110">filterWithPlatform</span><span class="sxs-lookup"><span data-stu-id="c7c56-110">filterWithPlatform</span></span>
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="c7c56-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7c56-111">Parameters</span></span> 
* `platform` 

<span data-ttu-id="c7c56-112">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c56-112">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c7c56-113">Returns</span><span class="sxs-lookup"><span data-stu-id="c7c56-113">Returns</span></span>
<span data-ttu-id="c7c56-114">Retourne un objet MCDRemoteSystemPlatformFilter filtré par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="c7c56-114">Returns an MCDRemoteSystemPlatformFilter object filtered by platform.</span></span>

### <a name="initwithplatform"></a><span data-ttu-id="c7c56-115">initWithPlatform</span><span class="sxs-lookup"><span data-stu-id="c7c56-115">initWithPlatform</span></span>
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="c7c56-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7c56-116">Parameters</span></span> 
* `platform` 

<span data-ttu-id="c7c56-117">Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="c7c56-117">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c7c56-118">Returns</span><span class="sxs-lookup"><span data-stu-id="c7c56-118">Returns</span></span>
<span data-ttu-id="c7c56-119">Retourne un objet MCDRemoteSystemPlatformFilter initialisé avec un filtre par plateforme.</span><span class="sxs-lookup"><span data-stu-id="c7c56-119">Returns an MCDRemoteSystemPlatformFilter object initialized with a filter by platform.</span></span>