---
title: MCDConnectedDevicesAccountAddedStatus
description: Contient les valeurs qui décrivent l’état de l’opération Ajouter compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907201"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="f75d1-104">Enum `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="f75d1-104">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="f75d1-105">Contient les valeurs qui décrivent l’état de l’opération Ajouter compte.</span><span class="sxs-lookup"><span data-stu-id="f75d1-105">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="f75d1-106">Champs</span><span class="sxs-lookup"><span data-stu-id="f75d1-106">Fields</span></span>

| <span data-ttu-id="f75d1-107">Nom</span><span class="sxs-lookup"><span data-stu-id="f75d1-107">Name</span></span>                              |   <span data-ttu-id="f75d1-108">Value</span><span class="sxs-lookup"><span data-stu-id="f75d1-108">Value</span></span>     | <span data-ttu-id="f75d1-109">Description</span><span class="sxs-lookup"><span data-stu-id="f75d1-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="f75d1-110">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="f75d1-110">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="f75d1-111">0</span><span class="sxs-lookup"><span data-stu-id="f75d1-111">0</span></span> | <span data-ttu-id="f75d1-112">Le compte a été correctement ajouté à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="f75d1-112">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="f75d1-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="f75d1-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="f75d1-114">1</span><span class="sxs-lookup"><span data-stu-id="f75d1-114">1</span></span> | <span data-ttu-id="f75d1-115">L’opération de compte a échoué, car Rome ne détecté aucun accès réseau.</span><span class="sxs-lookup"><span data-stu-id="f75d1-115">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="f75d1-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="f75d1-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="f75d1-117">2</span><span class="sxs-lookup"><span data-stu-id="f75d1-117">2</span></span> | <span data-ttu-id="f75d1-118">L’opération de compte a échoué, car Rome n’a pas pu contacter les services web.</span><span class="sxs-lookup"><span data-stu-id="f75d1-118">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="f75d1-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="f75d1-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="f75d1-120">3</span><span class="sxs-lookup"><span data-stu-id="f75d1-120">3</span></span> | <span data-ttu-id="f75d1-121">L’opération de compte a échoué, car l’application n’a pas s’abonner à l’événement AccessTokenRequested.</span><span class="sxs-lookup"><span data-stu-id="f75d1-121">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="f75d1-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="f75d1-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="f75d1-123">4</span><span class="sxs-lookup"><span data-stu-id="f75d1-123">4</span></span> | <span data-ttu-id="f75d1-124">L’opération de compte a échoué, car l’application n’a pas retourné un jeton demandé.</span><span class="sxs-lookup"><span data-stu-id="f75d1-124">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="f75d1-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="f75d1-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="f75d1-126">5</span><span class="sxs-lookup"><span data-stu-id="f75d1-126">5</span></span> | <span data-ttu-id="f75d1-127">L’opération de compte a échoué pour une raison inconnue.</span><span class="sxs-lookup"><span data-stu-id="f75d1-127">The account operation failed for unknown reasons.</span></span> |
