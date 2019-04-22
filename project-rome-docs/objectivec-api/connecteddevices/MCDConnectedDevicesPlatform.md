---
title: MCDConnectedDevicesPlatform
description: Une classe pour représenter la plateforme d’appareils connectés et de gérer la connexion de l’application à celui-ci.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801781"
---
# <a name="class-mcdconnecteddevicesplatform"></a><span data-ttu-id="49df3-104">Classe `MCDConnectedDevicesPlatform`</span><span class="sxs-lookup"><span data-stu-id="49df3-104">class `MCDConnectedDevicesPlatform`</span></span> 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
<span data-ttu-id="49df3-105">Cette classe pour représenter la plateforme d’appareils connectés et de gérer la connexion de l’application à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="49df3-105">This class to represent the Connected Devices Platform and manage the app's connection to it.</span></span>

## <a name="properties"></a><span data-ttu-id="49df3-106">Properties</span><span class="sxs-lookup"><span data-stu-id="49df3-106">Properties</span></span>

### <a name="accountmanager"></a><span data-ttu-id="49df3-107">accountManager</span><span class="sxs-lookup"><span data-stu-id="49df3-107">accountManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

<span data-ttu-id="49df3-108">Instance MCDConnectedDevicesAccountManager détenue par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-108">MCDConnectedDevicesAccountManager instance held by the platform.</span></span>

### <a name="notificationregistrationmanager"></a><span data-ttu-id="49df3-109">notificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="49df3-109">notificationRegistrationManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

<span data-ttu-id="49df3-110">Instance MCDConnectedDevicesNotificationRegistrationManager détenue par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-110">MCDConnectedDevicesNotificationRegistrationManager instance held by platform.</span></span>

## <a name="constructors"></a><span data-ttu-id="49df3-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="49df3-111">Constructors</span></span>

### <a name="platformwithsettings"></a><span data-ttu-id="49df3-112">platformWithSettings</span><span class="sxs-lookup"><span data-stu-id="49df3-112">platformWithSettings</span></span>
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="49df3-113">Une nouvelle instance de cette classe avec les paramètres de plateforme spécifié.</span><span class="sxs-lookup"><span data-stu-id="49df3-113">A new instance of this class with specified platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="49df3-114">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49df3-114">Parameters</span></span> 
* `settings` 

<span data-ttu-id="49df3-115">L’objet MCDConnectedDevicesPlatformSettings qui stocke les paramètres de l’application de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-115">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="49df3-116">Returns</span><span class="sxs-lookup"><span data-stu-id="49df3-116">Returns</span></span>

<span data-ttu-id="49df3-117">Retourne un objet MCDConnectedDevicesPlatform contenant des paramètres de plateforme de l’application.</span><span class="sxs-lookup"><span data-stu-id="49df3-117">Returns an MCDConnectedDevicesPlatform object containing the app's platform settings.</span></span>

### <a name="initwithsettings"></a><span data-ttu-id="49df3-118">initWithSettings</span><span class="sxs-lookup"><span data-stu-id="49df3-118">initWithSettings</span></span>
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="49df3-119">Une nouvelle instance de cette classe avec les paramètres de plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-119">A new instance of this class with the platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="49df3-120">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49df3-120">Parameters</span></span> 
* `settings` 

<span data-ttu-id="49df3-121">L’objet MCDConnectedDevicesPlatformSettings qui stocke les paramètres de l’application de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-121">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="49df3-122">Returns</span><span class="sxs-lookup"><span data-stu-id="49df3-122">Returns</span></span>

<span data-ttu-id="49df3-123">Retourne un objet MCDConnectedDevicesPlatform initialisé avec les paramètres de plateforme de l’application.</span><span class="sxs-lookup"><span data-stu-id="49df3-123">Returns an MCDConnectedDevicesPlatform object initialized with the app's platform settings.</span></span>

## <a name="methods"></a><span data-ttu-id="49df3-124">Méthodes</span><span class="sxs-lookup"><span data-stu-id="49df3-124">Methods</span></span>

### <a name="processnotification"></a><span data-ttu-id="49df3-125">processNotification</span><span class="sxs-lookup"><span data-stu-id="49df3-125">processNotification</span></span>
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

<span data-ttu-id="49df3-126">Traiter la notification APNs entrante.</span><span class="sxs-lookup"><span data-stu-id="49df3-126">Process incoming APNs notification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="49df3-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49df3-127">Parameters</span></span> 
* `notification` 

<span data-ttu-id="49df3-128">Contient la notification APNs à traiter.</span><span class="sxs-lookup"><span data-stu-id="49df3-128">Contains the APNs notification to process.</span></span>

#### <a name="returns"></a><span data-ttu-id="49df3-129">Returns</span><span class="sxs-lookup"><span data-stu-id="49df3-129">Returns</span></span>

<span data-ttu-id="49df3-130">Une instance de la classe MCDConnectedDevicesProcessNotificationOperation.</span><span class="sxs-lookup"><span data-stu-id="49df3-130">An instance of the MCDConnectedDevicesProcessNotificationOperation class.</span></span>

### <a name="start"></a><span data-ttu-id="49df3-131">start</span><span class="sxs-lookup"><span data-stu-id="49df3-131">start</span></span>
`- (void) start;`

<span data-ttu-id="49df3-132">Démarrer la plateforme.</span><span class="sxs-lookup"><span data-stu-id="49df3-132">Start the platform.</span></span>

### <a name="shutdownasync"></a><span data-ttu-id="49df3-133">shutdownAsync</span><span class="sxs-lookup"><span data-stu-id="49df3-133">shutdownAsync</span></span>
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="49df3-134">Arrête la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="49df3-134">Shuts down the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="49df3-135">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49df3-135">Parameters</span></span> 
* `completionBlock` 

<span data-ttu-id="49df3-136">Le bloc à appeler à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="49df3-136">The block to invoke upon completion.</span></span>