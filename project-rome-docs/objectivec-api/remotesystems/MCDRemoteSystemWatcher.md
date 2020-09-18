---
title: MCDRemoteSystemWatcher
description: En savoir plus sur la classe MCDRemoteSystemWatcher et ses propriétés. Cette classe est utilisée pour détecter les systèmes distants.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: c000d5392fe6498c248b915ae4e26e49ad1d42db
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760643"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="fac82-105">type `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="fac82-105">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="fac82-106">Classe utilisée pour découvrir des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="fac82-106">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="fac82-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fac82-107">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="fac82-108">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="fac82-108">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="fac82-109">Événement lors de la détection d’un nouveau système distant.</span><span class="sxs-lookup"><span data-stu-id="fac82-109">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="fac82-110">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="fac82-110">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="fac82-111">Événement lorsqu’un système distant découvert précédemment dans cette session de découverte passe d’une connexion proximale à une connexion Cloud, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="fac82-111">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="fac82-112">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="fac82-112">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="fac82-113">Événement lors de la suppression d’un système distant.</span><span class="sxs-lookup"><span data-stu-id="fac82-113">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="fac82-114">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="fac82-114">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="fac82-115">Événement lorsque la détection initiale des appareils actuellement détectables est terminée.</span><span class="sxs-lookup"><span data-stu-id="fac82-115">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="fac82-116">Le processus de découverte continuera à s’exécuter et déclenchera des événements supplémentaires si l’ensemble des systèmes distants existants change.</span><span class="sxs-lookup"><span data-stu-id="fac82-116">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="fac82-117">errorOccurred</span><span class="sxs-lookup"><span data-stu-id="fac82-117">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="fac82-118">Événement quand une erreur se produit pendant la découverte.</span><span class="sxs-lookup"><span data-stu-id="fac82-118">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="fac82-119">Le processus de découverte se poursuivra dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="fac82-119">The discovery process will continue if possible.</span></span> <span data-ttu-id="fac82-120">Par exemple, si l’erreur se produit avec la valeur **MCDRemoteSystemWatcherError. MCDRemoteSystemWatcherErrorInternetNotAvailable**, la découverte proximale peut continuer car l’erreur s’applique uniquement à Cloud Discovery (voir **MCDRemoteSystemDiscoveryType**).</span><span class="sxs-lookup"><span data-stu-id="fac82-120">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="fac82-121">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="fac82-121">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="fac82-122">Observateur</span><span class="sxs-lookup"><span data-stu-id="fac82-122">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="fac82-123">Crée et Initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="fac82-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="fac82-124">Retours</span><span class="sxs-lookup"><span data-stu-id="fac82-124">Returns</span></span> 
<span data-ttu-id="fac82-125">Retourne une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="fac82-125">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="fac82-126">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="fac82-126">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="fac82-127">Crée et Initialise une nouvelle instance de cette classe avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="fac82-127">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="fac82-128">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fac82-128">Parameters</span></span> 
* `filters` 

<span data-ttu-id="fac82-129">Tableau de filtres à utiliser dans le processus de découverte d’appareils.</span><span class="sxs-lookup"><span data-stu-id="fac82-129">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="fac82-130">Retours</span><span class="sxs-lookup"><span data-stu-id="fac82-130">Returns</span></span> 
<span data-ttu-id="fac82-131">Retourne un objet MCDRemoteSystemWatcher avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="fac82-131">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="fac82-132">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="fac82-132">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="fac82-133">Crée et Initialise une nouvelle instance de cette classe avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="fac82-133">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="fac82-134">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fac82-134">Parameters</span></span> 
* `filters` 

<span data-ttu-id="fac82-135">Tableau de filtres à utiliser dans le processus de découverte d’appareils.</span><span class="sxs-lookup"><span data-stu-id="fac82-135">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="fac82-136">Retours</span><span class="sxs-lookup"><span data-stu-id="fac82-136">Returns</span></span> 
<span data-ttu-id="fac82-137">Retourne un objet MCDRemoteSystemWatcher initialisé avec des filtres.</span><span class="sxs-lookup"><span data-stu-id="fac82-137">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="fac82-138">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fac82-138">Methods</span></span>

### <a name="start"></a><span data-ttu-id="fac82-139">start</span><span class="sxs-lookup"><span data-stu-id="fac82-139">start</span></span>
`- (void)start;`

<span data-ttu-id="fac82-140">Commence à détecter les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="fac82-140">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="fac82-141">stop</span><span class="sxs-lookup"><span data-stu-id="fac82-141">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="fac82-142">Arrête la découverte active.</span><span class="sxs-lookup"><span data-stu-id="fac82-142">Stops the active discovery.</span></span>
