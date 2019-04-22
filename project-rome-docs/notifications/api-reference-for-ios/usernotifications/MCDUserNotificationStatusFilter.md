---
title: MCDUserNotificationStatusFilter
description: Contient des valeurs qui indique un filtre d’état de lecture lors de la création d’un lecteur de notification. Ce paramètre détermine si l’application souhaite recevoir toutes les notifications, lire uniquement, ou uniquement ceux qui sont lus.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801491"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>Enum `MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

Contient des valeurs qui indique un filtre d’état de lecture lors de la création d’un lecteur de notification. Ce paramètre détermine si l’application souhaite recevoir toutes les notifications, lire uniquement, ou uniquement ceux qui sont lus. 

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| Inclure toutes les notifications, quel que soit la valeur d’état. |
|   MCDUserNotificationStatusFilterActive |1| Inclure les notifications qui sont actifs et persistante dans le magasin de notification de plateforme de périphériques connectés. |
|   MCDUserNotificationStatusFilterDeleted | 2| Inclure uniquement les notifications supprimées.|