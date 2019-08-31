---
title: MCDUserNotificationReadStateFilter
description: Contient des valeurs qui classent les notifications par État de lecture (pour la récupération filtrée des notifications).
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801341"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="f97f4-104">variables`MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="f97f4-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="f97f4-105">Contient des valeurs qui classent les notifications par État de lecture (pour la récupération filtrée des notifications).</span><span class="sxs-lookup"><span data-stu-id="f97f4-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="f97f4-106">Name</span><span class="sxs-lookup"><span data-stu-id="f97f4-106">Name</span></span> | <span data-ttu-id="f97f4-107">Value</span><span class="sxs-lookup"><span data-stu-id="f97f4-107">Value</span></span> | <span data-ttu-id="f97f4-108">Description</span><span class="sxs-lookup"><span data-stu-id="f97f4-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="f97f4-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="f97f4-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="f97f4-110">0</span><span class="sxs-lookup"><span data-stu-id="f97f4-110">0</span></span> | <span data-ttu-id="f97f4-111">Inclure les notifications indépendamment de l’état de lecture.</span><span class="sxs-lookup"><span data-stu-id="f97f4-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="f97f4-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="f97f4-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="f97f4-113">1</span><span class="sxs-lookup"><span data-stu-id="f97f4-113">1</span></span> | <span data-ttu-id="f97f4-114">Incluez les notifications qui n’ont pas été lues.</span><span class="sxs-lookup"><span data-stu-id="f97f4-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="f97f4-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="f97f4-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="f97f4-116">2</span><span class="sxs-lookup"><span data-stu-id="f97f4-116">2</span></span> | <span data-ttu-id="f97f4-117">Inclut les notifications qui ont été lues.</span><span class="sxs-lookup"><span data-stu-id="f97f4-117">Include notifications that have been read.</span></span> |