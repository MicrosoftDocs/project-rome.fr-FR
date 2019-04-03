---
title: MCDAppServiceResponseStatus
description: Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908941"
---
# <a name="enum-mcdappserviceresponsestatus"></a><span data-ttu-id="48523-104">Enum `MCDAppServiceResponseStatus`</span><span class="sxs-lookup"><span data-stu-id="48523-104">enum `MCDAppServiceResponseStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

<span data-ttu-id="48523-105">Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="48523-105">Contains values that describe the status of a response message from a remote app service.</span></span>

|<span data-ttu-id="48523-106">Nom</span><span class="sxs-lookup"><span data-stu-id="48523-106">Name</span></span>         | <span data-ttu-id="48523-107">Value</span><span class="sxs-lookup"><span data-stu-id="48523-107">Value</span></span>  | <span data-ttu-id="48523-108">Description</span><span class="sxs-lookup"><span data-stu-id="48523-108">Description</span></span>    |                           
|--------|-------------|-----|
|<span data-ttu-id="48523-109">MCDAppServiceResponseStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="48523-109">MCDAppServiceResponseStatusSuccess</span></span> |<span data-ttu-id="48523-110">0</span><span class="sxs-lookup"><span data-stu-id="48523-110">0</span></span>| <span data-ttu-id="48523-111">Le service d’application correctement reçu et traité le message.</span><span class="sxs-lookup"><span data-stu-id="48523-111">The app service successfully received and processed the message.</span></span>|
|<span data-ttu-id="48523-112">MCDAppServiceResponseStatusFailure</span><span class="sxs-lookup"><span data-stu-id="48523-112">MCDAppServiceResponseStatusFailure</span></span> |<span data-ttu-id="48523-113">1</span><span class="sxs-lookup"><span data-stu-id="48523-113">1</span></span>| <span data-ttu-id="48523-114">Échec de l’app service recevoir et traiter le message.</span><span class="sxs-lookup"><span data-stu-id="48523-114">The app service failed to receive and process the message.</span></span>|
|<span data-ttu-id="48523-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="48523-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="48523-116">2</span><span class="sxs-lookup"><span data-stu-id="48523-116">2</span></span>| <span data-ttu-id="48523-117">Le service d’application s’est arrêté car pas suffisamment de ressources n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="48523-117">The app service exited because not enough resources were available.</span></span>|
|<span data-ttu-id="48523-118">MCDAppServiceResponseStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="48523-118">MCDAppServiceResponseStatusUnknown</span></span> |<span data-ttu-id="48523-119">3</span><span class="sxs-lookup"><span data-stu-id="48523-119">3</span></span>| <span data-ttu-id="48523-120">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="48523-120">An unknown error occurred.</span></span>|
|<span data-ttu-id="48523-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="48523-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span></span> |<span data-ttu-id="48523-122">4</span><span class="sxs-lookup"><span data-stu-id="48523-122">4</span></span>| <span data-ttu-id="48523-123">L’appareil auquel le message a été envoyé n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="48523-123">The device to which the message was sent is not available.</span></span>|
|<span data-ttu-id="48523-124">MCDAppServiceResponseStatusMessageTooLarge</span><span class="sxs-lookup"><span data-stu-id="48523-124">MCDAppServiceResponseStatusMessageTooLarge</span></span> |<span data-ttu-id="48523-125">5</span><span class="sxs-lookup"><span data-stu-id="48523-125">5</span></span>| <span data-ttu-id="48523-126">Le service de l’application a échoué traiter le message, car il est trop volumineux.</span><span class="sxs-lookup"><span data-stu-id="48523-126">The app service failed to process the message because it is too large.</span></span>|
|<span data-ttu-id="48523-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="48523-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span></span>|<span data-ttu-id="48523-128">6</span><span class="sxs-lookup"><span data-stu-id="48523-128">6</span></span>| <span data-ttu-id="48523-129">La connexion de service d’application a été fermée avant une réponse a été envoyée.</span><span class="sxs-lookup"><span data-stu-id="48523-129">The app service connection was closed before a response was sent.</span></span>|