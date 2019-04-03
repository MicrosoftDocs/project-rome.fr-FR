---
title: MCDRemoteLauncherOptions
description: Une classe pour représenter les options de la fonctionnalité de lancement à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907331"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="05916-104">Classe `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="05916-104">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="05916-105">Une classe pour représenter les options de la fonctionnalité de lancement à distance.</span><span class="sxs-lookup"><span data-stu-id="05916-105">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="05916-106">Properties</span><span class="sxs-lookup"><span data-stu-id="05916-106">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="05916-107">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="05916-107">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="05916-108">L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.</span><span class="sxs-lookup"><span data-stu-id="05916-108">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="05916-109">preferredPackageIds</span><span class="sxs-lookup"><span data-stu-id="05916-109">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="05916-110">Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="05916-110">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="05916-111">Pour les applications Windows, l’ID sera nom de famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="05916-111">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="05916-112">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="05916-112">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="05916-113">optionsWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="05916-113">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="05916-114">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="05916-114">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="05916-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05916-115">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="05916-116">L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.</span><span class="sxs-lookup"><span data-stu-id="05916-116">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="05916-117">Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="05916-117">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="05916-118">Pour les applications Windows, l’ID sera nom de famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="05916-118">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="05916-119">Returns</span><span class="sxs-lookup"><span data-stu-id="05916-119">Returns</span></span>
<span data-ttu-id="05916-120">Retourne l’initialisé [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="05916-120">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="05916-121">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="05916-121">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="05916-122">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="05916-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="05916-123">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05916-123">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="05916-124">L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.</span><span class="sxs-lookup"><span data-stu-id="05916-124">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="05916-125">Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI.</span><span class="sxs-lookup"><span data-stu-id="05916-125">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="05916-126">Pour les applications Windows, l’ID sera nom de famille de packages de l’application.</span><span class="sxs-lookup"><span data-stu-id="05916-126">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="05916-127">Returns</span><span class="sxs-lookup"><span data-stu-id="05916-127">Returns</span></span>
<span data-ttu-id="05916-128">Retourne l’initialisé [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="05916-128">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>