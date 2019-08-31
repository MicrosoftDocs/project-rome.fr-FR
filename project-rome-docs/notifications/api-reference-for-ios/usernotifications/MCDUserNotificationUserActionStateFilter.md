---
title: MCDUserNotificationUserActionStateFilter
description: Contient des valeurs qui classent les notifications par État d’action utilisateur (pour la récupération de notifications filtrées).
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800561"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="15bfb-104">variables`MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="15bfb-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="15bfb-105">Contient des valeurs qui classent les notifications par État d’action utilisateur (pour la récupération de notifications filtrées).</span><span class="sxs-lookup"><span data-stu-id="15bfb-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="15bfb-106">Name</span><span class="sxs-lookup"><span data-stu-id="15bfb-106">Name</span></span> | <span data-ttu-id="15bfb-107">Value</span><span class="sxs-lookup"><span data-stu-id="15bfb-107">Value</span></span> | <span data-ttu-id="15bfb-108">Description</span><span class="sxs-lookup"><span data-stu-id="15bfb-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="15bfb-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="15bfb-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="15bfb-110">0</span><span class="sxs-lookup"><span data-stu-id="15bfb-110">0</span></span>| <span data-ttu-id="15bfb-111">Inclure les notifications indépendamment de l’état de l’action de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bfb-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="15bfb-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="15bfb-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="15bfb-113">1</span><span class="sxs-lookup"><span data-stu-id="15bfb-113">1</span></span>| <span data-ttu-id="15bfb-114">Inclut les notifications qui n’ont pas été traitées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bfb-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="15bfb-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="15bfb-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="15bfb-116">2</span><span class="sxs-lookup"><span data-stu-id="15bfb-116">2</span></span>| <span data-ttu-id="15bfb-117">Inclut les notifications qui ont été activées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bfb-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="15bfb-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="15bfb-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="15bfb-119">3</span><span class="sxs-lookup"><span data-stu-id="15bfb-119">3</span></span>| <span data-ttu-id="15bfb-120">Inclut les notifications qui ont été ignorées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bfb-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="15bfb-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="15bfb-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="15bfb-122">4</span><span class="sxs-lookup"><span data-stu-id="15bfb-122">4</span></span>| <span data-ttu-id="15bfb-123">Inclut les notifications qui ont été répétées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bfb-123">Include notifications that have been snoozed by the user.</span></span>|