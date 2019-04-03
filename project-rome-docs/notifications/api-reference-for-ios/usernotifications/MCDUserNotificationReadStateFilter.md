---
title: MCDUserNotificationReadStateFilter
description: Contient des valeurs qui classent les notifications par état de lecture (pour la récupération de la notification filtré).
keywords: Microsoft, windows, les Notifications de graphique, iOS procédures, procédures iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907691"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="64cb6-104">Enum `MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="64cb6-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="64cb6-105">Contient des valeurs qui classent les notifications par état de lecture (pour la récupération de la notification filtré).</span><span class="sxs-lookup"><span data-stu-id="64cb6-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="64cb6-106">Nom</span><span class="sxs-lookup"><span data-stu-id="64cb6-106">Name</span></span> | <span data-ttu-id="64cb6-107">Value</span><span class="sxs-lookup"><span data-stu-id="64cb6-107">Value</span></span> | <span data-ttu-id="64cb6-108">Description</span><span class="sxs-lookup"><span data-stu-id="64cb6-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="64cb6-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="64cb6-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="64cb6-110">0</span><span class="sxs-lookup"><span data-stu-id="64cb6-110">0</span></span> | <span data-ttu-id="64cb6-111">Inclure des notifications, quel que soit l’état de lecture.</span><span class="sxs-lookup"><span data-stu-id="64cb6-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="64cb6-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="64cb6-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="64cb6-113">1</span><span class="sxs-lookup"><span data-stu-id="64cb6-113">1</span></span> | <span data-ttu-id="64cb6-114">Inclure les notifications ne sont pas lus.</span><span class="sxs-lookup"><span data-stu-id="64cb6-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="64cb6-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="64cb6-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="64cb6-116">2</span><span class="sxs-lookup"><span data-stu-id="64cb6-116">2</span></span> | <span data-ttu-id="64cb6-117">Inclure les notifications qui ont été lus.</span><span class="sxs-lookup"><span data-stu-id="64cb6-117">Include notifications that have been read.</span></span> |