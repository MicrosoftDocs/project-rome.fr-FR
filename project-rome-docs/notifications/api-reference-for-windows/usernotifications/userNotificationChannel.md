---
title: UserNotificationChannel
description: En savoir plus sur la classe UserNotificationChannel. Cette classe gère le cycle de vie des notifications utilisateur.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: f5347878da2d82035db1dbb63cca015180f66a34
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760933"
---
# <a name="class-usernotificationchannel"></a><span data-ttu-id="cd9c9-105">type `UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="cd9c9-105">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="cd9c9-106">Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications de l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="cd9c9-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cd9c9-107">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="cd9c9-108">CreateReader ()</span><span class="sxs-lookup"><span data-stu-id="cd9c9-108">CreateReader()</span></span> 
<span data-ttu-id="cd9c9-109">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-109">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="cd9c9-110">CreateReader (UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="cd9c9-110">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="cd9c9-111">Créer un lecteur de notifications utilisateur avec des options</span><span class="sxs-lookup"><span data-stu-id="cd9c9-111">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="cd9c9-112">CreateReaderWithState (chaîne)</span><span class="sxs-lookup"><span data-stu-id="cd9c9-112">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="cd9c9-113">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-113">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="cd9c9-114">Le lecteur démarre à l’état de suivi fourni.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-114">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="cd9c9-115">GetUserNotificationAsync (chaîne)</span><span class="sxs-lookup"><span data-stu-id="cd9c9-115">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="cd9c9-116">Obtenir une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-116">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="cd9c9-117">DeleteUserNotificationAsync (chaîne)</span><span class="sxs-lookup"><span data-stu-id="cd9c9-117">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="cd9c9-118">Obtenir une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-118">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="cd9c9-119">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="cd9c9-119">SyncScope()</span></span>
<span data-ttu-id="cd9c9-120">Obtient l’étendue de synchronisation de ce canal de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cd9c9-120">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```