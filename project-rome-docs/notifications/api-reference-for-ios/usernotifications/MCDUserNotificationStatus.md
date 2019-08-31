---
title: MCDUserNotificationStatus
description: Contient des valeurs qui déterminent si la notification est supprimée ou non. Les notifications supprimées seront toujours dans le magasin de notifications et seront retournées par le lecteur avant le nettoyage de la plateforme. Un UserNotificationStatusFilter de filtre de lecteur correspondant peut être appliqué pour empêcher l’émission de ces notifications dans le lecteur de notifications.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800811"
---
# <a name="enum-mcdusernotificationstatus"></a>variables`MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

Contient des valeurs qui déterminent si la notification est supprimée ou non. Les notifications supprimées seront toujours dans le magasin de notifications et seront retournées par le lecteur avant le nettoyage de la plateforme. Un UserNotificationStatusFilter de filtre de lecteur correspondant peut être appliqué pour empêcher l’émission de ces notifications dans le lecteur de notifications. 

|Name | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| La notification est toujours active et persistante dans le magasin de plateformes des appareils connectés. |
|   MCDUserNotificationStatusDeleted | 1| La notification a été supprimée.|