---
title: MCDUserDataFeedNotificationTypes
description: En savoir plus sur la classe MCDUserDataFeedNotificationTypes. Cette classe est chargée de fournir les types de notifications.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a9bb9b41309e32a429926c52769da9bc767ef5bc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760983"
---
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="263ba-105">type `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="263ba-105">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="263ba-106">Cette classe fournit les types de notification valides pour MCDUserDataFeedSyncScope. notificationType.</span><span class="sxs-lookup"><span data-stu-id="263ba-106">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="263ba-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="263ba-107">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="263ba-108">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="263ba-108">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="263ba-109">Représente les notifications push entrantes.</span><span class="sxs-lookup"><span data-stu-id="263ba-109">Represents the incoming push notifications.</span></span>  <span data-ttu-id="263ba-110">Il n’existe aucun rescrictions pour les notifications push autres que les restrictions de domaine/serveur.</span><span class="sxs-lookup"><span data-stu-id="263ba-110">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="263ba-111">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="263ba-111">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="263ba-112">Rétrograder toutes les notifications push vers une notification uniquement indiquant au système de se synchroniser pour recevoir les données, même si les données peuvent être contenues dans la notification push.</span><span class="sxs-lookup"><span data-stu-id="263ba-112">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="263ba-113">nonotification</span><span class="sxs-lookup"><span data-stu-id="263ba-113">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="263ba-114">Empêcher les notifications pour les nouvelles données utilisateur, recevoir uniquement les nouvelles données lorsque UserDataFeed. startSync est appelé, ou lors de l’interaction avec le serveur d’une autre manière</span><span class="sxs-lookup"><span data-stu-id="263ba-114">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>
