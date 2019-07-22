---
title: MCDUserActivityAttribution
description: Cette classe gère les éléments graphiques d’une activité de l’utilisateur.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 94ae2f5afef24a1f4e320014ac930d67b657b0d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801541"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="30519-104">Classe `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="30519-104">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="30519-105">Cette classe gère les éléments graphiques d’une activité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30519-105">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="30519-106">Properties</span><span class="sxs-lookup"><span data-stu-id="30519-106">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="30519-107">iconUri</span><span class="sxs-lookup"><span data-stu-id="30519-107">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="30519-108">URI de l’image d’icône.</span><span class="sxs-lookup"><span data-stu-id="30519-108">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="30519-109">alternateText</span><span class="sxs-lookup"><span data-stu-id="30519-109">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="30519-110">Le texte qui décrit l’image d’icône (pour une utilisation avec les lecteurs d’écran).</span><span class="sxs-lookup"><span data-stu-id="30519-110">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="30519-111">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="30519-111">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="30519-112">Détermine s’il faut autoriser Windows à ajouter une chaîne de requête à l’image URI fourni à partir de **IconUri** lors de la récupération de l’image.</span><span class="sxs-lookup"><span data-stu-id="30519-112">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="30519-113">La chaîne de requête inclut des informations qui peuvent aider à sélectionner l’image idéale basée sur la résolution de l’affichage de l’utilisateur, le paramètre de contraste élevé et langue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30519-113">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="30519-114">Cette chaîne de requête spécifie l’échelle, paramètre de contraste et la langue ; par exemple, un **IconUri** devient la valeur de "www.website.com/images/hello.png" "www.website.com/images/hello.png?ms-scale=100&ms-contraste=standard&ms-lang=en-us".</span><span class="sxs-lookup"><span data-stu-id="30519-114">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="30519-115">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="30519-115">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="30519-116">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="30519-116">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="30519-117">Crée une instance de cette classe avec un URI de l’icône.</span><span class="sxs-lookup"><span data-stu-id="30519-117">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="30519-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30519-118">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="30519-119">Valeur de chaîne d’un URI de l’icône d’appartenir à l’instance créée.</span><span class="sxs-lookup"><span data-stu-id="30519-119">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="30519-120">Returns</span><span class="sxs-lookup"><span data-stu-id="30519-120">Returns</span></span>
<span data-ttu-id="30519-121">Retourne un objet MCDUserActivityAttribution initialisé avec un uri de l’icône.</span><span class="sxs-lookup"><span data-stu-id="30519-121">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="30519-122">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="30519-122">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="30519-123">Crée une instance de cette classe avec l’attribution à un uri de l’icône.</span><span class="sxs-lookup"><span data-stu-id="30519-123">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="30519-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30519-124">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="30519-125">Valeur de chaîne d’un URI de l’icône d’appartenir à l’instance créée.</span><span class="sxs-lookup"><span data-stu-id="30519-125">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="30519-126">Returns</span><span class="sxs-lookup"><span data-stu-id="30519-126">Returns</span></span>
<span data-ttu-id="30519-127">Retourne un objet MCDUserActivityAttribution attribution avec un uri de l’icône.</span><span class="sxs-lookup"><span data-stu-id="30519-127">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>