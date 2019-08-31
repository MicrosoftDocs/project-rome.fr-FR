---
title: UserNotificationReader
description: Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur. Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.
keywords: Microsoft, Windows, notification utilisateur, procédures Windows
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801421"
---
# <a name="class-usernotificationreader"></a>type`UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur. Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.  

## <a name="methods"></a>Méthodes

### <a name="readbatchasyncint32"></a>ReadBatchAsync (Int32) 
Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>Events


### <a name="datachanged"></a>DataChanged
Déclenché lorsque le lecteur termine la synchronisation avec le serveur et qu’il dispose de nouvelles mises à jour UserNotifications ou UserNotification entrantes pour avertir l’application. 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
