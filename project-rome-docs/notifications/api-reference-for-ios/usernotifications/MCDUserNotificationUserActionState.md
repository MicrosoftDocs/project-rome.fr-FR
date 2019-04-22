---
title: MCDUserNotificationUserActionState
description: Contient des valeurs qui décrivent l’action de qu'un utilisateur a effectuées sur une notification.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800801"
---
# <a name="enum-mcdusernotificationuseractionstate"></a><span data-ttu-id="f0226-104">Enum `MCDUserNotificationUserActionState`</span><span class="sxs-lookup"><span data-stu-id="f0226-104">enum `MCDUserNotificationUserActionState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

<span data-ttu-id="f0226-105">Contient des valeurs qui décrivent l’action de qu'un utilisateur a effectuées sur une notification.</span><span class="sxs-lookup"><span data-stu-id="f0226-105">Contains values describing the action a user has taken on a notification.</span></span>

|<span data-ttu-id="f0226-106">Nom</span><span class="sxs-lookup"><span data-stu-id="f0226-106">Name</span></span> | <span data-ttu-id="f0226-107">Value</span><span class="sxs-lookup"><span data-stu-id="f0226-107">Value</span></span> | <span data-ttu-id="f0226-108">Description</span><span class="sxs-lookup"><span data-stu-id="f0226-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="f0226-109">MCDUserNotificationUserActionStateNoInteraction</span><span class="sxs-lookup"><span data-stu-id="f0226-109">MCDUserNotificationUserActionStateNoInteraction</span></span> |<span data-ttu-id="f0226-110">0</span><span class="sxs-lookup"><span data-stu-id="f0226-110">0</span></span>| <span data-ttu-id="f0226-111">L’utilisateur n’a pas encore pris aucune action.</span><span class="sxs-lookup"><span data-stu-id="f0226-111">The user hasn't taken any action.</span></span>|
|   <span data-ttu-id="f0226-112">MCDUserNotificationUserActionStateActivated</span><span class="sxs-lookup"><span data-stu-id="f0226-112">MCDUserNotificationUserActionStateActivated</span></span>|<span data-ttu-id="f0226-113">1</span><span class="sxs-lookup"><span data-stu-id="f0226-113">1</span></span>|<span data-ttu-id="f0226-114">L’utilisateur a activé la notification.</span><span class="sxs-lookup"><span data-stu-id="f0226-114">The user has activated the notification.</span></span>|
|   <span data-ttu-id="f0226-115">MCDUserNotificationUserActionStateDismissed</span><span class="sxs-lookup"><span data-stu-id="f0226-115">MCDUserNotificationUserActionStateDismissed</span></span>|<span data-ttu-id="f0226-116">2</span><span class="sxs-lookup"><span data-stu-id="f0226-116">2</span></span>| <span data-ttu-id="f0226-117">L’utilisateur a fermé la notification.</span><span class="sxs-lookup"><span data-stu-id="f0226-117">The user has dismissed the notification.</span></span>|
|   <span data-ttu-id="f0226-118">MCDUserNotificationUserActionStateSnoozed</span><span class="sxs-lookup"><span data-stu-id="f0226-118">MCDUserNotificationUserActionStateSnoozed</span></span>|<span data-ttu-id="f0226-119">3</span><span class="sxs-lookup"><span data-stu-id="f0226-119">3</span></span>| <span data-ttu-id="f0226-120">L’utilisateur a répété la notification.</span><span class="sxs-lookup"><span data-stu-id="f0226-120">The user has snoozed the notification.</span></span>|
