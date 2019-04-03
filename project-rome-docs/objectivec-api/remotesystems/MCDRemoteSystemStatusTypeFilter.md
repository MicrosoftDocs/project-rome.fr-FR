---
title: MCDRemoteSystemStatusTypeFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’état de disponibilité.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907121"
---
# <a name="class-mcdremotesystemstatustypefilter"></a>Classe `MCDRemoteSystemStatusTypeFilter`

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

Une classe utilisée pour filtrer les systèmes distants selon le type d’état de disponibilité.

## <a name="properties"></a>Properties

### <a name="type"></a>Type
`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` Le type d’état du système distant de cette instance de filtre.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>Paramètres 
* `statusType` Une valeur indiquant le type d’état de disponibilité pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemStatusTypeFilter filtré par type.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>Paramètres 
* `statusType` 

Une valeur indiquant le type d’état de disponibilité pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemStatusTypeFilter initialisé avec le type.