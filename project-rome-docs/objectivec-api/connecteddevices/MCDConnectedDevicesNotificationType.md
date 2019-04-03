---
title: MCDConnectedDevicesNotificationType
description: Contient des valeurs qui décrivent le type (service) d’une notification.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909481"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="52b7d-104">Enum `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="52b7d-104">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="52b7d-105">Contient des valeurs qui décrivent le type (service) d’une notification.</span><span class="sxs-lookup"><span data-stu-id="52b7d-105">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="52b7d-106">Champs</span><span class="sxs-lookup"><span data-stu-id="52b7d-106">Fields</span></span>

| <span data-ttu-id="52b7d-107">Nom</span><span class="sxs-lookup"><span data-stu-id="52b7d-107">Name</span></span>                              |   <span data-ttu-id="52b7d-108">Value</span><span class="sxs-lookup"><span data-stu-id="52b7d-108">Value</span></span>     | <span data-ttu-id="52b7d-109">Description</span><span class="sxs-lookup"><span data-stu-id="52b7d-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="52b7d-110">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="52b7d-110">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="52b7d-111">0</span><span class="sxs-lookup"><span data-stu-id="52b7d-111">0</span></span> | <span data-ttu-id="52b7d-112">ConnectedDevicesNotificationType est inconnu.</span><span class="sxs-lookup"><span data-stu-id="52b7d-112">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="52b7d-113">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="52b7d-113">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="52b7d-114">1</span><span class="sxs-lookup"><span data-stu-id="52b7d-114">1</span></span> | <span data-ttu-id="52b7d-115">Services de notifications Push Windows.</span><span class="sxs-lookup"><span data-stu-id="52b7d-115">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="52b7d-116">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="52b7d-116">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="52b7d-117">2</span><span class="sxs-lookup"><span data-stu-id="52b7d-117">2</span></span> | <span data-ttu-id="52b7d-118">Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="52b7d-118">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="52b7d-119">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="52b7d-119">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="52b7d-120">3</span><span class="sxs-lookup"><span data-stu-id="52b7d-120">3</span></span> | <span data-ttu-id="52b7d-121">Firebase Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="52b7d-121">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="52b7d-122">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="52b7d-122">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="52b7d-123">4</span><span class="sxs-lookup"><span data-stu-id="52b7d-123">4</span></span> | <span data-ttu-id="52b7d-124">Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="52b7d-124">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="52b7d-125">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="52b7d-125">MCDNotificationTypePolling</span></span> | <span data-ttu-id="52b7d-126">5</span><span class="sxs-lookup"><span data-stu-id="52b7d-126">5</span></span> | <span data-ttu-id="52b7d-127">Aucun service de notification cloud ; interroger à la place pour les réponses entrantes.</span><span class="sxs-lookup"><span data-stu-id="52b7d-127">No cloud notification service; instead poll for incoming responses.</span></span> |
