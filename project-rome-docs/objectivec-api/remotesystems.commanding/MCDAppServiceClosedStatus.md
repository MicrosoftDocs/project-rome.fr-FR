---
title: MCDAppServiceClosedStatus
description: Contient des valeurs qui décrivent une connexion fermée à un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907721"
---
# <a name="enum-mcdappserviceclosedstatus"></a>Enum `MCDAppServiceClosedStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

Contient des valeurs qui décrivent une connexion fermée à un service d’application à distance.

|Membre   |Value   |Description   |
|--------|-------|-------------|
|MCDAppServiceClosedStatusCompleted |0| Le point de terminaison pour le service d’application a été fermée correctement.|
|MCDAppServiceClosedStatusCanceled |1| Le point de terminaison pour le service d’application a été fermée par le client ou le système.|
|MCDAppServiceClosedStatusResourceLimitsExceeded |2| Le point de terminaison pour le service d’application a été fermée, car le point de terminaison a manqué de ressources.|
|MCDAppServiceClosedStatusUnknown |3| Une erreur inconnue s’est produite.|