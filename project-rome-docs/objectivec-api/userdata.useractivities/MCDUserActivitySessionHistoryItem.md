---
title: MCDUserActivitySessionHistoryItem
description: Cette classe fournit l’heure de début et de fin un utilisateur a été engagée dans une activité particulière.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907401"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a>Classe `MCDUserActivitySessionHistoryItem`

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

Cette classe fournit l’heure de début et de fin un utilisateur a été engagée dans une activité particulière.


## <a name="properties"></a>Properties

### <a name="useractivity"></a>UserActivity
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

L’activité des utilisateurs dont l’historique de cette instance de classe représente.

### <a name="starttime"></a>startTime
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

Heure de l’utilisateur démarrage attrayante dans l’activité associée.

### <a name="endtime"></a>endTime
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

L’heure lorsque l’utilisateur a arrêté impliqués dans l’activité associée.

### <a name="remotesystemid"></a>remoteSystemId
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

La chaîne indiquant l’id du système distant de l’appareil de l’utilisateur effectuant cette activité.