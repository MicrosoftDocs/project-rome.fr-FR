---
title: MCDUserActivity
description: Cette classe représente une instance d’activité utilisateur unique.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907421"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="62096-104">Classe `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="62096-104">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="62096-105">Cette classe représente une instance d’activité utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="62096-105">This class represents a single user activity instance.</span></span> <span data-ttu-id="62096-106">Une activité de l’utilisateur est créée par une application pendant son exécution pour notifier le système d’un flux de travail d’utilisateur qui peut être poursuivi sur un autre appareil ou à un autre moment sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="62096-106">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="62096-107">Il fournit des informations sur une tâche que prend part à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="62096-107">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="62096-108">**Remarque :** Les instances de MCDUserActivity ont une limite de taille de 100 Ko, au-delà de laquelle ils ne peuvent pas être publiés.</span><span class="sxs-lookup"><span data-stu-id="62096-108">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="62096-109">Properties</span><span class="sxs-lookup"><span data-stu-id="62096-109">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="62096-110">activityId</span><span class="sxs-lookup"><span data-stu-id="62096-110">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="62096-111">ID unique pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="62096-111">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="62096-112">État</span><span class="sxs-lookup"><span data-stu-id="62096-112">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="62096-113">L’état de cette activité.</span><span class="sxs-lookup"><span data-stu-id="62096-113">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="62096-114">activationUri</span><span class="sxs-lookup"><span data-stu-id="62096-114">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="62096-115">L’URI à suivre lors de cette activité utilisateur est activée.</span><span class="sxs-lookup"><span data-stu-id="62096-115">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="62096-116">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="62096-116">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="62096-117">L’URI web conviviale détenue par cette activité, à utiliser si l’URI principal échoue.</span><span class="sxs-lookup"><span data-stu-id="62096-117">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="62096-118">contentUri</span><span class="sxs-lookup"><span data-stu-id="62096-118">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="62096-119">L’URI de contenu pour cette activité (l’URI de l’image qui sera utilisé pour représenter l’activité sur un autre périphérique).</span><span class="sxs-lookup"><span data-stu-id="62096-119">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="62096-120">contentType</span><span class="sxs-lookup"><span data-stu-id="62096-120">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="62096-121">le type MIME (Multipurpose Internet Mail Extensions) du contenu stocké dans **contentUri**.</span><span class="sxs-lookup"><span data-stu-id="62096-121">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="62096-122">Par exemple, « text/plain ».</span><span class="sxs-lookup"><span data-stu-id="62096-122">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="62096-123">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="62096-123">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="62096-124">Informations de contenu de base pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="62096-124">The basic content info for this activity.</span></span> <span data-ttu-id="62096-125">Par exemple, si votre activité a été lu un flux RSS, la chaîne de contenu peut inclure le nom de l’article et son auteur.</span><span class="sxs-lookup"><span data-stu-id="62096-125">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="62096-126">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="62096-126">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="62096-127">Le nom d’affichage application pour cette activité.</span><span class="sxs-lookup"><span data-stu-id="62096-127">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="62096-128">VisualElements</span><span class="sxs-lookup"><span data-stu-id="62096-128">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="62096-129">Les éléments visuels pour cette activité (les informations qui peuvent être utilisées pour la vignette « détails » de l’activité).</span><span class="sxs-lookup"><span data-stu-id="62096-129">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="62096-130">transférable</span><span class="sxs-lookup"><span data-stu-id="62096-130">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="62096-131">Obtient ou définit si cette activité est itinérant pour les autres points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="62096-131">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="62096-132">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="62096-132">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="62096-133">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="62096-133">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="62096-134">Crée une instance de cette classe avec un ID donné.</span><span class="sxs-lookup"><span data-stu-id="62096-134">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="62096-135">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62096-135">Parameters</span></span>
* `activityId` 

<span data-ttu-id="62096-136">L’identificateur pour cette activité (doit être d’une chaîne unique).</span><span class="sxs-lookup"><span data-stu-id="62096-136">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="62096-137">Returns</span><span class="sxs-lookup"><span data-stu-id="62096-137">Returns</span></span>
<span data-ttu-id="62096-138">Retourne une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="62096-138">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="62096-139">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="62096-139">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="62096-140">Crée une instance de cette classe avec un ID donné.</span><span class="sxs-lookup"><span data-stu-id="62096-140">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="62096-141">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62096-141">Parameters</span></span>
* `activityId`

<span data-ttu-id="62096-142">L’identificateur pour cette activité (doit être d’une chaîne unique).</span><span class="sxs-lookup"><span data-stu-id="62096-142">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="62096-143">Returns</span><span class="sxs-lookup"><span data-stu-id="62096-143">Returns</span></span>
<span data-ttu-id="62096-144">Retourne une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="62096-144">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="62096-145">Méthodes</span><span class="sxs-lookup"><span data-stu-id="62096-145">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="62096-146">createSession</span><span class="sxs-lookup"><span data-stu-id="62096-146">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="62096-147">Crée une session d’activité utilisateur qui sera associé ce MCDUserActivity.</span><span class="sxs-lookup"><span data-stu-id="62096-147">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="62096-148">Une MCDUserActivitySession associée indique que l’utilisateur actuellement engagée dans l’activité.</span><span class="sxs-lookup"><span data-stu-id="62096-148">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="62096-149">Returns</span><span class="sxs-lookup"><span data-stu-id="62096-149">Returns</span></span>
<span data-ttu-id="62096-150">La session créée.</span><span class="sxs-lookup"><span data-stu-id="62096-150">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="62096-151">saveAsync</span><span class="sxs-lookup"><span data-stu-id="62096-151">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="62096-152">Publie l’activité des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="62096-152">Publishes the user activity.</span></span> <span data-ttu-id="62096-153">Le MCDUserActivity doit avoir une URI d’activation et de membre VisualElements avec texte à afficher ensemble avant que cette méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="62096-153">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="62096-154">Cette méthode doit être appelée chaque fois que l’application modifie une propriété de la MCDUserActivity (afin de publier la mise à jour).</span><span class="sxs-lookup"><span data-stu-id="62096-154">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="62096-155">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62096-155">Parameters</span></span>
* <span data-ttu-id="62096-156">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="62096-156">`completionBlock` The code block to execute upon completion.</span></span>