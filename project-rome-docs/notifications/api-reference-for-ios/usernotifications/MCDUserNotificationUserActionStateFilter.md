---
title: MCDUserNotificationUserActionStateFilter
description: Contient des valeurs qui classent les notifications par état d’action utilisateur (pour la récupération de la notification filtré).
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800561"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="8633f-104">Enum `MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="8633f-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="8633f-105">Contient des valeurs qui classent les notifications par état d’action utilisateur (pour la récupération de la notification filtré).</span><span class="sxs-lookup"><span data-stu-id="8633f-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="8633f-106">Nom</span><span class="sxs-lookup"><span data-stu-id="8633f-106">Name</span></span> | <span data-ttu-id="8633f-107">Value</span><span class="sxs-lookup"><span data-stu-id="8633f-107">Value</span></span> | <span data-ttu-id="8633f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8633f-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="8633f-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="8633f-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="8633f-110">0</span><span class="sxs-lookup"><span data-stu-id="8633f-110">0</span></span>| <span data-ttu-id="8633f-111">Inclure des notifications, quel que soit l’état d’action utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8633f-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="8633f-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="8633f-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="8633f-113">1</span><span class="sxs-lookup"><span data-stu-id="8633f-113">1</span></span>| <span data-ttu-id="8633f-114">Inclure des notifications qui n’ont pas été affrontées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8633f-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="8633f-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="8633f-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="8633f-116">2</span><span class="sxs-lookup"><span data-stu-id="8633f-116">2</span></span>| <span data-ttu-id="8633f-117">Inclure les notifications qui ont été activées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8633f-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="8633f-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="8633f-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="8633f-119">3</span><span class="sxs-lookup"><span data-stu-id="8633f-119">3</span></span>| <span data-ttu-id="8633f-120">Inclure les notifications qui ont été ignorées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8633f-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="8633f-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="8633f-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="8633f-122">4</span><span class="sxs-lookup"><span data-stu-id="8633f-122">4</span></span>| <span data-ttu-id="8633f-123">Inclure les notifications qui ont été répétées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8633f-123">Include notifications that have been snoozed by the user.</span></span>|