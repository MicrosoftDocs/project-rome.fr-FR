---
title: MCDUserNotificationStatus
description: Contient des valeurs qui détermine si la notification est supprimée ou non. Notifications supprimées seront toujours dans le magasin de notification et renvoyées par le lecteur avant le nettoyage de la plateforme se produit. Un filtre de lecteur correspondante UserNotificationStatusFilter peut être appliqué pour empêcher ces notifications de s’afficher dans le lecteur de notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800811"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="f6ae0-106">Enum `MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="f6ae0-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="f6ae0-107">Contient des valeurs qui détermine si la notification est supprimée ou non.</span><span class="sxs-lookup"><span data-stu-id="f6ae0-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="f6ae0-108">Notifications supprimées seront toujours dans le magasin de notification et renvoyées par le lecteur avant le nettoyage de la plateforme se produit.</span><span class="sxs-lookup"><span data-stu-id="f6ae0-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="f6ae0-109">Un filtre de lecteur correspondante UserNotificationStatusFilter peut être appliqué pour empêcher ces notifications de s’afficher dans le lecteur de notification.</span><span class="sxs-lookup"><span data-stu-id="f6ae0-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="f6ae0-110">Nom</span><span class="sxs-lookup"><span data-stu-id="f6ae0-110">Name</span></span> | <span data-ttu-id="f6ae0-111">Value</span><span class="sxs-lookup"><span data-stu-id="f6ae0-111">Value</span></span> | <span data-ttu-id="f6ae0-112">Description</span><span class="sxs-lookup"><span data-stu-id="f6ae0-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="f6ae0-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="f6ae0-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="f6ae0-114">0</span><span class="sxs-lookup"><span data-stu-id="f6ae0-114">0</span></span>| <span data-ttu-id="f6ae0-115">La notification est toujours actif et persistante à l’intérieur du magasin de la plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="f6ae0-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="f6ae0-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="f6ae0-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="f6ae0-117">1</span><span class="sxs-lookup"><span data-stu-id="f6ae0-117">1</span></span>| <span data-ttu-id="f6ae0-118">La notification a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="f6ae0-118">The notification has been deleted.</span></span>|