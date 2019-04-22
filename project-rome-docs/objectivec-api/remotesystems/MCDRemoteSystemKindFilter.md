---
title: MCDRemoteSystemKindFilter
description: Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801331"
---
# <a name="class-mcdremotesystemkindfilter"></a>Classe `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Une classe utilisée pour filtrer les systèmes distants selon le type d’appareil.

## <a name="properties"></a>Properties

### <a name="kinds"></a>types
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

Un tableau de chaînes indiquant les types d’appareil pour filtrer.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Une nouvelle instance de cette classe filtrée sur les types.

#### <a name="parameters"></a>Paramètres 
* `kinds`

 Un tableau de chaînes indiquant les types d’appareil pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemKindFilter filtré avec des types.

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Une nouvelle instance de cette classe filtrée sur les types.

#### <a name="parameters"></a>Paramètres 
* `kinds` 

Un tableau de chaînes indiquant les types d’appareil pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemKindFilter initialisé avec les types.