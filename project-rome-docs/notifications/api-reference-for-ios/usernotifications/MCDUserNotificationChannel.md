---
title: MCDUserNotificationChannel
description: Cette classe gère le cycle de vie des notifications à l’utilisateur.
keywords: Microsoft, windows, relais de l’appareil, iOS procédures, procédures iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907181"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="7a97b-104">Classe `MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="7a97b-104">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="7a97b-105">Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications à l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="7a97b-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="7a97b-106">Properties</span><span class="sxs-lookup"><span data-stu-id="7a97b-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="7a97b-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="7a97b-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="7a97b-108">SyncScope utilisée pour garantir la Qu'usernotifications sont incluses dans le flux.</span><span class="sxs-lookup"><span data-stu-id="7a97b-108">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="7a97b-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="7a97b-109">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="7a97b-110">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="7a97b-110">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="7a97b-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7a97b-111">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="7a97b-112">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="7a97b-112">userDataFeed</span></span>
<span data-ttu-id="7a97b-113">MCDUserDataFeed utilisée pour initialiser cette classe.</span><span class="sxs-lookup"><span data-stu-id="7a97b-113">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="7a97b-114">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="7a97b-114">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="7a97b-115">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="7a97b-115">userDataFeed</span></span>
<span data-ttu-id="7a97b-116">MCDUserDataFeed utilisée pour initialiser cette classe.</span><span class="sxs-lookup"><span data-stu-id="7a97b-116">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="7a97b-117">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7a97b-117">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="7a97b-118">createReader</span><span class="sxs-lookup"><span data-stu-id="7a97b-118">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="7a97b-119">Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="7a97b-119">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="7a97b-120">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="7a97b-120">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="7a97b-121">Créer un lecteur de notification utilisateur avec les options.</span><span class="sxs-lookup"><span data-stu-id="7a97b-121">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="7a97b-122">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="7a97b-122">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="7a97b-123">Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.</span><span class="sxs-lookup"><span data-stu-id="7a97b-123">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="7a97b-124">Le lecteur démarre à l’état de suivi.</span><span class="sxs-lookup"><span data-stu-id="7a97b-124">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="7a97b-125">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="7a97b-125">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="7a97b-126">Recevez une notification de l’utilisateur en fonction de son id.</span><span class="sxs-lookup"><span data-stu-id="7a97b-126">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="7a97b-127">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="7a97b-127">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="7a97b-128">Supprimer une notification à l’utilisateur en fonction de son id.</span><span class="sxs-lookup"><span data-stu-id="7a97b-128">Delete a user notification based on its id.</span></span> 