---
title: UserNotificationReaderOptions
description: Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801381"
---
# <a name="class-usernotificationreaderoptions"></a>type`UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes. 

## <a name="constructors"></a>Constructeurs

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
Crée et Initialise une nouvelle instance de UserNotificationReaderOptions.

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)
Crée et Initialise une nouvelle instance de UserNotificationReaderOptions avec les filtres et la position de début spécifiés. 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>Properties

|Nom | Description |
|:-- |:-- |
|StartPosition |Obtient ou définit la position de départ de cette instance de UserNotificationReaderOptions.|
|   StatusFilter |Obtient ou définit le filtre d’État pour le lecteur de notifications utilisateur que vous souhaitez créer.| 
|   ReadStateFilter |Obtient ou définit le filtre d’état de lecture défini pour cette instance de UserNotificationReaderOptions.| 
|   UserActionStateFilter|Getor définit le filtre d’état des actions de l’utilisateur défini pour cette instance de UserNotificationReaderOptions.| 




