---
title: MCDAppServiceInfo
description: Cette classe décrit un service d’application qui appartient à une application ou un périphérique distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801161"
---
# <a name="class-mcdappserviceinfo"></a><span data-ttu-id="770dd-104">Classe `MCDAppServiceInfo`</span><span class="sxs-lookup"><span data-stu-id="770dd-104">class `MCDAppServiceInfo`</span></span> 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

<span data-ttu-id="770dd-105">Cette classe décrit un service d’application qui appartient à une application ou un périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="770dd-105">This class describes an app service that belongs to a remote device or application.</span></span>

## <a name="properties"></a><span data-ttu-id="770dd-106">Properties</span><span class="sxs-lookup"><span data-stu-id="770dd-106">Properties</span></span>

### <a name="name"></a><span data-ttu-id="770dd-107">name</span><span class="sxs-lookup"><span data-stu-id="770dd-107">name</span></span>
`@property(nonatomic, readonly, nullable) NSString* name;`

<span data-ttu-id="770dd-108">Le nom du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-108">The name of the app service being described.</span></span>

### <a name="packageid"></a><span data-ttu-id="770dd-109">packageId</span><span class="sxs-lookup"><span data-stu-id="770dd-109">packageId</span></span>
`@property(nonatomic, readonly, nullable) NSString* packageId;`

<span data-ttu-id="770dd-110">L’ID de package du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-110">The package ID of the app service being described.</span></span>

## <a name="constructors"></a><span data-ttu-id="770dd-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="770dd-111">Constructors</span></span>

### <a name="infowithname"></a><span data-ttu-id="770dd-112">infoWithName</span><span class="sxs-lookup"><span data-stu-id="770dd-112">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

<span data-ttu-id="770dd-113">Initialiser la classe avec les informations et le nom du service d’application.</span><span class="sxs-lookup"><span data-stu-id="770dd-113">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="770dd-114">Paramètres</span><span class="sxs-lookup"><span data-stu-id="770dd-114">Parameters</span></span> 
* `name` 

<span data-ttu-id="770dd-115">Le nom du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-115">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="770dd-116">Returns</span><span class="sxs-lookup"><span data-stu-id="770dd-116">Returns</span></span>
<span data-ttu-id="770dd-117">Retourne un objet MCDAppServiceInfo contenant le nom fourni.</span><span class="sxs-lookup"><span data-stu-id="770dd-117">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="770dd-118">initWithName</span><span class="sxs-lookup"><span data-stu-id="770dd-118">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

<span data-ttu-id="770dd-119">Initialiser la classe avec le nom de l’app service.</span><span class="sxs-lookup"><span data-stu-id="770dd-119">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="770dd-120">Paramètres</span><span class="sxs-lookup"><span data-stu-id="770dd-120">Parameters</span></span> 
* `name` 

<span data-ttu-id="770dd-121">Le nom du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-121">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="770dd-122">Returns</span><span class="sxs-lookup"><span data-stu-id="770dd-122">Returns</span></span>
<span data-ttu-id="770dd-123">Retourne un objet MCDAppServiceInfo initialisé avec le nom fourni.</span><span class="sxs-lookup"><span data-stu-id="770dd-123">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>

### <a name="infowithname"></a><span data-ttu-id="770dd-124">infoWithName</span><span class="sxs-lookup"><span data-stu-id="770dd-124">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="770dd-125">Initialiser la classe avec les informations et le nom du service d’application.</span><span class="sxs-lookup"><span data-stu-id="770dd-125">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="770dd-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="770dd-126">Parameters</span></span> 
* `name` 

<span data-ttu-id="770dd-127">Le nom du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-127">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="770dd-128">L’ID de package du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-128">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="770dd-129">Returns</span><span class="sxs-lookup"><span data-stu-id="770dd-129">Returns</span></span>
<span data-ttu-id="770dd-130">Retourne un objet MCDAppServiceInfo contenant le nom fourni.</span><span class="sxs-lookup"><span data-stu-id="770dd-130">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="770dd-131">initWithName</span><span class="sxs-lookup"><span data-stu-id="770dd-131">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="770dd-132">Initialiser la classe avec le nom de l’app service.</span><span class="sxs-lookup"><span data-stu-id="770dd-132">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="770dd-133">Paramètres</span><span class="sxs-lookup"><span data-stu-id="770dd-133">Parameters</span></span> 
* `name` 

<span data-ttu-id="770dd-134">Le nom du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-134">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="770dd-135">L’ID de package du service d’application en cours de description.</span><span class="sxs-lookup"><span data-stu-id="770dd-135">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="770dd-136">Returns</span><span class="sxs-lookup"><span data-stu-id="770dd-136">Returns</span></span>
<span data-ttu-id="770dd-137">Retourne un objet MCDAppServiceInfo initialisé avec le nom fourni.</span><span class="sxs-lookup"><span data-stu-id="770dd-137">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>
