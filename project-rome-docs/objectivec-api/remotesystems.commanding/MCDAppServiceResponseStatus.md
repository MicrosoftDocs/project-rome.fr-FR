---
title: MCDAppServiceResponseStatus
description: Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800331"
---
# <a name="enum-mcdappserviceresponsestatus"></a><span data-ttu-id="be8b5-104">Enum `MCDAppServiceResponseStatus`</span><span class="sxs-lookup"><span data-stu-id="be8b5-104">enum `MCDAppServiceResponseStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

<span data-ttu-id="be8b5-105">Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="be8b5-105">Contains values that describe the status of a response message from a remote app service.</span></span>

|<span data-ttu-id="be8b5-106">Nom</span><span class="sxs-lookup"><span data-stu-id="be8b5-106">Name</span></span>         | <span data-ttu-id="be8b5-107">Value</span><span class="sxs-lookup"><span data-stu-id="be8b5-107">Value</span></span>  | <span data-ttu-id="be8b5-108">Description</span><span class="sxs-lookup"><span data-stu-id="be8b5-108">Description</span></span>    |                           
|--------|-------------|-----|
|<span data-ttu-id="be8b5-109">MCDAppServiceResponseStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="be8b5-109">MCDAppServiceResponseStatusSuccess</span></span> |<span data-ttu-id="be8b5-110">0</span><span class="sxs-lookup"><span data-stu-id="be8b5-110">0</span></span>| <span data-ttu-id="be8b5-111">Le service d’application correctement reçu et traité le message.</span><span class="sxs-lookup"><span data-stu-id="be8b5-111">The app service successfully received and processed the message.</span></span>|
|<span data-ttu-id="be8b5-112">MCDAppServiceResponseStatusFailure</span><span class="sxs-lookup"><span data-stu-id="be8b5-112">MCDAppServiceResponseStatusFailure</span></span> |<span data-ttu-id="be8b5-113">1</span><span class="sxs-lookup"><span data-stu-id="be8b5-113">1</span></span>| <span data-ttu-id="be8b5-114">Échec de l’app service recevoir et traiter le message.</span><span class="sxs-lookup"><span data-stu-id="be8b5-114">The app service failed to receive and process the message.</span></span>|
|<span data-ttu-id="be8b5-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="be8b5-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="be8b5-116">2</span><span class="sxs-lookup"><span data-stu-id="be8b5-116">2</span></span>| <span data-ttu-id="be8b5-117">Le service d’application s’est arrêté car pas suffisamment de ressources n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="be8b5-117">The app service exited because not enough resources were available.</span></span>|
|<span data-ttu-id="be8b5-118">MCDAppServiceResponseStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="be8b5-118">MCDAppServiceResponseStatusUnknown</span></span> |<span data-ttu-id="be8b5-119">3</span><span class="sxs-lookup"><span data-stu-id="be8b5-119">3</span></span>| <span data-ttu-id="be8b5-120">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="be8b5-120">An unknown error occurred.</span></span>|
|<span data-ttu-id="be8b5-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="be8b5-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span></span> |<span data-ttu-id="be8b5-122">4</span><span class="sxs-lookup"><span data-stu-id="be8b5-122">4</span></span>| <span data-ttu-id="be8b5-123">L’appareil auquel le message a été envoyé n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="be8b5-123">The device to which the message was sent is not available.</span></span>|
|<span data-ttu-id="be8b5-124">MCDAppServiceResponseStatusMessageTooLarge</span><span class="sxs-lookup"><span data-stu-id="be8b5-124">MCDAppServiceResponseStatusMessageTooLarge</span></span> |<span data-ttu-id="be8b5-125">5</span><span class="sxs-lookup"><span data-stu-id="be8b5-125">5</span></span>| <span data-ttu-id="be8b5-126">Le service de l’application a échoué traiter le message, car il est trop volumineux.</span><span class="sxs-lookup"><span data-stu-id="be8b5-126">The app service failed to process the message because it is too large.</span></span>|
|<span data-ttu-id="be8b5-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="be8b5-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span></span>|<span data-ttu-id="be8b5-128">6</span><span class="sxs-lookup"><span data-stu-id="be8b5-128">6</span></span>| <span data-ttu-id="be8b5-129">La connexion de service d’application a été fermée avant une réponse a été envoyée.</span><span class="sxs-lookup"><span data-stu-id="be8b5-129">The app service connection was closed before a response was sent.</span></span>|