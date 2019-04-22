---
title: MCDUserNotificationReadStateFilter
description: Contient des valeurs qui classent les notifications par état de lecture (pour la récupération de la notification filtré).
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801341"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a>Enum `MCDUserNotificationReadStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

Contient des valeurs qui classent les notifications par état de lecture (pour la récupération de la notification filtré).

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationReadStateFilterAny | 0 | Inclure des notifications, quel que soit l’état de lecture.|
|   MCDUserNotificationReadStateFilterUnread | 1 | Inclure les notifications ne sont pas lus.|
|   MCDUserNotificationReadStateFilterRead | 2 | Inclure les notifications qui ont été lus. |