---
title: MCDConnectedDevicesNotificationRegistrationState
description: En savoir plus sur la classe MCDConnectedDevicesNotificationRegistrationState. Ces valeurs sont utilisées pour communiquer l’état de l’inscription du Cloud.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761113"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>type `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
Valeurs utilisées pour communiquer l’état de l’inscription du Cloud.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | L’inscription n’a jamais été démarrée.
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | L’inscription est terminée. |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | L’inscription est sur le point d’expirer et l’application doit donc réexécuter l’inscription. |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | L’inscription a expiré et l’application doit à nouveau effectuer l’inscription. |