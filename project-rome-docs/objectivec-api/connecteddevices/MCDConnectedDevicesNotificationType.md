---
title: MCDConnectedDevicesNotificationType
description: En savoir plus sur l’énumération MCDConnectedDevicesNotificationType. Cette énumération contient des valeurs qui décrivent le type (service) d’une notification.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 5daf6db553df72a14a2cf201b4e974083eb7cf80
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761093"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>variables `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
Contient des valeurs qui décrivent le type (service) d’une notification.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType est inconnu. |
| MCDNotificationTypeWNS | 1 | Notification Services Push Windows. |
| MCDNotificationTypeGCM | 2 | Google Cloud Messaging. |
| MCDNotificationTypeFCM | 3 | Firebase Cloud Messaging.|
| MCDNotificationTypeAPN | 4 | Apple Push Notification Service. |
| MCDNotificationTypePolling | 5 | Aucun service de notification Cloud ; Interrogez plutôt les réponses entrantes. |
