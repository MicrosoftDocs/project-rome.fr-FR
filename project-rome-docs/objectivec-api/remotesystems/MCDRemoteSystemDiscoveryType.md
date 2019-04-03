---
title: MCDRemoteSystemDiscoveryType
description: Contient des valeurs qui décrivent les systèmes distants comment sont en mesure d’être découverts.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907031"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a>Enum `MCDRemoteSystemDiscoveryType` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

Contient des valeurs qui décrivent les systèmes distants comment sont en mesure d’être découverts. 

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemDiscoveryTypeAny   | 0     | Systèmes distants sont détectables via toute connexion.  |
| MCDRemoteSystemDiscoveryTypeProximal | 1     | Les systèmes à distance ne sont plus détectables via une connexion PROXIMALE, comme une variable locale
réseau ou une connexion Bluetooth. |
| MCDRemoteSystemDiscoveryTypeCloud | 2     | Systèmes distants ne sont pas identifiables par la connexion de cloud. |
| MCDRemoteSystemDiscoveryTypeSpatiallyProximal | 3     | Systèmes distants sont détectables via une connexion PROXIMALE et sont supposés être
dans l’espace proche de l’appareil client (dans la plage de Bluetooth, par exemple).  |

