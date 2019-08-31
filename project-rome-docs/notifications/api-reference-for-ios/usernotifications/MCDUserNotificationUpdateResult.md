---
title: MCDUserNotificationUpdateResult
description: Cette classe décrit l’état d’une tentative de mise à jour d’une notification.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801481"
---
# <a name="class-mcdusernotificationupdateresult"></a>type`MCDUserNotificationUpdateResult`

```
@interface MCDUserNotificationUpdateResult : NSObject
```

Cette classe décrit l’état d’une tentative de mise à jour d’une notification.

## <a name="properties"></a>Properties

### <a name="notificationid"></a>ID
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

ID de la notification.

### <a name="succeeded"></a>a réussi
`@property(nonatomic, readonly) Succeeded succeeded;`

Indique si l’opération a réussi. 