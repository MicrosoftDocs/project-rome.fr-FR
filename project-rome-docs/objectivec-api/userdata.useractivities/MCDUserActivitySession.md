---
title: MCDUserActivitySession
description: Cette classe effectue le suivi d’une activité de l’utilisateur ([MCDUserActivity](MCDUserActivity.md) instance) pendant que l’utilisateur est engagé dans cette activité.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2ae85e637bb059e811a60e5bde5f33ea767c8314
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800661"
---
# <a name="class-mcduseractivitysession"></a>Classe `MCDUserActivitySession`

```
@interface MCDUserActivitySession : NSObject
```

Cette classe effectue le suivi d’engagement pour une activité de l’utilisateur spécifié ([MCDUserActivity](MCDUserActivity.md) instance).

Un [MCDUserActivity](MCDUserActivity.md) est associé à une MCDUserActivitySession qui effectue le suivi de la durée pendant laquelle l’utilisateur est engagé dans cette activité. Par exemple, une activité telle que regarder un film peut apparaître activé et désactivé au cours de plusieurs jours. Lorsque l’utilisateur commence à la nouvelle activité de regarder un film, une MCDUserActivitySession doit être créée. Il doit être supprimé lorsque l’utilisateur bascule vers une autre activité. Lorsque l’utilisateur reprend, l’application doit créer un autre **MCDUserActivitySession** à partir de la version d’origine [MCDUserActivity](MCDUserActivity.md) pour effectuer le suivi de l’activité tant que l’utilisateur est chargé d’observer le film.


## <a name="properties"></a>Properties

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

Un ID unique pour le MCDUserActivity associé à cette MCDUserActivitySession.

## <a name="methods"></a>Méthodes

### <a name="stop"></a>stop
`- (void)stop;`

Arrête cette session de l’activité. Cela doit être appelée lorsque l’utilisateur n’est plus prend part à l’activité associée à cette session.