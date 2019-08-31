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
# <a name="class-usernotificationreader"></a><span data-ttu-id="a8dab-105">type`UserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="a8dab-105">class `UserNotificationReader`</span></span>

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

<span data-ttu-id="a8dab-106">Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a8dab-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="a8dab-107">Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.</span><span class="sxs-lookup"><span data-stu-id="a8dab-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="methods"></a><span data-ttu-id="a8dab-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a8dab-108">Methods</span></span>

### <a name="readbatchasyncint32"></a><span data-ttu-id="a8dab-109">ReadBatchAsync (Int32)</span><span class="sxs-lookup"><span data-stu-id="a8dab-109">ReadBatchAsync(Int32)</span></span> 
<span data-ttu-id="a8dab-110">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="a8dab-110">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a><span data-ttu-id="a8dab-111">Events</span><span class="sxs-lookup"><span data-stu-id="a8dab-111">Events</span></span>


### <a name="datachanged"></a><span data-ttu-id="a8dab-112">DataChanged</span><span class="sxs-lookup"><span data-stu-id="a8dab-112">DataChanged</span></span>
<span data-ttu-id="a8dab-113">Déclenché lorsque le lecteur termine la synchronisation avec le serveur et qu’il dispose de nouvelles mises à jour UserNotifications ou UserNotification entrantes pour avertir l’application.</span><span class="sxs-lookup"><span data-stu-id="a8dab-113">Raised when the reader completes sync with the server and has new change - new incoming UserNotifications or UserNotification updates to notify the app.</span></span> 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
