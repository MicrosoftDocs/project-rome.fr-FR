---
title: MCDRemoteLauncherOptions
description: En savoir plus sur la classe MCDRemoteLauncherOptions. Cette classe représente les options de la fonctionnalité de lancement à distance.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 2e698ad71282e44d1447e19085598139b67f9270
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760733"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="1ce0c-105">type `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="1ce0c-105">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="1ce0c-106">Classe qui représente les options de la fonctionnalité de lancement à distance.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-106">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="1ce0c-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1ce0c-107">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="1ce0c-108">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="1ce0c-108">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="1ce0c-109">URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-109">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="1ce0c-110">preferredPackageIds</span><span class="sxs-lookup"><span data-stu-id="1ce0c-110">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="1ce0c-111">Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-111">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="1ce0c-112">Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-112">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="1ce0c-113">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="1ce0c-113">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="1ce0c-114">optionsWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="1ce0c-114">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="1ce0c-115">Crée et Initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1ce0c-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ce0c-116">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="1ce0c-117">URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-117">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="1ce0c-118">Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-118">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="1ce0c-119">Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-119">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="1ce0c-120">Retours</span><span class="sxs-lookup"><span data-stu-id="1ce0c-120">Returns</span></span>
<span data-ttu-id="1ce0c-121">Retourne le [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) initialisé en cas de réussite, sinon Nil.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-121">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="1ce0c-122">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="1ce0c-122">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="1ce0c-123">Crée et Initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1ce0c-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ce0c-124">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="1ce0c-125">URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-125">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="1ce0c-126">Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-126">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="1ce0c-127">Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-127">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="1ce0c-128">Retours</span><span class="sxs-lookup"><span data-stu-id="1ce0c-128">Returns</span></span>
<span data-ttu-id="1ce0c-129">Retourne le [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) initialisé en cas de réussite, sinon Nil.</span><span class="sxs-lookup"><span data-stu-id="1ce0c-129">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>