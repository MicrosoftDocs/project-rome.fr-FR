---
title: MCDRemoteSystemAuthorizationKindFilter
description: En savoir plus sur la classe MCDRemoteSystemAuthorizationKindFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type d’autorisation.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760703"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a>type `MCDRemoteSystemAuthorizationKindFilter` 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

Classe utilisée pour filtrer les systèmes distants en fonction du type d’autorisation.

## <a name="properties"></a>Propriétés

### <a name="kind"></a>kind
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

Type d’autorisation à filtrer.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Nouvelle instance de cette classe filtrée sur MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Paramètres 
* `authorizationKind` 

Type d’autorisation à filtrer.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemAuthorizationKindFilter avec le filtre d’autorisation fourni.

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Nouvelle instance de cette classe avec MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Paramètres 
* `authorizationKind` 

Type d’autorisation à filtrer.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemAuthorizationKindFilter initialisé avec authorizationKind.