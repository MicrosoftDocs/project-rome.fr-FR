---
title: MCDUserNotificationUserActionStateFilter
description: Contient des valeurs qui classent les notifications par état d’action utilisateur (pour la récupération de la notification filtré).
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800561"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>Enum `MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

Contient des valeurs qui classent les notifications par état d’action utilisateur (pour la récupération de la notification filtré).

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| Inclure des notifications, quel que soit l’état d’action utilisateur.|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| Inclure des notifications qui n’ont pas été affrontées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterActivated|2| Inclure les notifications qui ont été activées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterDismissed|3| Inclure les notifications qui ont été ignorées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| Inclure les notifications qui ont été répétées par l’utilisateur.|