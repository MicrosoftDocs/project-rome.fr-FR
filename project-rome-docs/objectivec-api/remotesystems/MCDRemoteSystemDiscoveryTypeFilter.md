---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Une classe utilisée pour filtrer en fonction de type de découverte de systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907521"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>Classe `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

Une classe utilisée pour filtrer en fonction de type de découverte de systèmes distants.

## <a name="properties"></a>Properties

### <a name="type"></a>Type
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

Le type de découverte pour filtrer.

> Remarque: Sur Android, la plateforme d’appareils connectés peuvent uniquement utiliser Bluetooth sur les systèmes exécutant Android 8.0 (Oreo) ou version ultérieure.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Paramètres 
* `discoveryType` Le type de découverte pour filtrer.

#### <a name="returns"></a>Returns
Une nouvelle instance de cette classe avec la valeur du type donné. Valeurs peuvent être liées par and ensemble pour appliquer plusieurs filtres à la fois.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Paramètres 
* `discoveryType` Le type de découverte pour filtrer.

#### <a name="returns"></a>Returns
Une nouvelle instance de cette classe avec la valeur du type donné. Valeurs peuvent être liées par and ensemble pour appliquer plusieurs filtres à la fois.