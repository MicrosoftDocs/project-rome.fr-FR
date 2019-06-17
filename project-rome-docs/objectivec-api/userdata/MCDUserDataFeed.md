---
title: MCDUserDataFeed
description: Cette classe est chargée pour la synchronisation des données spécifiques à l’utilisateur avec le backend de la plateforme de périphériques connectés.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: cd90c266c3c0293996a4f23059719224579404ff
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132237"
---
# <a name="class-mcduserdatafeed"></a><span data-ttu-id="860cc-104">Classe `MCDUserDataFeed`</span><span class="sxs-lookup"><span data-stu-id="860cc-104">class `MCDUserDataFeed`</span></span>

```
@interface MCDUserDataFeed : NSObject
```

<span data-ttu-id="860cc-105">Cette classe est chargée pour la synchronisation des données spécifiques à l’utilisateur avec le backend de la plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="860cc-105">This class is responsible for synchronizing user-specific data with the Connected Devices Platform backend.</span></span> <span data-ttu-id="860cc-106">Les données sont synchronisées varie en fonction **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances sont contenues.</span><span class="sxs-lookup"><span data-stu-id="860cc-106">The data that is synchronized depends on which **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances are contained.</span></span>

## <a name="properties"></a><span data-ttu-id="860cc-107">Properties</span><span class="sxs-lookup"><span data-stu-id="860cc-107">Properties</span></span>

### <a name="syncstatus"></a><span data-ttu-id="860cc-108">syncStatus</span><span class="sxs-lookup"><span data-stu-id="860cc-108">syncStatus</span></span>
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

<span data-ttu-id="860cc-109">Décrit l’état actuel de la synchronisation des données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="860cc-109">Describes the current status of user data synchronization.</span></span>

### <a name="syncstatuschanged"></a><span data-ttu-id="860cc-110">syncStatusChanged</span><span class="sxs-lookup"><span data-stu-id="860cc-110">syncStatusChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

<span data-ttu-id="860cc-111">Événement de modification du statut de la synchronisation de la UserDataFeed.</span><span class="sxs-lookup"><span data-stu-id="860cc-111">Event for when the sync status of the UserDataFeed changes.</span></span>

### <a name="daystosync"></a><span data-ttu-id="860cc-112">daysToSync</span><span class="sxs-lookup"><span data-stu-id="860cc-112">daysToSync</span></span>
`@property(nonatomic, readwrite) NSInteger daysToSync;`

<span data-ttu-id="860cc-113">Le nombre de jours de données à synchroniser, qui doivent être de moins de 30.</span><span class="sxs-lookup"><span data-stu-id="860cc-113">The number of days of data to sync, which should be fewer than 30.</span></span>  <span data-ttu-id="860cc-114">Il représente la valeur par défaut, qui est déterminée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="860cc-114">It represents the default value, which will be determined by the server.</span></span>

## <a name="constructors"></a><span data-ttu-id="860cc-115">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="860cc-115">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="860cc-116">getForAccount</span><span class="sxs-lookup"><span data-stu-id="860cc-116">getForAccount</span></span>
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

<span data-ttu-id="860cc-117">Crée et initialise une nouvelle instance de cette classe avec un compte d’utilisateur, instance de la plateforme et l’ID d’application multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="860cc-117">Creates and initializes a new instance of this class with a user account, platform instance, and the cross-platform app ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="860cc-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="860cc-118">Parameters</span></span>
* `userAccount` 

<span data-ttu-id="860cc-119">Le compte d’utilisateur qui seront associées ces données.</span><span class="sxs-lookup"><span data-stu-id="860cc-119">The user account that this data will be associated with.</span></span>

* `platform` 

<span data-ttu-id="860cc-120">Le **MCDPlatform** instance qui a été initialisé pour les fonctionnalités des appareils connectés de cette application.</span><span class="sxs-lookup"><span data-stu-id="860cc-120">The **MCDPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

* `activitySourceHost` 

<span data-ttu-id="860cc-121">L’ID d’application multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="860cc-121">The cross-platform app ID.</span></span> <span data-ttu-id="860cc-122">Cette valeur est extraite via l’inscription de tableau de bord de développement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="860cc-122">This is retrieved through the Microsoft Developer Dashboard registration.</span></span>

#### <a name="returns"></a><span data-ttu-id="860cc-123">Returns</span><span class="sxs-lookup"><span data-stu-id="860cc-123">Returns</span></span>
<span data-ttu-id="860cc-124">Retourne une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="860cc-124">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="860cc-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="860cc-125">Methods</span></span>

> [!WARNING]
> <span data-ttu-id="860cc-126">Cette fonction est dépréciée, 'subscribeToSyncScopesWithResultAsync' à la place.</span><span class="sxs-lookup"><span data-stu-id="860cc-126">This function is deprecated, 'subscribeToSyncScopesWithResultAsync' instead.</span></span>

### <a name="subscribetosyncscopesasync"></a><span data-ttu-id="860cc-127">subscribeToSyncScopesAsync</span><span class="sxs-lookup"><span data-stu-id="860cc-127">subscribeToSyncScopesAsync</span></span>
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback  __attribute__((deprecated("Use subscribeToSyncScopesWithResultAsync instead")));`

<span data-ttu-id="860cc-128">Ajoute **MCDUserDataFeedSyncScope** instances à cette MCDUserDataFeed.</span><span class="sxs-lookup"><span data-stu-id="860cc-128">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="860cc-129">Cette MCDUserDataFeed est synchronisé en fonction de la **MCDUserDataFeedSyncScope** instances spécifiées.</span><span class="sxs-lookup"><span data-stu-id="860cc-129">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="860cc-130">Paramètres</span><span class="sxs-lookup"><span data-stu-id="860cc-130">Parameters</span></span>

* <span data-ttu-id="860cc-131">`syncScopes` Un tableau de **MCDSyncScope** instances.</span><span class="sxs-lookup"><span data-stu-id="860cc-131">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="860cc-132">Le résultat de rappel indique si l’abonnement est réussie, ou non.</span><span class="sxs-lookup"><span data-stu-id="860cc-132">The callback result indicates if subscription is successful, or not.</span></span>

### <a name="subscribetosyncscopeswithresultasync"></a><span data-ttu-id="860cc-133">subscribeToSyncScopesWithResultAsync</span><span class="sxs-lookup"><span data-stu-id="860cc-133">subscribeToSyncScopesWithResultAsync</span></span>
`- (void)subscribeToSyncScopesWithResultAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(MCDUserDataFeedSubscribeResult* _Nullable, NSError* _Nullable)) callback;`

<span data-ttu-id="860cc-134">Ajoute **MCDUserDataFeedSyncScope** instances à cette MCDUserDataFeed.</span><span class="sxs-lookup"><span data-stu-id="860cc-134">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="860cc-135">Cette MCDUserDataFeed est synchronisé en fonction de la **MCDUserDataFeedSyncScope** instances spécifiées.</span><span class="sxs-lookup"><span data-stu-id="860cc-135">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="860cc-136">Paramètres</span><span class="sxs-lookup"><span data-stu-id="860cc-136">Parameters</span></span>

* <span data-ttu-id="860cc-137">`syncScopes` Un tableau de **MCDSyncScope** instances.</span><span class="sxs-lookup"><span data-stu-id="860cc-137">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="860cc-138">Le résultat de rappel indique si l’abonnement est réussie, ou non.</span><span class="sxs-lookup"><span data-stu-id="860cc-138">The callback result indicates if subscription is successful, or not.</span></span>

### <a name="startsync"></a><span data-ttu-id="860cc-139">startSync</span><span class="sxs-lookup"><span data-stu-id="860cc-139">startSync</span></span>
`- (void)startSync;`

<span data-ttu-id="860cc-140">Démarre le processus de synchronisation avec la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="860cc-140">Starts the synchronization process with the Connected Devices Platform.</span></span> <span data-ttu-id="860cc-141">Pendant cette opération, le **syncStatus** propriété sera actualisée et les événements de modification seront déclenchés.</span><span class="sxs-lookup"><span data-stu-id="860cc-141">During this operation, the **syncStatus** property will be updated and change events will be raised.</span></span>