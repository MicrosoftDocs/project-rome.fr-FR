---
title: UserNotificationChannel
description: Cette classe gère le cycle de vie des notifications à l’utilisateur.
keywords: Microsoft, windows, les Notifications de graphique, les procédures relatives à Windows
ms.openlocfilehash: ee30f0eab2bb212dddf1de401a91f0487c512705
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801441"
---
# <a name="class-usernotificationchannel"></a>Classe `UserNotificationChannel`

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications à l’utilisateur pour l’application. 

## <a name="methods"></a>Méthodes

### <a name="createreader"></a>CreateReader() 
Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a>CreateReader(UserNotificationReaderOptions) 
Créer un lecteur de notification utilisateur avec options 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a>CreateReaderWithState(String) 
Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application. Le lecteur démarre à l’état de suivi. 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a>GetUserNotificationAsync(String)
Recevez une notification de l’utilisateur en fonction de son id. 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a>DeleteUserNotificationAsync(String)
Recevez une notification de l’utilisateur en fonction de son id. 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a>SyncScope()
Obtenir l’étendue de la synchronisation de ce canal de notification utilisateur.
```C#
public static IUserDataFeedSyncScope SyncScope()
```