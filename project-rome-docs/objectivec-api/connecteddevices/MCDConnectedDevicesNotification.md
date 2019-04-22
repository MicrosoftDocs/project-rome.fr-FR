---
title: MCDConnectedDevicesNotification
description: Résultat du traitement d’une notification.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800601"
---
# <a name="class-mcdconnecteddevicesnotification"></a>Classe `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
Résultat du traitement d’une notification.

## <a name="methods"></a>Méthodes

### <a name="tryparse"></a>tryParse

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

Tentatives d’analyse une MCDConnectedDevicesNotification à partir d’un APNS mise en forme de carte.

#### <a name="parameters"></a>Paramètres 
* `dictionary` 

La carte a reçu de la notification APNS de la plateforme d’appareils connectés pour le traitement.
