---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: Classe d’arguments événement pour l’événement MCDConnectedDevicesNotificationRegistration état modifié.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800691"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a>Classe `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs` 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
Classe d’arguments événement pour l’événement MCDConnectedDevicesNotificationRegistration état modifié. Cela permet de garantir que l’application obtient informée sur les nouveaux messages de plateforme d’appareils connectés via le mécanisme de notification correct.

## <a name="properties"></a>Properties

### <a name="account"></a>compte
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

Le compte pour lequel l’état d’inscription de notification a été modifiée pour.

### <a name="registration"></a>registration
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

Les informations pour l’inscription de l’instance dont l’état a changé.

### <a name="state"></a>État
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

Le nouvel état de l’inscription.