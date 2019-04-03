---
title: MCDUserNotificationUserActionState
description: Contient des valeurs qui décrivent l’action de qu'un utilisateur a effectuées sur une notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907781"
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
