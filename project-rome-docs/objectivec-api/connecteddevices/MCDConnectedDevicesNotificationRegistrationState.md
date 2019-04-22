---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valeurs utilisées pour communiquer l’état de l’inscription du cloud.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800711"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>Classe `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
Valeurs utilisées pour communiquer l’état de l’inscription du cloud.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | L’inscription n’a jamais été démarrée.
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | L’inscription est terminée. |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | L’inscription est sur le point d’expirer et par conséquent, l’application doit effectuer à nouveau l’inscription. |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | L’inscription a expiré et par conséquent, l’application doit effectuer à nouveau l’inscription. |