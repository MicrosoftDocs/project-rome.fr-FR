---
title: MCDUserDataFeedSyncScopeFlags
description: En savoir plus sur la classe MCDUserDataFeedSyncScopeFlags. Cette classe fournit des indicateurs valides facultatifs pour MCDUserDataFeedSyncScope. syncScopeFlags.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8a1f5ae5b157f8e8f8113277778c2951f92fbbfb
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760963"
---
# <a name="class-mcduserdatafeedsyncscopeflags"></a>type `MCDUserDataFeedSyncScopeFlags`

```
@interface MCDUserDataFeedSyncScopeFlags : NSObject
```

Cette classe fournit des indicateurs valides facultatifs pour MCDUserDataFeedSyncScope. syncScopeFlags.

## <a name="properties"></a>Propriétés

### <a name="excludeautogenerated"></a>excludeAutoGenerated

`@property(class, nonatomic, readonly, nonnull) NSString* excludeAutoGenerated;`

Excluez les activités qui sont générées automatiquement par SAM sur Windows.

### <a name="includewebactionable"></a>includeWebActionable
`@property(class, nonatomic, readonly, nonnull) NSString* includeWebActionable;`

Toujours inclure les activités qui peuvent être activées par le biais de l’application Web.