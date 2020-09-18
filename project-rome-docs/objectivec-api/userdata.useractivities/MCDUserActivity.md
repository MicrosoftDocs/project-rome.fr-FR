---
title: MCDUserActivity
description: En savoir plus sur la classe MCDUserActivity et ses propriétés. Cette classe représente une instance d’activité utilisateur unique.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760143"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="3899e-105">type `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="3899e-105">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="3899e-106">Cette classe représente une instance d’activité utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="3899e-106">This class represents a single user activity instance.</span></span> <span data-ttu-id="3899e-107">Une activité utilisateur est créée par une application pendant son exécution pour notifier au système d’un flux de travail de l’utilisateur qui peut être poursuivi sur un autre appareil ou à un autre moment sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="3899e-107">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="3899e-108">Il fournit des informations sur une tâche dans laquelle l’utilisateur est engagé.</span><span class="sxs-lookup"><span data-stu-id="3899e-108">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="3899e-109">**Remarque :** Les instances MCDUserActivity ont une limite de taille de 100 Ko, au-delà de laquelle elles ne peuvent pas être publiées.</span><span class="sxs-lookup"><span data-stu-id="3899e-109">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="3899e-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3899e-110">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="3899e-111">activityId</span><span class="sxs-lookup"><span data-stu-id="3899e-111">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="3899e-112">ID unique de cette activité.</span><span class="sxs-lookup"><span data-stu-id="3899e-112">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="3899e-113">state</span><span class="sxs-lookup"><span data-stu-id="3899e-113">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="3899e-114">État de cette activité.</span><span class="sxs-lookup"><span data-stu-id="3899e-114">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="3899e-115">activationUri</span><span class="sxs-lookup"><span data-stu-id="3899e-115">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="3899e-116">URI à suivre lorsque l’activité de l’utilisateur est activée.</span><span class="sxs-lookup"><span data-stu-id="3899e-116">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="3899e-117">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="3899e-117">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="3899e-118">URI convivial du Web détenu par cette activité, à utiliser en cas d’échec de l’URI principal.</span><span class="sxs-lookup"><span data-stu-id="3899e-118">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="3899e-119">contentUri</span><span class="sxs-lookup"><span data-stu-id="3899e-119">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="3899e-120">URI de contenu pour cette activité (l’URI de l’image qui sera utilisée pour représenter l’activité sur un autre appareil).</span><span class="sxs-lookup"><span data-stu-id="3899e-120">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="3899e-121">contentType</span><span class="sxs-lookup"><span data-stu-id="3899e-121">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="3899e-122">type MIME (Multipurpose Internet Mail Extensions) du contenu stocké dans **contentUri**.</span><span class="sxs-lookup"><span data-stu-id="3899e-122">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="3899e-123">Par exemple, « text/plain ».</span><span class="sxs-lookup"><span data-stu-id="3899e-123">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="3899e-124">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="3899e-124">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="3899e-125">Informations de base sur le contenu pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="3899e-125">The basic content info for this activity.</span></span> <span data-ttu-id="3899e-126">Par exemple, si votre activité lit un flux RSS, la chaîne de contenu peut inclure le nom de l’article et son auteur.</span><span class="sxs-lookup"><span data-stu-id="3899e-126">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="3899e-127">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="3899e-127">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="3899e-128">Nom complet de l’application pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="3899e-128">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="3899e-129">visualElements</span><span class="sxs-lookup"><span data-stu-id="3899e-129">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="3899e-130">Éléments visuels pour cette activité (informations qui peuvent être utilisées pour la vignette « détails » de l’activité).</span><span class="sxs-lookup"><span data-stu-id="3899e-130">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="3899e-131">itinérance</span><span class="sxs-lookup"><span data-stu-id="3899e-131">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="3899e-132">Obtient ou définit une valeur indiquant si cette activité est itinérante vers d’autres points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3899e-132">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="3899e-133">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="3899e-133">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="3899e-134">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="3899e-134">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="3899e-135">Crée une instance de cette classe avec un ID donné.</span><span class="sxs-lookup"><span data-stu-id="3899e-135">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3899e-136">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3899e-136">Parameters</span></span>
* `activityId` 

<span data-ttu-id="3899e-137">Identificateur de cette activité (doit être une chaîne unique).</span><span class="sxs-lookup"><span data-stu-id="3899e-137">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="3899e-138">Retours</span><span class="sxs-lookup"><span data-stu-id="3899e-138">Returns</span></span>
<span data-ttu-id="3899e-139">Retourne une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3899e-139">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="3899e-140">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="3899e-140">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="3899e-141">Crée une instance de cette classe avec un ID donné.</span><span class="sxs-lookup"><span data-stu-id="3899e-141">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3899e-142">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3899e-142">Parameters</span></span>
* `activityId`

<span data-ttu-id="3899e-143">Identificateur de cette activité (doit être une chaîne unique).</span><span class="sxs-lookup"><span data-stu-id="3899e-143">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="3899e-144">Retours</span><span class="sxs-lookup"><span data-stu-id="3899e-144">Returns</span></span>
<span data-ttu-id="3899e-145">Retourne une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3899e-145">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="3899e-146">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3899e-146">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="3899e-147">createSession</span><span class="sxs-lookup"><span data-stu-id="3899e-147">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="3899e-148">Crée une session d’activité utilisateur à laquelle ce MCDUserActivity sera associé.</span><span class="sxs-lookup"><span data-stu-id="3899e-148">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="3899e-149">Un MCDUserActivitySession associé indique que l’utilisateur est actuellement engagé dans l’activité.</span><span class="sxs-lookup"><span data-stu-id="3899e-149">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="3899e-150">Retours</span><span class="sxs-lookup"><span data-stu-id="3899e-150">Returns</span></span>
<span data-ttu-id="3899e-151">Session créée.</span><span class="sxs-lookup"><span data-stu-id="3899e-151">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="3899e-152">saveAsync</span><span class="sxs-lookup"><span data-stu-id="3899e-152">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="3899e-153">Publie l’activité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3899e-153">Publishes the user activity.</span></span> <span data-ttu-id="3899e-154">Le MCDUserActivity doit avoir un URI d’activation et un membre VisualElements avec le texte d’affichage défini avant que cette méthode soit appelée.</span><span class="sxs-lookup"><span data-stu-id="3899e-154">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="3899e-155">Cette méthode doit être appelée chaque fois que l’application modifie une propriété de MCDUserActivity (afin de publier la mise à jour).</span><span class="sxs-lookup"><span data-stu-id="3899e-155">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="3899e-156">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3899e-156">Parameters</span></span>
* <span data-ttu-id="3899e-157">`completionBlock` Bloc de code à exécuter à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3899e-157">`completionBlock` The code block to execute upon completion.</span></span>