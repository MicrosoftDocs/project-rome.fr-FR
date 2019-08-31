---
title: MCDUserNotificationStatusFilter
description: Contient des valeurs qui indiquent un filtre d’état de lecture lors de la création d’un lecteur de notifications. Cela détermine si l’application souhaite recevoir toutes les notifications, lire uniquement celles-ci ou uniquement celles qui n’ont pas été lues.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801491"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="48fb9-105">variables`MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="48fb9-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="48fb9-106">Contient des valeurs qui indiquent un filtre d’état de lecture lors de la création d’un lecteur de notifications.</span><span class="sxs-lookup"><span data-stu-id="48fb9-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="48fb9-107">Cela détermine si l’application souhaite recevoir toutes les notifications, lire uniquement celles-ci ou uniquement celles qui n’ont pas été lues.</span><span class="sxs-lookup"><span data-stu-id="48fb9-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="48fb9-108">Nom</span><span class="sxs-lookup"><span data-stu-id="48fb9-108">Name</span></span> | <span data-ttu-id="48fb9-109">Value</span><span class="sxs-lookup"><span data-stu-id="48fb9-109">Value</span></span> | <span data-ttu-id="48fb9-110">Description</span><span class="sxs-lookup"><span data-stu-id="48fb9-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="48fb9-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="48fb9-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="48fb9-112">0</span><span class="sxs-lookup"><span data-stu-id="48fb9-112">0</span></span>| <span data-ttu-id="48fb9-113">Inclut toutes les notifications indépendamment de la valeur d’État.</span><span class="sxs-lookup"><span data-stu-id="48fb9-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="48fb9-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="48fb9-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="48fb9-115">1</span><span class="sxs-lookup"><span data-stu-id="48fb9-115">1</span></span>| <span data-ttu-id="48fb9-116">Inclure les notifications actives et conservées dans le magasin de notifications de la plateforme des appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="48fb9-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="48fb9-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="48fb9-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="48fb9-118">2</span><span class="sxs-lookup"><span data-stu-id="48fb9-118">2</span></span>| <span data-ttu-id="48fb9-119">Inclut uniquement les notifications supprimées.</span><span class="sxs-lookup"><span data-stu-id="48fb9-119">Include deleted notifications only.</span></span>|