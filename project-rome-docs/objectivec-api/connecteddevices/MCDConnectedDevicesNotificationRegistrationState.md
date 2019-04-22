---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valeurs utilisées pour communiquer l’état de l’inscription du cloud.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800711"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="28b45-104">Classe `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="28b45-104">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="28b45-105">Valeurs utilisées pour communiquer l’état de l’inscription du cloud.</span><span class="sxs-lookup"><span data-stu-id="28b45-105">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="28b45-106">Champs</span><span class="sxs-lookup"><span data-stu-id="28b45-106">Fields</span></span>

| <span data-ttu-id="28b45-107">Nom</span><span class="sxs-lookup"><span data-stu-id="28b45-107">Name</span></span>                              |   <span data-ttu-id="28b45-108">Value</span><span class="sxs-lookup"><span data-stu-id="28b45-108">Value</span></span>     | <span data-ttu-id="28b45-109">Description</span><span class="sxs-lookup"><span data-stu-id="28b45-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="28b45-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="28b45-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="28b45-111">0</span><span class="sxs-lookup"><span data-stu-id="28b45-111">0</span></span> | <span data-ttu-id="28b45-112">L’inscription n’a jamais été démarrée.</span><span class="sxs-lookup"><span data-stu-id="28b45-112">Registration has never been started.</span></span>
| <span data-ttu-id="28b45-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="28b45-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="28b45-114">1</span><span class="sxs-lookup"><span data-stu-id="28b45-114">1</span></span> | <span data-ttu-id="28b45-115">L’inscription est terminée.</span><span class="sxs-lookup"><span data-stu-id="28b45-115">Registration has finished.</span></span> |
| <span data-ttu-id="28b45-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="28b45-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="28b45-117">2</span><span class="sxs-lookup"><span data-stu-id="28b45-117">2</span></span> | <span data-ttu-id="28b45-118">L’inscription est sur le point d’expirer et par conséquent, l’application doit effectuer à nouveau l’inscription.</span><span class="sxs-lookup"><span data-stu-id="28b45-118">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="28b45-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="28b45-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="28b45-120">3</span><span class="sxs-lookup"><span data-stu-id="28b45-120">3</span></span> | <span data-ttu-id="28b45-121">L’inscription a expiré et par conséquent, l’application doit effectuer à nouveau l’inscription.</span><span class="sxs-lookup"><span data-stu-id="28b45-121">Registration has expired and so the app must perform registration again.</span></span> |