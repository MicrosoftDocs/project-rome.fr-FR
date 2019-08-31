---
title: MCDUserNotificationUserActionStateFilter
description: Contient des valeurs qui classent les notifications par État d’action utilisateur (pour la récupération de notifications filtrées).
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800561"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>variables`MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

Contient des valeurs qui classent les notifications par État d’action utilisateur (pour la récupération de notifications filtrées).

|Name | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| Inclure les notifications indépendamment de l’état de l’action de l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| Inclut les notifications qui n’ont pas été traitées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterActivated|2| Inclut les notifications qui ont été activées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterDismissed|3| Inclut les notifications qui ont été ignorées par l’utilisateur.|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| Inclut les notifications qui ont été répétées par l’utilisateur.|