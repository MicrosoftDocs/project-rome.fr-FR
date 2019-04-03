---
title: MCDUserDataFeedNotificationTypes
description: Cette classe est chargée de fournir les types de notification
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908911"
---
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="eb439-104">Classe `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="eb439-104">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="eb439-105">Cette classe fournit les types de notification valide pour MCDUserDataFeedSyncScope.notificationType.</span><span class="sxs-lookup"><span data-stu-id="eb439-105">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="eb439-106">Properties</span><span class="sxs-lookup"><span data-stu-id="eb439-106">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="eb439-107">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="eb439-107">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="eb439-108">Représente les notifications push entrantes.</span><span class="sxs-lookup"><span data-stu-id="eb439-108">Represents the incoming push notifications.</span></span>  <span data-ttu-id="eb439-109">Il n’y a aucun rescrictions pour envoyer des notifications autres que des restrictions de domaine/serveur.</span><span class="sxs-lookup"><span data-stu-id="eb439-109">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="eb439-110">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="eb439-110">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="eb439-111">Rétrograder tous les notifications push à une notification n'indiquant que le système de synchronisation pour recevoir les données, même si les données pourraient être contenues dans les notifications push.</span><span class="sxs-lookup"><span data-stu-id="eb439-111">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="eb439-112">noNotification</span><span class="sxs-lookup"><span data-stu-id="eb439-112">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="eb439-113">Empêcher les notifications pour les nouvelles données utilisateur, de recevoir uniquement les nouvelles données lorsque UserDataFeed.startSync est appelée, ou lors de l’interaction avec le serveur par d’autres moyens</span><span class="sxs-lookup"><span data-stu-id="eb439-113">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>
