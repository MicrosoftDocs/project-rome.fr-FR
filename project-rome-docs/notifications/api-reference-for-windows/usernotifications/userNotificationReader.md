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
# <a name="class-usernotificationreader"></a><span data-ttu-id="b9c53-105">Classe `UserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="b9c53-105">class `UserNotificationReader`</span></span>

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

<span data-ttu-id="b9c53-106">Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour.</span><span class="sxs-lookup"><span data-stu-id="b9c53-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="b9c53-107">Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="b9c53-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="methods"></a><span data-ttu-id="b9c53-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b9c53-108">Methods</span></span>

### <a name="readbatchasyncint32"></a><span data-ttu-id="b9c53-109">ReadBatchAsync(Int32)</span><span class="sxs-lookup"><span data-stu-id="b9c53-109">ReadBatchAsync(Int32)</span></span> 
<span data-ttu-id="b9c53-110">Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="b9c53-110">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a><span data-ttu-id="b9c53-111">Événements</span><span class="sxs-lookup"><span data-stu-id="b9c53-111">Events</span></span>


### <a name="datachanged"></a><span data-ttu-id="b9c53-112">DataChanged</span><span class="sxs-lookup"><span data-stu-id="b9c53-112">DataChanged</span></span>
<span data-ttu-id="b9c53-113">Déclenché lorsque le lecteur termine la synchronisation avec le serveur et a des modifications - nouvelle UserNotifications entrantes ou UserNotification met à jour pour notifier l’application.</span><span class="sxs-lookup"><span data-stu-id="b9c53-113">Raised when the reader completes sync with the server and has new change - new incoming UserNotifications or UserNotification updates to notify the app.</span></span> 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
