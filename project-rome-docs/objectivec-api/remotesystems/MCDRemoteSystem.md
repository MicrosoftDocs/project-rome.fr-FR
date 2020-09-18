---
title: MCDRemoteSystem
description: En savoir plus sur la classe MCDRemoteSystem et ses propriétés. Cette classe est utilisée pour représenter un système distant.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: e211de33117f48cc221152cf40645015693dcddc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760993"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="ac385-105">type `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="ac385-105">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="ac385-106">Classe pour représenter un système distant.</span><span class="sxs-lookup"><span data-stu-id="ac385-106">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="ac385-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ac385-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="ac385-108">kind</span><span class="sxs-lookup"><span data-stu-id="ac385-108">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="ac385-109">Type d’appareil de ce système distant.</span><span class="sxs-lookup"><span data-stu-id="ac385-109">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="ac385-110">systemId</span><span class="sxs-lookup"><span data-stu-id="ac385-110">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="ac385-111">Identificateur de ce système distant.</span><span class="sxs-lookup"><span data-stu-id="ac385-111">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="ac385-112">displayName</span><span class="sxs-lookup"><span data-stu-id="ac385-112">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="ac385-113">Nom du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="ac385-113">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="ac385-114">status</span><span class="sxs-lookup"><span data-stu-id="ac385-114">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="ac385-115">État de la disponibilité de ce système distant.</span><span class="sxs-lookup"><span data-stu-id="ac385-115">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="ac385-116">La présence WNS est utilisée pour la création de rapports de disponibilité pour les applications et les appareils Windows qui utilisent WNS comme type de notification.</span><span class="sxs-lookup"><span data-stu-id="ac385-116">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="ac385-117">Les RemoteSystem sont marqués comme étant « disponibles » lorsque l’appareil est considéré comme disponible (Windows) ou lorsque l’une des applications sous-jacentes signale leur présence comme étant disponible (iOS et Android).</span><span class="sxs-lookup"><span data-stu-id="ac385-117">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="ac385-118">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="ac385-118">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="ac385-119">Nom du fabricant du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="ac385-119">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="ac385-120">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="ac385-120">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="ac385-121">Nom de modèle du système distant donné.</span><span class="sxs-lookup"><span data-stu-id="ac385-121">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="ac385-122">applications</span><span class="sxs-lookup"><span data-stu-id="ac385-122">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="ac385-123">Tableau des applications sur ce système distant qui sont disponibles pour la connectivité.</span><span class="sxs-lookup"><span data-stu-id="ac385-123">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="ac385-124">plateforme</span><span class="sxs-lookup"><span data-stu-id="ac385-124">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="ac385-125">MCDRemoteSystemPlatform gérant l’activité du système distant.</span><span class="sxs-lookup"><span data-stu-id="ac385-125">The MCDRemoteSystemPlatform managing remote system activity.</span></span>