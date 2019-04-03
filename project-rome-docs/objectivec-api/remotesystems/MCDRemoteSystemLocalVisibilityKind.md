---
title: MCDRemoteSystemLocalVisibilityKind
description: Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908861"
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