---
title: MCDUserNotificationStatusFilter
description: Contient des valeurs qui indique un filtre d’état de lecture lors de la création d’un lecteur de notification. Ce paramètre détermine si l’application souhaite recevoir toutes les notifications, lire uniquement, ou uniquement ceux qui sont lus.
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801491"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="c8c3e-105">Enum `MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="c8c3e-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="c8c3e-106">Contient des valeurs qui indique un filtre d’état de lecture lors de la création d’un lecteur de notification.</span><span class="sxs-lookup"><span data-stu-id="c8c3e-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="c8c3e-107">Ce paramètre détermine si l’application souhaite recevoir toutes les notifications, lire uniquement, ou uniquement ceux qui sont lus.</span><span class="sxs-lookup"><span data-stu-id="c8c3e-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="c8c3e-108">Nom</span><span class="sxs-lookup"><span data-stu-id="c8c3e-108">Name</span></span> | <span data-ttu-id="c8c3e-109">Value</span><span class="sxs-lookup"><span data-stu-id="c8c3e-109">Value</span></span> | <span data-ttu-id="c8c3e-110">Description</span><span class="sxs-lookup"><span data-stu-id="c8c3e-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="c8c3e-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="c8c3e-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="c8c3e-112">0</span><span class="sxs-lookup"><span data-stu-id="c8c3e-112">0</span></span>| <span data-ttu-id="c8c3e-113">Inclure toutes les notifications, quel que soit la valeur d’état.</span><span class="sxs-lookup"><span data-stu-id="c8c3e-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="c8c3e-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="c8c3e-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="c8c3e-115">1</span><span class="sxs-lookup"><span data-stu-id="c8c3e-115">1</span></span>| <span data-ttu-id="c8c3e-116">Inclure les notifications qui sont actifs et persistante dans le magasin de notification de plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="c8c3e-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="c8c3e-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="c8c3e-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="c8c3e-118">2</span><span class="sxs-lookup"><span data-stu-id="c8c3e-118">2</span></span>| <span data-ttu-id="c8c3e-119">Inclure uniquement les notifications supprimées.</span><span class="sxs-lookup"><span data-stu-id="c8c3e-119">Include deleted notifications only.</span></span>|