---
title: MCDUserNotificationReadStateFilter
description: Contient des valeurs qui classent les notifications par État de lecture (pour la récupération filtrée des notifications).
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801341"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a>variables`MCDUserNotificationReadStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

Contient des valeurs qui classent les notifications par État de lecture (pour la récupération filtrée des notifications).

|Name | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationReadStateFilterAny | 0 | Inclure les notifications indépendamment de l’état de lecture.|
|   MCDUserNotificationReadStateFilterUnread | 1 | Incluez les notifications qui n’ont pas été lues.|
|   MCDUserNotificationReadStateFilterRead | 2 | Inclut les notifications qui ont été lues. |