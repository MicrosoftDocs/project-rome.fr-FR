---
title: UserNotificationReader
description: Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour. Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.
keywords: Microsoft, windows, la notification utilisateur, et conseils pour windows
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801421"
---
# <a name="class-usernotificationreader"></a>Classe `UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour. Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.  

## <a name="methods"></a>Méthodes

### <a name="readbatchasyncint32"></a>ReadBatchAsync(Int32) 
Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>Événements


### <a name="datachanged"></a>DataChanged
Déclenché lorsque le lecteur termine la synchronisation avec le serveur et a des modifications - nouvelle UserNotifications entrantes ou UserNotification met à jour pour notifier l’application. 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
