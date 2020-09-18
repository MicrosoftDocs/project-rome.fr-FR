---
title: MCDConnectedDevicesNotification
description: En savoir plus sur la classe MCDConnectedDevicesNotification. Cette classe est le résultat du traitement d’une notification.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761013"
---
# <a name="class-mcdconnecteddevicesnotification"></a>type `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
Résultat du traitement d’une notification.

## <a name="methods"></a>Méthodes

### <a name="tryparse"></a>tryParse

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

Tente d’analyser un MCDConnectedDevicesNotification à partir d’une carte mise en forme APNS.

#### <a name="parameters"></a>Paramètres 
* `dictionary` 

Carte reçue de la notification APNS à la plateforme d’appareils connectés pour traitement.
