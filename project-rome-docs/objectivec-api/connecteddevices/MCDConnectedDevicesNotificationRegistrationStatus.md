---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: Valeurs utilisées pour communiquer l’état de l’inscription du cloud.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909131"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a><span data-ttu-id="b6007-104">Classe `MCDConnectedDevicesNotificationRegistrationStatus`</span><span class="sxs-lookup"><span data-stu-id="b6007-104">class `MCDConnectedDevicesNotificationRegistrationStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
<span data-ttu-id="b6007-105">Énumération indiquant l’état de l’opération d’inscription.</span><span class="sxs-lookup"><span data-stu-id="b6007-105">Enumeration indicating the status of the registration operation.</span></span>
<span data-ttu-id="b6007-106">Les États d’erreur indiquent des conditions transitoires où le développeur d’applications peut souhaitez réessayer l’inscription.</span><span class="sxs-lookup"><span data-stu-id="b6007-106">The error statuses indicate transient conditions where the app developer may want to retry registration.</span></span>

## <a name="fields"></a><span data-ttu-id="b6007-107">Champs</span><span class="sxs-lookup"><span data-stu-id="b6007-107">Fields</span></span>

| <span data-ttu-id="b6007-108">Nom</span><span class="sxs-lookup"><span data-stu-id="b6007-108">Name</span></span>                              |   <span data-ttu-id="b6007-109">Value</span><span class="sxs-lookup"><span data-stu-id="b6007-109">Value</span></span>     | <span data-ttu-id="b6007-110">Description</span><span class="sxs-lookup"><span data-stu-id="b6007-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="b6007-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="b6007-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span></span> | <span data-ttu-id="b6007-112">0</span><span class="sxs-lookup"><span data-stu-id="b6007-112">0</span></span> | <span data-ttu-id="b6007-113">Opération achevée avec succès.</span><span class="sxs-lookup"><span data-stu-id="b6007-113">Operation completed successfully.</span></span>
| <span data-ttu-id="b6007-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="b6007-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span></span> | <span data-ttu-id="b6007-115">1</span><span class="sxs-lookup"><span data-stu-id="b6007-115">1</span></span> | <span data-ttu-id="b6007-116">Réseau n’était pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b6007-116">Network was unavailable.</span></span> |
| <span data-ttu-id="b6007-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="b6007-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span></span> | <span data-ttu-id="b6007-118">2</span><span class="sxs-lookup"><span data-stu-id="b6007-118">2</span></span> | <span data-ttu-id="b6007-119">Échec d’un service web.</span><span class="sxs-lookup"><span data-stu-id="b6007-119">A web service failed.</span></span> |
| <span data-ttu-id="b6007-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="b6007-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="b6007-121">3</span><span class="sxs-lookup"><span data-stu-id="b6007-121">3</span></span> | <span data-ttu-id="b6007-122">Aucun abonné demande de jeton a répondu.</span><span class="sxs-lookup"><span data-stu-id="b6007-122">No token request subscribers responded.</span></span> |
| <span data-ttu-id="b6007-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="b6007-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="b6007-124">4</span><span class="sxs-lookup"><span data-stu-id="b6007-124">4</span></span> | <span data-ttu-id="b6007-125">Échec de la demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="b6007-125">The token request failed.</span></span> |
| <span data-ttu-id="b6007-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="b6007-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span></span> | <span data-ttu-id="b6007-127">5</span><span class="sxs-lookup"><span data-stu-id="b6007-127">5</span></span> | <span data-ttu-id="b6007-128">Impossible de trouver le compte pour inscrire les informations pour.</span><span class="sxs-lookup"><span data-stu-id="b6007-128">Account to register information for was not found.</span></span> |
| <span data-ttu-id="b6007-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="b6007-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span></span> | <span data-ttu-id="b6007-130">6</span><span class="sxs-lookup"><span data-stu-id="b6007-130">6</span></span> | <span data-ttu-id="b6007-131">Opération a rencontré une erreur inconnue.</span><span class="sxs-lookup"><span data-stu-id="b6007-131">Operation encountered an unknown error.</span></span> |