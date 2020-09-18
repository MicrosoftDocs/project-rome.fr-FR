---
title: MCDConnectedDevicesNotificationType
description: En savoir plus sur l’énumération MCDConnectedDevicesNotificationType. Cette énumération contient des valeurs qui décrivent le type (service) d’une notification.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 5daf6db553df72a14a2cf201b4e974083eb7cf80
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761093"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="1c9a6-105">variables `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="1c9a6-105">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="1c9a6-106">Contient des valeurs qui décrivent le type (service) d’une notification.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-106">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="1c9a6-107">Champs</span><span class="sxs-lookup"><span data-stu-id="1c9a6-107">Fields</span></span>

| <span data-ttu-id="1c9a6-108">Nom</span><span class="sxs-lookup"><span data-stu-id="1c9a6-108">Name</span></span>                              |   <span data-ttu-id="1c9a6-109">Value</span><span class="sxs-lookup"><span data-stu-id="1c9a6-109">Value</span></span>     | <span data-ttu-id="1c9a6-110">Description</span><span class="sxs-lookup"><span data-stu-id="1c9a6-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="1c9a6-111">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="1c9a6-111">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="1c9a6-112">0</span><span class="sxs-lookup"><span data-stu-id="1c9a6-112">0</span></span> | <span data-ttu-id="1c9a6-113">ConnectedDevicesNotificationType est inconnu.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-113">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="1c9a6-114">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="1c9a6-114">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="1c9a6-115">1</span><span class="sxs-lookup"><span data-stu-id="1c9a6-115">1</span></span> | <span data-ttu-id="1c9a6-116">Notification Services Push Windows.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-116">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="1c9a6-117">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="1c9a6-117">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="1c9a6-118">2</span><span class="sxs-lookup"><span data-stu-id="1c9a6-118">2</span></span> | <span data-ttu-id="1c9a6-119">Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-119">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="1c9a6-120">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="1c9a6-120">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="1c9a6-121">3</span><span class="sxs-lookup"><span data-stu-id="1c9a6-121">3</span></span> | <span data-ttu-id="1c9a6-122">Firebase Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-122">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="1c9a6-123">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="1c9a6-123">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="1c9a6-124">4</span><span class="sxs-lookup"><span data-stu-id="1c9a6-124">4</span></span> | <span data-ttu-id="1c9a6-125">Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-125">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="1c9a6-126">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="1c9a6-126">MCDNotificationTypePolling</span></span> | <span data-ttu-id="1c9a6-127">5</span><span class="sxs-lookup"><span data-stu-id="1c9a6-127">5</span></span> | <span data-ttu-id="1c9a6-128">Aucun service de notification Cloud ; Interrogez plutôt les réponses entrantes.</span><span class="sxs-lookup"><span data-stu-id="1c9a6-128">No cloud notification service; instead poll for incoming responses.</span></span> |
