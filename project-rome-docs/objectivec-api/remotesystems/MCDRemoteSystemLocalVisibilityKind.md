---
title: MCDRemoteSystemLocalVisibilityKind
description: Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801101"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a>Enum `MCDRemoteSystemLocalVisibilityKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemLocalVisibilityKindShowAll | 0 | Afficher toutes les applications détectables, y compris l’application appelante.
| MCDRemoteSystemLocalVisibilityKindHideLocalApp | 1 | Masquer l’application appelante.