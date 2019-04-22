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
# <a name="class-usernotificationchannel"></a><span data-ttu-id="b1e57-104">Classe `UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="b1e57-104">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="b1e57-105">Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications à l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="b1e57-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="b1e57-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b1e57-106">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="b1e57-107">CreateReader()</span><span class="sxs-lookup"><span data-stu-id="b1e57-107">CreateReader()</span></span> 
<span data-ttu-id="b1e57-108">Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="b1e57-108">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="b1e57-109">CreateReader(UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="b1e57-109">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="b1e57-110">Créer un lecteur de notification utilisateur avec options</span><span class="sxs-lookup"><span data-stu-id="b1e57-110">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="b1e57-111">CreateReaderWithState(String)</span><span class="sxs-lookup"><span data-stu-id="b1e57-111">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="b1e57-112">Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="b1e57-112">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="b1e57-113">Le lecteur démarre à l’état de suivi.</span><span class="sxs-lookup"><span data-stu-id="b1e57-113">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="b1e57-114">GetUserNotificationAsync(String)</span><span class="sxs-lookup"><span data-stu-id="b1e57-114">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="b1e57-115">Recevez une notification de l’utilisateur en fonction de son id.</span><span class="sxs-lookup"><span data-stu-id="b1e57-115">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="b1e57-116">DeleteUserNotificationAsync(String)</span><span class="sxs-lookup"><span data-stu-id="b1e57-116">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="b1e57-117">Recevez une notification de l’utilisateur en fonction de son id.</span><span class="sxs-lookup"><span data-stu-id="b1e57-117">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="b1e57-118">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="b1e57-118">SyncScope()</span></span>
<span data-ttu-id="b1e57-119">Obtenir l’étendue de la synchronisation de ce canal de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1e57-119">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```