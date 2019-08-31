---
title: MCDUserNotificationStatus
description: Contient des valeurs qui déterminent si la notification est supprimée ou non. Les notifications supprimées seront toujours dans le magasin de notifications et seront retournées par le lecteur avant le nettoyage de la plateforme. Un UserNotificationStatusFilter de filtre de lecteur correspondant peut être appliqué pour empêcher l’émission de ces notifications dans le lecteur de notifications.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800811"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="91237-106">variables`MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="91237-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="91237-107">Contient des valeurs qui déterminent si la notification est supprimée ou non.</span><span class="sxs-lookup"><span data-stu-id="91237-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="91237-108">Les notifications supprimées seront toujours dans le magasin de notifications et seront retournées par le lecteur avant le nettoyage de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="91237-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="91237-109">Un UserNotificationStatusFilter de filtre de lecteur correspondant peut être appliqué pour empêcher l’émission de ces notifications dans le lecteur de notifications.</span><span class="sxs-lookup"><span data-stu-id="91237-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="91237-110">Name</span><span class="sxs-lookup"><span data-stu-id="91237-110">Name</span></span> | <span data-ttu-id="91237-111">Value</span><span class="sxs-lookup"><span data-stu-id="91237-111">Value</span></span> | <span data-ttu-id="91237-112">Description</span><span class="sxs-lookup"><span data-stu-id="91237-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="91237-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="91237-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="91237-114">0</span><span class="sxs-lookup"><span data-stu-id="91237-114">0</span></span>| <span data-ttu-id="91237-115">La notification est toujours active et persistante dans le magasin de plateformes des appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="91237-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="91237-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="91237-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="91237-117">1</span><span class="sxs-lookup"><span data-stu-id="91237-117">1</span></span>| <span data-ttu-id="91237-118">La notification a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="91237-118">The notification has been deleted.</span></span>|