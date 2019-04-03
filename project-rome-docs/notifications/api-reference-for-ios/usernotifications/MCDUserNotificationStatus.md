---
title: MCDUserNotificationStatus
description: Contient des valeurs qui détermine si la notification est supprimée ou non. Notifications supprimées seront toujours dans le magasin de notification et renvoyées par le lecteur avant le nettoyage de la plateforme se produit. Un filtre de lecteur correspondante UserNotificationStatusFilter peut être appliqué pour empêcher ces notifications de s’afficher dans le lecteur de notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907241"
---
# <a name="enum-mcdusernotificationstatus"></a>Enum `MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

Contient des valeurs qui détermine si la notification est supprimée ou non. Notifications supprimées seront toujours dans le magasin de notification et renvoyées par le lecteur avant le nettoyage de la plateforme se produit. Un filtre de lecteur correspondante UserNotificationStatusFilter peut être appliqué pour empêcher ces notifications de s’afficher dans le lecteur de notification. 

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| La notification est toujours actif et persistante à l’intérieur du magasin de la plateforme de périphériques connectés. |
|   MCDUserNotificationStatusDeleted | 1| La notification a été supprimée.|