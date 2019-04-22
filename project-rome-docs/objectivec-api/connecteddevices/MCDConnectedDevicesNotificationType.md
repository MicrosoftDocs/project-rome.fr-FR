---
title: MCDConnectedDevicesNotificationType
description: Contient des valeurs qui décrivent le type (service) d’une notification.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801691"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="d6195-104">Enum `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="d6195-104">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="d6195-105">Contient des valeurs qui décrivent le type (service) d’une notification.</span><span class="sxs-lookup"><span data-stu-id="d6195-105">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="d6195-106">Champs</span><span class="sxs-lookup"><span data-stu-id="d6195-106">Fields</span></span>

| <span data-ttu-id="d6195-107">Nom</span><span class="sxs-lookup"><span data-stu-id="d6195-107">Name</span></span>                              |   <span data-ttu-id="d6195-108">Value</span><span class="sxs-lookup"><span data-stu-id="d6195-108">Value</span></span>     | <span data-ttu-id="d6195-109">Description</span><span class="sxs-lookup"><span data-stu-id="d6195-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="d6195-110">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="d6195-110">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="d6195-111">0</span><span class="sxs-lookup"><span data-stu-id="d6195-111">0</span></span> | <span data-ttu-id="d6195-112">ConnectedDevicesNotificationType est inconnu.</span><span class="sxs-lookup"><span data-stu-id="d6195-112">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="d6195-113">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="d6195-113">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="d6195-114">1</span><span class="sxs-lookup"><span data-stu-id="d6195-114">1</span></span> | <span data-ttu-id="d6195-115">Services de notifications Push Windows.</span><span class="sxs-lookup"><span data-stu-id="d6195-115">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="d6195-116">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="d6195-116">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="d6195-117">2</span><span class="sxs-lookup"><span data-stu-id="d6195-117">2</span></span> | <span data-ttu-id="d6195-118">Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="d6195-118">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="d6195-119">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="d6195-119">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="d6195-120">3</span><span class="sxs-lookup"><span data-stu-id="d6195-120">3</span></span> | <span data-ttu-id="d6195-121">Firebase Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="d6195-121">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="d6195-122">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="d6195-122">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="d6195-123">4</span><span class="sxs-lookup"><span data-stu-id="d6195-123">4</span></span> | <span data-ttu-id="d6195-124">Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="d6195-124">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="d6195-125">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="d6195-125">MCDNotificationTypePolling</span></span> | <span data-ttu-id="d6195-126">5</span><span class="sxs-lookup"><span data-stu-id="d6195-126">5</span></span> | <span data-ttu-id="d6195-127">Aucun service de notification cloud ; interroger à la place pour les réponses entrantes.</span><span class="sxs-lookup"><span data-stu-id="d6195-127">No cloud notification service; instead poll for incoming responses.</span></span> |
