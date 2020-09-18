---
title: MCDRemoteSystemKindFilter
description: En savoir plus sur la classe MCDRemoteSystemKindFilter. Cette classe est utilisée pour filtrer les systèmes distants en fonction du type d’appareil.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760673"
---
# <a name="class-mcdremotesystemkindfilter"></a>type `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Classe utilisée pour filtrer les systèmes distants en fonction du type d’appareil.

## <a name="properties"></a>Propriétés

### <a name="kinds"></a>catégories
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

Tableau de chaînes indiquant les genres de périphériques à filtrer.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Nouvelle instance de cette classe filtrée sur des genres.

#### <a name="parameters"></a>Paramètres 
* `kinds`

 Tableau de chaînes indiquant les genres de périphériques à filtrer.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemKindFilter filtré avec des genres.

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Nouvelle instance de cette classe filtrée sur des genres.

#### <a name="parameters"></a>Paramètres 
* `kinds` 

Tableau de chaînes indiquant les genres de périphériques à filtrer.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemKindFilter initialisé avec des genres.