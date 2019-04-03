---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valeurs utilisées pour communiquer l’état de l’inscription du cloud.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909231"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="f7c6f-104">Classe `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="f7c6f-104">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="f7c6f-105">Valeurs utilisées pour communiquer l’état de l’inscription du cloud.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-105">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="f7c6f-106">Champs</span><span class="sxs-lookup"><span data-stu-id="f7c6f-106">Fields</span></span>

| <span data-ttu-id="f7c6f-107">Nom</span><span class="sxs-lookup"><span data-stu-id="f7c6f-107">Name</span></span>                              |   <span data-ttu-id="f7c6f-108">Value</span><span class="sxs-lookup"><span data-stu-id="f7c6f-108">Value</span></span>     | <span data-ttu-id="f7c6f-109">Description</span><span class="sxs-lookup"><span data-stu-id="f7c6f-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="f7c6f-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="f7c6f-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="f7c6f-111">0</span><span class="sxs-lookup"><span data-stu-id="f7c6f-111">0</span></span> | <span data-ttu-id="f7c6f-112">L’inscription n’a jamais été démarrée.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-112">Registration has never been started.</span></span>
| <span data-ttu-id="f7c6f-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="f7c6f-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="f7c6f-114">1</span><span class="sxs-lookup"><span data-stu-id="f7c6f-114">1</span></span> | <span data-ttu-id="f7c6f-115">L’inscription est terminée.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-115">Registration has finished.</span></span> |
| <span data-ttu-id="f7c6f-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="f7c6f-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="f7c6f-117">2</span><span class="sxs-lookup"><span data-stu-id="f7c6f-117">2</span></span> | <span data-ttu-id="f7c6f-118">L’inscription est sur le point d’expirer et par conséquent, l’application doit effectuer à nouveau l’inscription.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-118">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="f7c6f-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="f7c6f-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="f7c6f-120">3</span><span class="sxs-lookup"><span data-stu-id="f7c6f-120">3</span></span> | <span data-ttu-id="f7c6f-121">L’inscription a expiré et par conséquent, l’application doit effectuer à nouveau l’inscription.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-121">Registration has expired and so the app must perform registration again.</span></span> |