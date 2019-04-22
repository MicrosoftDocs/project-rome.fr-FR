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
# <a name="class-mcdremotesystem"></a>Classe `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

Une classe pour représenter un système distant.

## <a name="properties"></a>Properties

### <a name="kind"></a>Type
`@property(nonatomic, readonly, nonnull) NSString* kind;`

Le type d’appareil de ce système distant.

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

L’identificateur pour ce système distant.

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

Le nom du système distant donné.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

L’état de disponibilité de ce système distant.

> [!NOTE]
Présence WNS est utilisé pour les rapports de disponibilité pour les appareils Windows et les applications qui utilisent WNS en tant que type de notification.  RemoteSystem portera la mention « disponible » lorsque l’appareil est considéré comme disponible (Windows) ou lorsque l’une des applications sous-jacent signale sa présence comme étant disponibles (iOS et Android). 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

Le nom du fabricant du système distant donné.

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

Le nom du modèle du système distant donné.

### <a name="apps"></a>Microsoft
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

Tableau des applications sur ce système à distance qui sont disponibles pour la connectivité.

### <a name="platform"></a>Plateforme
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

MCDRemoteSystemPlatform de gestion de l’activité du système distant.