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
# <a name="class-mcdremotesystemwatcher"></a>type `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

Classe utilisée pour découvrir des systèmes distants. 

## <a name="properties"></a>Propriétés

### <a name="remotesystemadded"></a>remoteSystemAdded
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

Événement lors de la détection d’un nouveau système distant.

### <a name="remotesystemupdated"></a>remoteSystemUpdated
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

Événement lorsqu’un système distant découvert précédemment dans cette session de découverte passe d’une connexion proximale à une connexion Cloud, ou vice versa. 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

Événement lors de la suppression d’un système distant. 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

Événement lorsque la détection initiale des appareils actuellement détectables est terminée.  Le processus de découverte continuera à s’exécuter et déclenchera des événements supplémentaires si l’ensemble des systèmes distants existants change.

### <a name="erroroccurred"></a>errorOccurred
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

Événement quand une erreur se produit pendant la découverte. Le processus de découverte se poursuivra dans la mesure du possible. Par exemple, si l’erreur se produit avec la valeur **MCDRemoteSystemWatcherError. MCDRemoteSystemWatcherErrorInternetNotAvailable**, la découverte proximale peut continuer car l’erreur s’applique uniquement à Cloud Discovery (voir **MCDRemoteSystemDiscoveryType**).

## <a name="constructors"></a>Constructeurs

### <a name="watcher"></a>Observateur
```
+ (nullable instancetype)watcher;
```

Crée et Initialise une nouvelle instance de cette classe.

#### <a name="returns"></a>Retours 
Retourne une nouvelle instance de cette classe.

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crée et Initialise une nouvelle instance de cette classe avec des filtres.

#### <a name="parameters"></a>Paramètres 
* `filters` 

Tableau de filtres à utiliser dans le processus de découverte d’appareils.

#### <a name="returns"></a>Retours 
Retourne un objet MCDRemoteSystemWatcher avec des filtres.

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crée et Initialise une nouvelle instance de cette classe avec des filtres.

#### <a name="parameters"></a>Paramètres 
* `filters` 

Tableau de filtres à utiliser dans le processus de découverte d’appareils.

#### <a name="returns"></a>Retours 
Retourne un objet MCDRemoteSystemWatcher initialisé avec des filtres.

## <a name="methods"></a>Méthodes

### <a name="start"></a>start
`- (void)start;`

Commence à détecter les systèmes distants.

### <a name="stop"></a>stop
`- (void)stop;` 

Arrête la découverte active.
