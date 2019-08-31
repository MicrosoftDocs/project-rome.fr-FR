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
# <a name="class-usernotificationchannel"></a><span data-ttu-id="6f2aa-104">type`UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="6f2aa-104">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="6f2aa-105">Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications de l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="6f2aa-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6f2aa-106">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="6f2aa-107">CreateReader ()</span><span class="sxs-lookup"><span data-stu-id="6f2aa-107">CreateReader()</span></span> 
<span data-ttu-id="6f2aa-108">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-108">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="6f2aa-109">CreateReader (UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="6f2aa-109">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="6f2aa-110">Créer un lecteur de notifications utilisateur avec des options</span><span class="sxs-lookup"><span data-stu-id="6f2aa-110">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="6f2aa-111">CreateReaderWithState (chaîne)</span><span class="sxs-lookup"><span data-stu-id="6f2aa-111">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="6f2aa-112">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-112">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="6f2aa-113">Le lecteur démarre à l’état de suivi fourni.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-113">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="6f2aa-114">GetUserNotificationAsync (chaîne)</span><span class="sxs-lookup"><span data-stu-id="6f2aa-114">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="6f2aa-115">Obtenir une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-115">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="6f2aa-116">DeleteUserNotificationAsync (chaîne)</span><span class="sxs-lookup"><span data-stu-id="6f2aa-116">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="6f2aa-117">Obtenir une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-117">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="6f2aa-118">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="6f2aa-118">SyncScope()</span></span>
<span data-ttu-id="6f2aa-119">Obtient l’étendue de synchronisation de ce canal de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f2aa-119">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```