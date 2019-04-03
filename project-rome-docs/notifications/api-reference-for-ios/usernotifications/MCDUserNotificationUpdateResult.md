---
title: MCDUserNotificationUpdateResult
description: Cette classe décrit l’état d’une tentative de mise à jour d’une notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907971"
---
# <a name="class-mcdusernotificationupdateresult"></a>Classe `MCDUserNotificationUpdateResult`

```
@interface MCDUserNotificationUpdateResult : NSObject
```

Cette classe décrit l’état d’une tentative de mise à jour d’une notification.

## <a name="properties"></a>Properties

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

L’ID de la notification.

### <a name="succeeded"></a>a réussi
`@property(nonatomic, readonly) Succeeded succeeded;`

Indique si l’opération a réussi. 