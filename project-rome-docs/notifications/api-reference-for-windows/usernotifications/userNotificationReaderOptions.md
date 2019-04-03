---
title: UserNotificationReaderOptions
description: Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.
keywords: Microsoft, windows, les Notifications de graphique, les procédures relatives à Windows
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909681"
---
# <a name="class-usernotificationreaderoptions"></a>Classe `UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas. 

## <a name="constructors"></a>Constructeurs

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
Crée et initialise une nouvelle instance de UserNotificationReaderOptions.

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)
Crée et initialise une nouvelle instance de UserNotificationReaderOptions avec les filtres et la position de début spécifiée. 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>Properties

|Nom | Description |
|:-- |:-- |
|StartPosition |Obtient ou définit la position de départ pour cette instance de UserNotificationReaderOptions.|
|   StatusFilter |Obtient ou définit le filtre d’état pour ce lecteur de notification utilisateur que vous souhaitez créer.| 
|   ReadStateFilter |Obtient ou définit le filtre d’état de lecture qui est défini pour cette instance de UserNotificationReaderOptions.| 
|   UserActionStateFilter|Getor définir le filtre d’état utilisateur action définie pour cette instance de UserNotificationReaderOptions.| 




