---
title: MCDUserNotificationUserActionState
description: Contient des valeurs décrivant l’action effectuée par un utilisateur sur une notification.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800801"
---
# <a name="enum-mcdusernotificationuseractionstate"></a><span data-ttu-id="30aa8-104">variables`MCDUserNotificationUserActionState`</span><span class="sxs-lookup"><span data-stu-id="30aa8-104">enum `MCDUserNotificationUserActionState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

<span data-ttu-id="30aa8-105">Contient des valeurs décrivant l’action effectuée par un utilisateur sur une notification.</span><span class="sxs-lookup"><span data-stu-id="30aa8-105">Contains values describing the action a user has taken on a notification.</span></span>

|<span data-ttu-id="30aa8-106">Nom</span><span class="sxs-lookup"><span data-stu-id="30aa8-106">Name</span></span> | <span data-ttu-id="30aa8-107">Value</span><span class="sxs-lookup"><span data-stu-id="30aa8-107">Value</span></span> | <span data-ttu-id="30aa8-108">Description</span><span class="sxs-lookup"><span data-stu-id="30aa8-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="30aa8-109">MCDUserNotificationUserActionStateNoInteraction</span><span class="sxs-lookup"><span data-stu-id="30aa8-109">MCDUserNotificationUserActionStateNoInteraction</span></span> |<span data-ttu-id="30aa8-110">0</span><span class="sxs-lookup"><span data-stu-id="30aa8-110">0</span></span>| <span data-ttu-id="30aa8-111">L’utilisateur n’a pris aucune mesure.</span><span class="sxs-lookup"><span data-stu-id="30aa8-111">The user hasn't taken any action.</span></span>|
|   <span data-ttu-id="30aa8-112">MCDUserNotificationUserActionStateActivated</span><span class="sxs-lookup"><span data-stu-id="30aa8-112">MCDUserNotificationUserActionStateActivated</span></span>|<span data-ttu-id="30aa8-113">1</span><span class="sxs-lookup"><span data-stu-id="30aa8-113">1</span></span>|<span data-ttu-id="30aa8-114">L’utilisateur a activé la notification.</span><span class="sxs-lookup"><span data-stu-id="30aa8-114">The user has activated the notification.</span></span>|
|   <span data-ttu-id="30aa8-115">MCDUserNotificationUserActionStateDismissed</span><span class="sxs-lookup"><span data-stu-id="30aa8-115">MCDUserNotificationUserActionStateDismissed</span></span>|<span data-ttu-id="30aa8-116">2</span><span class="sxs-lookup"><span data-stu-id="30aa8-116">2</span></span>| <span data-ttu-id="30aa8-117">L’utilisateur a rejeté la notification.</span><span class="sxs-lookup"><span data-stu-id="30aa8-117">The user has dismissed the notification.</span></span>|
|   <span data-ttu-id="30aa8-118">MCDUserNotificationUserActionStateSnoozed</span><span class="sxs-lookup"><span data-stu-id="30aa8-118">MCDUserNotificationUserActionStateSnoozed</span></span>|<span data-ttu-id="30aa8-119">3</span><span class="sxs-lookup"><span data-stu-id="30aa8-119">3</span></span>| <span data-ttu-id="30aa8-120">L’utilisateur a répété la notification.</span><span class="sxs-lookup"><span data-stu-id="30aa8-120">The user has snoozed the notification.</span></span>|
