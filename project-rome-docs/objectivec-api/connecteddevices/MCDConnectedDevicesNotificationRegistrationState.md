---
title: MCDConnectedDevicesNotificationRegistrationState
description: En savoir plus sur la classe MCDConnectedDevicesNotificationRegistrationState. Ces valeurs sont utilisées pour communiquer l’état de l’inscription du Cloud.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761113"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="abe24-105">type `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="abe24-105">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="abe24-106">Valeurs utilisées pour communiquer l’état de l’inscription du Cloud.</span><span class="sxs-lookup"><span data-stu-id="abe24-106">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="abe24-107">Champs</span><span class="sxs-lookup"><span data-stu-id="abe24-107">Fields</span></span>

| <span data-ttu-id="abe24-108">Nom</span><span class="sxs-lookup"><span data-stu-id="abe24-108">Name</span></span>                              |   <span data-ttu-id="abe24-109">Value</span><span class="sxs-lookup"><span data-stu-id="abe24-109">Value</span></span>     | <span data-ttu-id="abe24-110">Description</span><span class="sxs-lookup"><span data-stu-id="abe24-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="abe24-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="abe24-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="abe24-112">0</span><span class="sxs-lookup"><span data-stu-id="abe24-112">0</span></span> | <span data-ttu-id="abe24-113">L’inscription n’a jamais été démarrée.</span><span class="sxs-lookup"><span data-stu-id="abe24-113">Registration has never been started.</span></span>
| <span data-ttu-id="abe24-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="abe24-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="abe24-115">1</span><span class="sxs-lookup"><span data-stu-id="abe24-115">1</span></span> | <span data-ttu-id="abe24-116">L’inscription est terminée.</span><span class="sxs-lookup"><span data-stu-id="abe24-116">Registration has finished.</span></span> |
| <span data-ttu-id="abe24-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="abe24-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="abe24-118">2</span><span class="sxs-lookup"><span data-stu-id="abe24-118">2</span></span> | <span data-ttu-id="abe24-119">L’inscription est sur le point d’expirer et l’application doit donc réexécuter l’inscription.</span><span class="sxs-lookup"><span data-stu-id="abe24-119">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="abe24-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="abe24-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="abe24-121">3</span><span class="sxs-lookup"><span data-stu-id="abe24-121">3</span></span> | <span data-ttu-id="abe24-122">L’inscription a expiré et l’application doit à nouveau effectuer l’inscription.</span><span class="sxs-lookup"><span data-stu-id="abe24-122">Registration has expired and so the app must perform registration again.</span></span> |