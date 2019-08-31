---
title: UserNotificationChannel
description: Cette classe gère le cycle de vie des notifications utilisateur.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: ee30f0eab2bb212dddf1de401a91f0487c512705
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801441"
---
# <a name="class-usernotificationchannel"></a>type`UserNotificationChannel`

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications de l’utilisateur pour l’application. 

## <a name="methods"></a>Méthodes

### <a name="createreader"></a>CreateReader () 
Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a>CreateReader (UserNotificationReaderOptions) 
Créer un lecteur de notifications utilisateur avec des options 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a>CreateReaderWithState (chaîne) 
Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications. Le lecteur démarre à l’état de suivi fourni. 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a>GetUserNotificationAsync (chaîne)
Obtenir une notification utilisateur en fonction de son ID. 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a>DeleteUserNotificationAsync (chaîne)
Obtenir une notification utilisateur en fonction de son ID. 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a>SyncScope()
Obtient l’étendue de synchronisation de ce canal de notification utilisateur.
```C#
public static IUserDataFeedSyncScope SyncScope()
```