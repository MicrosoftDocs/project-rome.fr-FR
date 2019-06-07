---
title: MCDRemoteSystemWatcher
description: Une classe utilisée pour découvrir des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 8fcb0c01fd8f8c3ef1eb2d959dc9ef8af758562d
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755741"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="a87cc-104">Classe `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="a87cc-104">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="a87cc-105">Une classe utilisée pour découvrir des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="a87cc-105">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="a87cc-106">Properties</span><span class="sxs-lookup"><span data-stu-id="a87cc-106">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="a87cc-107">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="a87cc-107">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="a87cc-108">Événement quand un nouveau système à distance est découvert.</span><span class="sxs-lookup"><span data-stu-id="a87cc-108">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="a87cc-109">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="a87cc-109">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="a87cc-110">Événement quand un système distant qui a été détecté précédemment dans cette session de découverte passe de proximally connecté au cloud connectés ou l’inverse.</span><span class="sxs-lookup"><span data-stu-id="a87cc-110">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="a87cc-111">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="a87cc-111">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="a87cc-112">Événement pour qu’un système distant est supprimé.</span><span class="sxs-lookup"><span data-stu-id="a87cc-112">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="a87cc-113">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="a87cc-113">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="a87cc-114">Événement au terme de la découverte initiale des périphériques actuellement détectable.</span><span class="sxs-lookup"><span data-stu-id="a87cc-114">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="a87cc-115">Le processus de découverte continuera à exécuter et va déclencher des événements supplémentaires si l’ensemble des systèmes à distance existants est modifié.</span><span class="sxs-lookup"><span data-stu-id="a87cc-115">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="a87cc-116">errorOccurred</span><span class="sxs-lookup"><span data-stu-id="a87cc-116">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="a87cc-117">Événement pour déterminer quand une erreur survient pendant la découverte.</span><span class="sxs-lookup"><span data-stu-id="a87cc-117">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="a87cc-118">Le processus de découverte continue si possible.</span><span class="sxs-lookup"><span data-stu-id="a87cc-118">The discovery process will continue if possible.</span></span> <span data-ttu-id="a87cc-119">Par exemple, si l’erreur se produit avec la valeur **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, découverte PROXIMALE peut continuer, car l’erreur s’applique uniquement à la découverte du cloud (voir  **MCDRemoteSystemDiscoveryType**).</span><span class="sxs-lookup"><span data-stu-id="a87cc-119">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="a87cc-120">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a87cc-120">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="a87cc-121">Observateur</span><span class="sxs-lookup"><span data-stu-id="a87cc-121">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="a87cc-122">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a87cc-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="a87cc-123">Returns</span><span class="sxs-lookup"><span data-stu-id="a87cc-123">Returns</span></span> 
<span data-ttu-id="a87cc-124">Retourne une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a87cc-124">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="a87cc-125">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="a87cc-125">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="a87cc-126">Crée et initialise une nouvelle instance de cette classe avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="a87cc-126">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a87cc-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a87cc-127">Parameters</span></span> 
* `filters` 

<span data-ttu-id="a87cc-128">Tableau des filtres à utiliser dans le processus de découverte de périphérique.</span><span class="sxs-lookup"><span data-stu-id="a87cc-128">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="a87cc-129">Returns</span><span class="sxs-lookup"><span data-stu-id="a87cc-129">Returns</span></span> 
<span data-ttu-id="a87cc-130">Retourne un objet MCDRemoteSystemWatcher avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="a87cc-130">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="a87cc-131">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="a87cc-131">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="a87cc-132">Crée et initialise une nouvelle instance de cette classe avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="a87cc-132">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a87cc-133">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a87cc-133">Parameters</span></span> 
* `filters` 

<span data-ttu-id="a87cc-134">Tableau des filtres à utiliser dans le processus de découverte de périphérique.</span><span class="sxs-lookup"><span data-stu-id="a87cc-134">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="a87cc-135">Returns</span><span class="sxs-lookup"><span data-stu-id="a87cc-135">Returns</span></span> 
<span data-ttu-id="a87cc-136">Retourne un objet MCDRemoteSystemWatcher initialisé avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="a87cc-136">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="a87cc-137">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a87cc-137">Methods</span></span>

### <a name="start"></a><span data-ttu-id="a87cc-138">start</span><span class="sxs-lookup"><span data-stu-id="a87cc-138">start</span></span>
`- (void)start;`

<span data-ttu-id="a87cc-139">Commence à identifier les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="a87cc-139">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="a87cc-140">stop</span><span class="sxs-lookup"><span data-stu-id="a87cc-140">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="a87cc-141">Arrête la recherche active.</span><span class="sxs-lookup"><span data-stu-id="a87cc-141">Stops the active discovery.</span></span>
