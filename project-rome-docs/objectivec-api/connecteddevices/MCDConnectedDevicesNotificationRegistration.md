---
title: MCDConnectedDevicesNotificationRegistration
description: Cette classe représente l’inscription de l’application avec un service de notification push (nécessaire pour certains scénarios de Project Rome).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801431"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a>Classe `MCDConnectedDevicesNotificationRegistration` 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 Cette classe représente l’inscription de l’application avec un service de notification push (nécessaire pour certains scénarios de Project Rome). Il communique cette information à la plateforme d’appareils connectés.

## <a name="properties"></a>Properties

### <a name="type"></a>Type
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

Les types de notifications dans cette configuration.

### <a name="token"></a>Jeton
`@property(nonatomic, readwrite, nonnull) NSString* token;`

Le jeton d’inscription.

### <a name="appid"></a>appId
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

L’ID d’application pour l’inscription aux notifications push.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

Le surnom d’application. Il doit s’agir du nom de l’application qui a été utilisé pour l’inscription sur le portail de développement Microsoft.