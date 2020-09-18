---
title: MCDUserNotificationChannel
description: En savoir plus sur la classe MCDUserNotificationChannel. Cette classe gère le cycle de vie des notifications utilisateur.
keywords: Microsoft, Windows, appareil Relay, procédure iOS, iPhone
ms.openlocfilehash: dc7e451494014cdcdebd056b00e57cfdf5f0757f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760873"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="d53df-105">type `MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="d53df-105">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="d53df-106">Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications de l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="d53df-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="d53df-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d53df-107">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="d53df-108">syncScope</span><span class="sxs-lookup"><span data-stu-id="d53df-108">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="d53df-109">SyncScope utilisé pour garantir que les UserNotifications sont inclus dans le flux.</span><span class="sxs-lookup"><span data-stu-id="d53df-109">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="d53df-110">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="d53df-110">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="d53df-111">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="d53df-111">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="d53df-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d53df-112">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="d53df-113">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="d53df-113">userDataFeed</span></span>
<span data-ttu-id="d53df-114">MCDUserDataFeed utilisé pour initialiser cette classe.</span><span class="sxs-lookup"><span data-stu-id="d53df-114">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="d53df-115">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="d53df-115">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="d53df-116">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="d53df-116">userDataFeed</span></span>
<span data-ttu-id="d53df-117">MCDUserDataFeed utilisé pour initialiser cette classe.</span><span class="sxs-lookup"><span data-stu-id="d53df-117">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="d53df-118">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d53df-118">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="d53df-119">createReader</span><span class="sxs-lookup"><span data-stu-id="d53df-119">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="d53df-120">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="d53df-120">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="d53df-121">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="d53df-121">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="d53df-122">Créez un lecteur de notifications utilisateur avec des options.</span><span class="sxs-lookup"><span data-stu-id="d53df-122">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="d53df-123">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="d53df-123">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="d53df-124">Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="d53df-124">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="d53df-125">Le lecteur démarre à l’état de suivi fourni.</span><span class="sxs-lookup"><span data-stu-id="d53df-125">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="d53df-126">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="d53df-126">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="d53df-127">Obtenir une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="d53df-127">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="d53df-128">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="d53df-128">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="d53df-129">Supprimer une notification utilisateur en fonction de son ID.</span><span class="sxs-lookup"><span data-stu-id="d53df-129">Delete a user notification based on its id.</span></span> 