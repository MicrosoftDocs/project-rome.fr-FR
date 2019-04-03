---
title: MCDUserNotificationReaderOptions
description: Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907981"
---
# <a name="class-mcdusernotificationreaderoptions"></a>Classe `MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas. 

## <a name="properties"></a>Properties

### <a name="startposition"></a>startPosition
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Obtient ou définit la position de départ pour cette instance de UserNotificationReaderOptions.

### <a name="statusfilter"></a>statusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Obtient ou définit le filtre d’état pour ce lecteur de notification utilisateur que vous souhaitez créer.

### <a name="readstatefilter"></a>readStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Obtient ou définit le filtre d’état de lecture qui est défini pour cette instance de UserNotificationReaderOptions

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor définir le filtre d’état utilisateur action définie pour cette instance de UserNotificationReaderOptions.

## <a name="constructors"></a>Constructeurs

### <a name="options"></a>options
`+ (nullable instancetype)options;` Crée et initialise une nouvelle instance des options pour les Notifications de l’utilisateur.