---
title: MCDRemoteSystemStatus
description: En savoir plus sur l’énumération MCDRemoteSystemStatus. Cette énumération contient des valeurs qui décrivent la disponibilité d’un système distant.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760653"
---
# <a name="enum-mcdremotesystemstatus"></a>variables `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
Contient des valeurs qui décrivent la disponibilité d’un système distant. Sur les applications iOS, la valeur **MCDRemoteSystemStatusUnknown** est toujours rencontrée. les autres valeurs sont disponibles uniquement sur les systèmes Windows.

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | Le système distant est signalé comme étant non disponible. |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | L’état du système distant est en cours de détermination (se produit pendant le processus de découverte). |
| MCDRemoteSystemStatusAvailable | 2 | Le système distant est signalé comme étant disponible. |
| MCDRemoteSystemStatusUnknown | 3 | L’État est inconnu. |
