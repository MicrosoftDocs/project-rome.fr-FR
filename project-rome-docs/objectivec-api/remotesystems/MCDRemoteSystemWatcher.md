---
title: MCDRemoteSystemWatcher
description: Une classe utilisée pour découvrir des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 88bb52465de165224c62270e0630dfb72f47b31f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908831"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="df15b-104">Classe `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="df15b-104">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="df15b-105">Une classe utilisée pour découvrir des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="df15b-105">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="df15b-106">Properties</span><span class="sxs-lookup"><span data-stu-id="df15b-106">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="df15b-107">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="df15b-107">remoteSystemAdded</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;`

<span data-ttu-id="df15b-108">Événement quand un nouveau système à distance est découvert.</span><span class="sxs-lookup"><span data-stu-id="df15b-108">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="df15b-109">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="df15b-109">remoteSystemUpdated</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;`

<span data-ttu-id="df15b-110">Événement quand un système distant qui a été détecté précédemment dans cette session de découverte passe de proximally connecté au cloud connectés ou l’inverse.</span><span class="sxs-lookup"><span data-stu-id="df15b-110">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="df15b-111">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="df15b-111">remoteSystemRemoved</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;`

<span data-ttu-id="df15b-112">Événement pour qu’un système distant est supprimé.</span><span class="sxs-lookup"><span data-stu-id="df15b-112">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="df15b-113">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="df15b-113">enumerationCompleted</span></span>
<span data-ttu-id="df15b-114">'''@property(non atomique, en lecture seule, non null) MCDEvent < MCDRemoteSystemWatcher *, MCDRemoteSystemEnumerationCompletedEventArgs*> \* enumerationCompleted ;</span><span class="sxs-lookup"><span data-stu-id="df15b-114">\`\`\`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher *, MCDRemoteSystemEnumerationCompletedEventArgs*>\* enumerationCompleted;</span></span>
```

Event for when the initial discovery of currently-discoverable devices has finished.  The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.

### errorOccurred
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;`

Event for when an error occurs during discovery. The discovery process will continue if possible. For example, if the error
occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery
may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).

## Constructors

### watcher
`+ (nullable instancetype)watcher;`

Creates and initializes a new instance of this class.

#### Returns 
Returns a new instance of this class.

### watcherWithFilters
`+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;`

Creates and initializes a new instance of this class with filters.

#### Parameters 
* `filters` 

An array of filters to use in the device discovery process.

#### Returns 
Returns an MCDRemoteSystemWatcher object with filters.

### initWithFilters
`- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;`

Creates and initializes a new instance of this class with filters.

#### Parameters 
* `filters` 

An array of filters to use in the device discovery process.

#### Returns 
Returns an MCDRemoteSystemWatcher object initialized with filters.

## Methods

### start
`- (void)start;`

Begins discovering remote systems.

### stop
`- (void)stop;` 

Stops the active discovery.