---
title: MCDRemoteSystemDiscoveryTypeFilter
description: En savoir plus sur la classe MCDRemoteSystemDiscoveryTypeFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type de découverte.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760693"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>type `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

Classe utilisée pour filtrer les systèmes distants en fonction du type de découverte.

## <a name="properties"></a>Propriétés

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

Type de découverte à filtrer.

> Remarque : sur Android, la plateforme appareils connectés peut uniquement utiliser Bluetooth sur les systèmes qui exécutent Android 8,0 (Oreo) ou version ultérieure.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Paramètres 
* `discoveryType` Type de découverte à filtrer.

#### <a name="returns"></a>Retours
Nouvelle instance de cette classe avec la valeur de type donnée. Les valeurs peuvent être AND’ed ensemble pour appliquer plusieurs filtres à la fois.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Paramètres 
* `discoveryType` Type de découverte à filtrer.

#### <a name="returns"></a>Retours
Nouvelle instance de cette classe avec la valeur de type donnée. Les valeurs peuvent être AND’ed ensemble pour appliquer plusieurs filtres à la fois.