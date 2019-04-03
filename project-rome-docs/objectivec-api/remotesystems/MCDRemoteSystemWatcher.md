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
# <a name="class-mcdremotesystemwatcher"></a>Classe `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

Une classe utilisée pour découvrir des systèmes distants. 

## <a name="properties"></a>Properties

### <a name="remotesystemadded"></a>remoteSystemAdded
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;`

Événement quand un nouveau système à distance est découvert.

### <a name="remotesystemupdated"></a>remoteSystemUpdated
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;`

Événement quand un système distant qui a été détecté précédemment dans cette session de découverte passe de proximally connecté au cloud connectés ou l’inverse. 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;`

Événement pour qu’un système distant est supprimé. 

### <a name="enumerationcompleted"></a>enumerationCompleted
'''@property(non atomique, en lecture seule, non null) MCDEvent < MCDRemoteSystemWatcher *, MCDRemoteSystemEnumerationCompletedEventArgs*> * enumerationCompleted ;
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