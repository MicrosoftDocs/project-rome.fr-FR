---
title: MCDUserNotificationUserActionState
description: Contient des valeurs qui décrivent l’action de qu'un utilisateur a effectuées sur une notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800801"
---
# <a name="enum-mcdusernotificationuseractionstate"></a>Enum `MCDUserNotificationUserActionState`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

Contient des valeurs qui décrivent l’action de qu'un utilisateur a effectuées sur une notification.

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateNoInteraction |0| L’utilisateur n’a pas encore pris aucune action.|
|   MCDUserNotificationUserActionStateActivated|1|L’utilisateur a activé la notification.|
|   MCDUserNotificationUserActionStateDismissed|2| L’utilisateur a fermé la notification.|
|   MCDUserNotificationUserActionStateSnoozed|3| L’utilisateur a répété la notification.|
