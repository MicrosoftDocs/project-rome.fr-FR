---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: Une classe utilisée pour définir la préférence de visibilité application (appelant) local lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800671"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a>Classe `MCDRemoteSystemLocalVisibilityKindFilter` 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Une classe utilisée pour définir la préférence de visibilité application (appelant) local lors de la découverte des systèmes distants.

## <a name="properties"></a>Properties

### <a name="kind"></a>Type
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

Le paramètre de visibilité à utiliser comme filtre.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

Crée et initialise une instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `localVisibilityKind` 

Une valeur MCDRemoteSystemLocalVisibilityKind indiquant le paramètre de visibilité de l’application locale à utiliser comme filtre.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemLocalVisibilityKind filtré par type.

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

Crée et initialise une instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `localVisibilityKind` 

Une valeur MCDRemoteSystemLocalVisibilityKind indiquant le paramètre de visibilité de l’application locale à utiliser comme filtre.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemLocalVisibilityKind initialisé avec le type.