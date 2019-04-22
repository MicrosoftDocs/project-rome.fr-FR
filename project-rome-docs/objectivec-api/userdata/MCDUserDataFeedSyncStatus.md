---
title: MCDUserDataSyncStatus
description: Contient des valeurs qui décrivent l’état d’un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de synchronisation avec le backend de la plateforme de périphériques connectés.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801411"
---
# <a name="enum-mcduserdatasyncstatus"></a><span data-ttu-id="10f09-104">Enum `MCDUserDataSyncStatus`</span><span class="sxs-lookup"><span data-stu-id="10f09-104">enum `MCDUserDataSyncStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

<span data-ttu-id="10f09-105">Contient des valeurs qui décrivent l’état d’un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de synchronisation avec le backend de la plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="10f09-105">Contains values that describe the state of a **[MCDUserDataFeed](MCDUserDataFeed.md)**'s synchronization with the Connected Devices Platform backend.</span></span>

|<span data-ttu-id="10f09-106">Nom</span><span class="sxs-lookup"><span data-stu-id="10f09-106">Name</span></span> | <span data-ttu-id="10f09-107">Value</span><span class="sxs-lookup"><span data-stu-id="10f09-107">Value</span></span> | <span data-ttu-id="10f09-108">Description</span><span class="sxs-lookup"><span data-stu-id="10f09-108">Description</span></span> |
|:-- |:-- |:-- |
|  <span data-ttu-id="10f09-109">MCDUserDataFeedSyncStatusQueued</span><span class="sxs-lookup"><span data-stu-id="10f09-109">MCDUserDataFeedSyncStatusQueued</span></span> |<span data-ttu-id="10f09-110">0</span><span class="sxs-lookup"><span data-stu-id="10f09-110">0</span></span>| <span data-ttu-id="10f09-111">Les données ne sont pas encore synchronisées.</span><span class="sxs-lookup"><span data-stu-id="10f09-111">The data is not yet synchronized.</span></span> |
| <span data-ttu-id="10f09-112">MCDUserDataFeedSyncStatusSynchronized</span><span class="sxs-lookup"><span data-stu-id="10f09-112">MCDUserDataFeedSyncStatusSynchronized</span></span> |<span data-ttu-id="10f09-113">1</span><span class="sxs-lookup"><span data-stu-id="10f09-113">1</span></span>| <span data-ttu-id="10f09-114">Les données ont été synchronisées.</span><span class="sxs-lookup"><span data-stu-id="10f09-114">The data has been synchronized.</span></span>|