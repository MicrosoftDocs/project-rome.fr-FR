---
title: MCDRemoteSystemAuthorizationKindFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’autorisation.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801251"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a>Classe `MCDRemoteSystemAuthorizationKindFilter` 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

Une classe utilisée pour filtrer les systèmes distants selon le type d’autorisation.

## <a name="properties"></a>Properties

### <a name="kind"></a>Type
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

Le type d’autorisation pour filtrer.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Une nouvelle instance de cette classe filtrée sur MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Paramètres 
* `authorizationKind` 

Le type d’autorisation pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemAuthorizationKindFilter avec le filtre d’autorisation fourni.

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Une nouvelle instance de cette classe avec MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Paramètres 
* `authorizationKind` 

Le type d’autorisation pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemAuthorizationKindFilter initialisé avec l’authorizationKind.