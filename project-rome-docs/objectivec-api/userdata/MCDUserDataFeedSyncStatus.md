---
title: MCDUserDataSyncStatus
description: Contient des valeurs qui décrivent l’état d’un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de synchronisation avec le backend de la plateforme de périphériques connectés.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908621"
---
# <a name="enum-mcduserdatasyncstatus"></a>Enum `MCDUserDataSyncStatus`

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

Contient des valeurs qui décrivent l’état d’un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de synchronisation avec le backend de la plateforme de périphériques connectés.

|Nom | Value | Description |
|:-- |:-- |:-- |
|  MCDUserDataFeedSyncStatusQueued |0| Les données ne sont pas encore synchronisées. |
| MCDUserDataFeedSyncStatusSynchronized |1| Les données ont été synchronisées.|