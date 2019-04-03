---
title: MCDAppServiceClosedStatus
description: Contient des valeurs qui décrivent une connexion fermée à un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907721"
---
# <a name="enum-mcdappserviceclosedstatus"></a><span data-ttu-id="db703-104">Enum `MCDAppServiceClosedStatus`</span><span class="sxs-lookup"><span data-stu-id="db703-104">enum `MCDAppServiceClosedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

<span data-ttu-id="db703-105">Contient des valeurs qui décrivent une connexion fermée à un service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="db703-105">Contains values that describe a closed connection to a remote app service.</span></span>

|<span data-ttu-id="db703-106">Membre</span><span class="sxs-lookup"><span data-stu-id="db703-106">Member</span></span>   |<span data-ttu-id="db703-107">Value</span><span class="sxs-lookup"><span data-stu-id="db703-107">Value</span></span>   |<span data-ttu-id="db703-108">Description</span><span class="sxs-lookup"><span data-stu-id="db703-108">Description</span></span>   |
|--------|-------|-------------|
|<span data-ttu-id="db703-109">MCDAppServiceClosedStatusCompleted</span><span class="sxs-lookup"><span data-stu-id="db703-109">MCDAppServiceClosedStatusCompleted</span></span> |<span data-ttu-id="db703-110">0</span><span class="sxs-lookup"><span data-stu-id="db703-110">0</span></span>| <span data-ttu-id="db703-111">Le point de terminaison pour le service d’application a été fermée correctement.</span><span class="sxs-lookup"><span data-stu-id="db703-111">The endpoint for the app service closed gracefully.</span></span>|
|<span data-ttu-id="db703-112">MCDAppServiceClosedStatusCanceled</span><span class="sxs-lookup"><span data-stu-id="db703-112">MCDAppServiceClosedStatusCanceled</span></span> |<span data-ttu-id="db703-113">1</span><span class="sxs-lookup"><span data-stu-id="db703-113">1</span></span>| <span data-ttu-id="db703-114">Le point de terminaison pour le service d’application a été fermée par le client ou le système.</span><span class="sxs-lookup"><span data-stu-id="db703-114">The endpoint for the app service was closed by the client or the system.</span></span>|
|<span data-ttu-id="db703-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="db703-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="db703-116">2</span><span class="sxs-lookup"><span data-stu-id="db703-116">2</span></span>| <span data-ttu-id="db703-117">Le point de terminaison pour le service d’application a été fermée, car le point de terminaison a manqué de ressources.</span><span class="sxs-lookup"><span data-stu-id="db703-117">The endpoint for the app service was closed because the endpoint ran out of resources.</span></span>|
|<span data-ttu-id="db703-118">MCDAppServiceClosedStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="db703-118">MCDAppServiceClosedStatusUnknown</span></span> |<span data-ttu-id="db703-119">3</span><span class="sxs-lookup"><span data-stu-id="db703-119">3</span></span>| <span data-ttu-id="db703-120">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db703-120">An unknown error occurred.</span></span>|