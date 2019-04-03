---
title: MCDUserActivityChannel
description: Cette classe gère l’ajout et l’interrogation des activités de l’utilisateur pour l’application.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b047af1da3ba79be88a53cf589c3894892b01ef4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907801"
---
# <a name="class-mcduseractivitychannel"></a><span data-ttu-id="d8829-104">Classe `MCDUserActivityChannel`</span><span class="sxs-lookup"><span data-stu-id="d8829-104">class `MCDUserActivityChannel`</span></span>

```
@interface MCDUserActivityChannel : NSObject
```

<span data-ttu-id="d8829-105">Cette classe gère l’ajout et l’interrogation des activités de l’utilisateur pour l’application.</span><span class="sxs-lookup"><span data-stu-id="d8829-105">This class handles the adding and querying of user activities for the application.</span></span>

## <a name="properties"></a><span data-ttu-id="d8829-106">Properties</span><span class="sxs-lookup"><span data-stu-id="d8829-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="d8829-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="d8829-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="d8829-108">Obtient la valeur de portée de synchronisation de données utilisateur pour les activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8829-108">Gets the user data sync scope value for User Activities.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="d8829-109">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="d8829-109">appDisplayName</span></span>
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

<span data-ttu-id="d8829-110">Nom complet de l’application pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="d8829-110">The display name of the app for all activities.</span></span>

## <a name="constructors"></a><span data-ttu-id="d8829-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="d8829-111">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="d8829-112">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="d8829-112">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

<span data-ttu-id="d8829-113">Crée une instance de cette classe avec le flux de données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8829-113">Creates an instance of this class with the user data feed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-114">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-114">Parameters</span></span>
* <span data-ttu-id="d8829-115">`userDataFeed` Les données utilisateur associées aux activités sur ce canal.</span><span class="sxs-lookup"><span data-stu-id="d8829-115">`userDataFeed` The user data associated with the activities on this channel.</span></span>

#### <a name="returns"></a><span data-ttu-id="d8829-116">Returns</span><span class="sxs-lookup"><span data-stu-id="d8829-116">Returns</span></span>
<span data-ttu-id="d8829-117">Retourne une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="d8829-117">Returns a new instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="d8829-118">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d8829-118">Methods</span></span>

### <a name="getorcreateuseractivityasync"></a><span data-ttu-id="d8829-119">getOrCreateUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-119">getOrCreateUserActivityAsync</span></span>
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-120">Crée l’activité de l’utilisateur spécifié ou obtient une référence à celui-ci s’il existe déjà.</span><span class="sxs-lookup"><span data-stu-id="d8829-120">Creates the specified user activity, or gets a reference to it if it already exists.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-121">Parameters</span></span>
* <span data-ttu-id="d8829-122">`activityId` L’ID pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="d8829-122">`activityId` The ID for this activity.</span></span>
* <span data-ttu-id="d8829-123">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-123">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="d8829-124">Fournit l’accès à l’activité récupérée.</span><span class="sxs-lookup"><span data-stu-id="d8829-124">This provides access to the retrieved activity.</span></span>

### <a name="deleteactivityasync"></a><span data-ttu-id="d8829-125">deleteActivityAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-125">deleteActivityAsync</span></span>
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-126">Supprime l’activité utilisateur donné.</span><span class="sxs-lookup"><span data-stu-id="d8829-126">Deletes the given user activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-127">Parameters</span></span>
* <span data-ttu-id="d8829-128">`activityId` ID de l’activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d8829-128">`activityId` The ID of the activity to delete.</span></span>
* <span data-ttu-id="d8829-129">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-129">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="deleteallactivitiesasync"></a><span data-ttu-id="d8829-130">deleteAllActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-130">deleteAllActivitiesAsync</span></span>
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-131">Supprime toutes les activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8829-131">Deletes all user activities.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-132">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-132">Parameters</span></span>
* <span data-ttu-id="d8829-133">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-133">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="getrecentuseractivitiesasync"></a><span data-ttu-id="d8829-134">getRecentUserActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-134">getRecentUserActivitiesAsync</span></span>
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-135">Obtient un historique des activités récentes de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8829-135">Gets a history of recent user activities.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="d8829-136">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-136">Parameters</span></span>
* <span data-ttu-id="d8829-137">`maxUniqueActivities` Le nombre maximal d’activités d’utilisateur à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d8829-137">`maxUniqueActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="d8829-138">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-138">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="d8829-139">Fournit l’accès à l’historique de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d8829-139">This provides access to the activity history.</span></span>

### <a name="getsessionhistoryitemsforuseractivityasync"></a><span data-ttu-id="d8829-140">getSessionHistoryItemsForUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-140">getSessionHistoryItemsForUserActivityAsync</span></span>
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-141">Obtient des entrées d’historique de la session pour une activité donnée.</span><span class="sxs-lookup"><span data-stu-id="d8829-141">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-142">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-142">Parameters</span></span>
* <span data-ttu-id="d8829-143">`activityId` L’ID de l’activité pour obtenir l’historique pour.</span><span class="sxs-lookup"><span data-stu-id="d8829-143">`activityId` The ID of the activity to get history for.</span></span>
* <span data-ttu-id="d8829-144">`startTime` L’heure à laquelle à prendre en compte l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="d8829-144">`startTime` The time at which to consider session history.</span></span>
* <span data-ttu-id="d8829-145">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-145">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="d8829-146">Fournit l’accès à l’historique de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d8829-146">This provides access to the activity history.</span></span>

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a><span data-ttu-id="d8829-147">getRecentSessionHistoryItemsForTimeRangeAsync</span><span class="sxs-lookup"><span data-stu-id="d8829-147">getRecentSessionHistoryItemsForTimeRangeAsync</span></span>
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

<span data-ttu-id="d8829-148">Obtient des entrées d’historique de la session pour une activité donnée.</span><span class="sxs-lookup"><span data-stu-id="d8829-148">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8829-149">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8829-149">Parameters</span></span>
* <span data-ttu-id="d8829-150">`startTime` Heure à laquelle commencer à évaluer l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="d8829-150">`startTime` The time at which to start considering session history.</span></span>
* <span data-ttu-id="d8829-151">`endTime` Heure à laquelle se termine en tenant compte de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="d8829-151">`endTime` The time at which to end considering session history.</span></span>
* <span data-ttu-id="d8829-152">`maxActivities` Le nombre maximal d’activités d’utilisateur à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d8829-152">`maxActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="d8829-153">`completion` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-153">`completion` The code block to execute upon completion.</span></span>
* <span data-ttu-id="d8829-154">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="d8829-154">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="d8829-155">Fournit l’accès à l’historique de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d8829-155">This provides access to the activity history.</span></span>