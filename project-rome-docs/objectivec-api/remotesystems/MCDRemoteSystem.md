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
# <a name="class-mcdremotesystem"></a>type `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

Classe pour représenter un système distant.

## <a name="properties"></a>Propriétés

### <a name="kind"></a>kind
`@property(nonatomic, readonly, nonnull) NSString* kind;`

Type d’appareil de ce système distant.

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

Identificateur de ce système distant.

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

Nom du système distant donné.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

État de la disponibilité de ce système distant.

> [!NOTE]
La présence WNS est utilisée pour la création de rapports de disponibilité pour les applications et les appareils Windows qui utilisent WNS comme type de notification.  Les RemoteSystem sont marqués comme étant « disponibles » lorsque l’appareil est considéré comme disponible (Windows) ou lorsque l’une des applications sous-jacentes signale leur présence comme étant disponible (iOS et Android). 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

Nom du fabricant du système distant donné.

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

Nom de modèle du système distant donné.

### <a name="apps"></a>applications
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

Tableau des applications sur ce système distant qui sont disponibles pour la connectivité.

### <a name="platform"></a>plateforme
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

MCDRemoteSystemPlatform gérant l’activité du système distant.