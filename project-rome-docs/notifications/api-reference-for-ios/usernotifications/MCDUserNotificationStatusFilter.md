---
title: MCDUserNotificationStatusFilter
description: Contient des valeurs qui indiquent un filtre d’état de lecture lors de la création d’un lecteur de notifications. Cela détermine si l’application souhaite recevoir toutes les notifications, lire uniquement celles-ci ou uniquement celles qui n’ont pas été lues.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801491"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>variables`MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

Contient des valeurs qui indiquent un filtre d’état de lecture lors de la création d’un lecteur de notifications. Cela détermine si l’application souhaite recevoir toutes les notifications, lire uniquement celles-ci ou uniquement celles qui n’ont pas été lues. 

|Nom | Value | Description |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| Inclut toutes les notifications indépendamment de la valeur d’État. |
|   MCDUserNotificationStatusFilterActive |1| Inclure les notifications actives et conservées dans le magasin de notifications de la plateforme des appareils connectés. |
|   MCDUserNotificationStatusFilterDeleted | 2| Inclut uniquement les notifications supprimées.|