---
title: MCDConnectedDevicesNotificationType
description: Contient des valeurs qui décrivent le type (service) d’une notification.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801691"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>Enum `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
Contient des valeurs qui décrivent le type (service) d’une notification.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType est inconnu. |
| MCDNotificationTypeWNS | 1 | Services de notifications Push Windows. |
| MCDNotificationTypeGCM | 2 | Google Cloud Messaging. |
| MCDNotificationTypeFCM | 3 | Firebase Cloud Messaging.|
| MCDNotificationTypeAPN | 4 | Apple Push Notification Service. |
| MCDNotificationTypePolling | 5 | Aucun service de notification cloud ; interroger à la place pour les réponses entrantes. |
