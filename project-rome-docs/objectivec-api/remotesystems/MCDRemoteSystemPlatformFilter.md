---
title: MCDRemoteSystemPlatformFilter
description: Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801217"
---
# <a name="class-mcdremotesystemplatformfilter"></a>Classe `MCDRemoteSystemPlatformFilter` 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

Une classe utilisée pour filtrer les systèmes distants en fonction de la plateforme du système d’exploitation qu’ils sont en cours d’exécution.

## <a name="properties"></a>Properties

### <a name="platform"></a>Plateforme
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithplatform"></a>filterWithPlatform
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>Paramètres 
* `platform` 

Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemPlatformFilter filtré par la plateforme.

### <a name="initwithplatform"></a>initWithPlatform
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>Paramètres 
* `platform` 

Valeur MCDRemoteSystemPlatform indiquant la plateforme pour filtrer.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemPlatformFilter initialisé avec un filtre par plateforme.