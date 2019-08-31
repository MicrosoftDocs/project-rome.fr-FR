---
title: MCDUserNotificationReaderOptions
description: Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907981"
---
# <a name="class-mcdusernotificationreaderoptions"></a>type`MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes. 

## <a name="properties"></a>Properties

### <a name="startposition"></a>startPosition
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`Obtient ou définit la position de départ de cette instance de UserNotificationReaderOptions.

### <a name="statusfilter"></a>statusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`Obtient ou définit le filtre d’État pour le lecteur de notifications utilisateur que vous souhaitez créer.

### <a name="readstatefilter"></a>readStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`Obtient ou définit le filtre d’état de lecture défini pour cette instance de UserNotificationReaderOptions

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`Getor définit le filtre d’état des actions de l’utilisateur défini pour cette instance de UserNotificationReaderOptions.

## <a name="constructors"></a>Constructeurs

### <a name="options"></a>options
`+ (nullable instancetype)options;`Crée et Initialise une nouvelle instance d’options pour les notifications utilisateur.