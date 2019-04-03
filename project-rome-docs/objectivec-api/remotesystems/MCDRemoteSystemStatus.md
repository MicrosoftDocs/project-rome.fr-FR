---
title: MCDRemoteSystemStatus
description: Contient des valeurs qui décrivent la disponibilité d’un système distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907581"
---
# <a name="enum-mcdremotesystemstatus"></a>Enum `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
Contient des valeurs qui décrivent la disponibilité d’un système distant. Sur les applications iOS, une valeur de **MCDRemoteSystemStatusUnknown** surviennent toujours ; d’autres valeurs sont disponibles uniquement sur les systèmes Windows.

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | Le système distant est signalé comme étant indisponible. |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | L’état du système distant est déterminé (se produit pendant le processus de découverte). |
| MCDRemoteSystemStatusAvailable | 2 | Le système distant est signalé comme étant disponible. |
| MCDRemoteSystemStatusUnknown | 3 | L’état est inconnu. |
