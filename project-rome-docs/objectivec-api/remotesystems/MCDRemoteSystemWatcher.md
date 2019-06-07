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
# <a name="class-mcdremotesystemwatcher"></a>Classe `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

Une classe utilisée pour découvrir des systèmes distants. 

## <a name="properties"></a>Properties

### <a name="remotesystemadded"></a>remoteSystemAdded
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

Événement quand un nouveau système à distance est découvert.

### <a name="remotesystemupdated"></a>remoteSystemUpdated
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

Événement quand un système distant qui a été détecté précédemment dans cette session de découverte passe de proximally connecté au cloud connectés ou l’inverse. 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

Événement pour qu’un système distant est supprimé. 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

Événement au terme de la découverte initiale des périphériques actuellement détectable.  Le processus de découverte continuera à exécuter et va déclencher des événements supplémentaires si l’ensemble des systèmes à distance existants est modifié.

### <a name="erroroccurred"></a>errorOccurred
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

Événement pour déterminer quand une erreur survient pendant la découverte. Le processus de découverte continue si possible. Par exemple, si l’erreur se produit avec la valeur **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, découverte PROXIMALE peut continuer, car l’erreur s’applique uniquement à la découverte du cloud (voir  **MCDRemoteSystemDiscoveryType**).

## <a name="constructors"></a>Constructeurs

### <a name="watcher"></a>Observateur
```
+ (nullable instancetype)watcher;
```

Crée et initialise une nouvelle instance de cette classe.

#### <a name="returns"></a>Returns 
Retourne une nouvelle instance de cette classe.

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crée et initialise une nouvelle instance de cette classe avec des filtres.

#### <a name="parameters"></a>Paramètres 
* `filters` 

Tableau des filtres à utiliser dans le processus de découverte de périphérique.

#### <a name="returns"></a>Returns 
Retourne un objet MCDRemoteSystemWatcher avec des filtres.

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crée et initialise une nouvelle instance de cette classe avec des filtres.

#### <a name="parameters"></a>Paramètres 
* `filters` 

Tableau des filtres à utiliser dans le processus de découverte de périphérique.

#### <a name="returns"></a>Returns 
Retourne un objet MCDRemoteSystemWatcher initialisé avec des filtres.

## <a name="methods"></a>Méthodes

### <a name="start"></a>start
`- (void)start;`

Commence à identifier les systèmes distants.

### <a name="stop"></a>stop
`- (void)stop;` 

Arrête la recherche active.
