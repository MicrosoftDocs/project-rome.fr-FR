---
title: MCDRemoteSystem
description: Une classe pour représenter un système distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5f0ab2108d4efa486b992bf7bc8c8847692623da
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801761"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="02231-104">Classe `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="02231-104">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="02231-105">Une classe pour représenter un système distant.</span><span class="sxs-lookup"><span data-stu-id="02231-105">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="02231-106">Properties</span><span class="sxs-lookup"><span data-stu-id="02231-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="02231-107">Type</span><span class="sxs-lookup"><span data-stu-id="02231-107">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="02231-108">Le type d’appareil de ce système distant.</span><span class="sxs-lookup"><span data-stu-id="02231-108">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="02231-109">systemId</span><span class="sxs-lookup"><span data-stu-id="02231-109">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="02231-110">L’identificateur pour ce système distant.</span><span class="sxs-lookup"><span data-stu-id="02231-110">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="02231-111">displayName</span><span class="sxs-lookup"><span data-stu-id="02231-111">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="02231-112">Le nom du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="02231-112">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="02231-113">status</span><span class="sxs-lookup"><span data-stu-id="02231-113">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="02231-114">L’état de disponibilité de ce système distant.</span><span class="sxs-lookup"><span data-stu-id="02231-114">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="02231-115">Présence WNS est utilisé pour les rapports de disponibilité pour les appareils Windows et les applications qui utilisent WNS en tant que type de notification.</span><span class="sxs-lookup"><span data-stu-id="02231-115">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="02231-116">RemoteSystem portera la mention « disponible » lorsque l’appareil est considéré comme disponible (Windows) ou lorsque l’une des applications sous-jacent signale sa présence comme étant disponibles (iOS et Android).</span><span class="sxs-lookup"><span data-stu-id="02231-116">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="02231-117">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="02231-117">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="02231-118">Le nom du fabricant du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="02231-118">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="02231-119">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="02231-119">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="02231-120">Le nom du modèle du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="02231-120">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="02231-121">Microsoft</span><span class="sxs-lookup"><span data-stu-id="02231-121">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="02231-122">Tableau des applications sur ce système à distance qui sont disponibles pour la connectivité.</span><span class="sxs-lookup"><span data-stu-id="02231-122">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="02231-123">Plateforme</span><span class="sxs-lookup"><span data-stu-id="02231-123">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="02231-124">MCDRemoteSystemPlatform de gestion de l’activité du système distant.</span><span class="sxs-lookup"><span data-stu-id="02231-124">The MCDRemoteSystemPlatform managing remote system activity.</span></span>