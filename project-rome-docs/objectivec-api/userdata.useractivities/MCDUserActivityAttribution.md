---
title: MCDUserActivityAttribution
description: En savoir plus sur la classe MCDUserActivityAttribution. Cette classe gère les éléments graphiques d’une activité utilisateur.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: e4cf9f078215e987c2f0e8068c4afdf640409acc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760193"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="a5538-105">type `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="a5538-105">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="a5538-106">Cette classe gère les éléments graphiques d’une activité utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5538-106">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="a5538-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a5538-107">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="a5538-108">iconUri</span><span class="sxs-lookup"><span data-stu-id="a5538-108">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a5538-109">URI de l’image d’icône.</span><span class="sxs-lookup"><span data-stu-id="a5538-109">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="a5538-110">alternateText</span><span class="sxs-lookup"><span data-stu-id="a5538-110">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="a5538-111">Texte qui décrit l’image d’icône (pour une utilisation avec les lecteurs d’écran).</span><span class="sxs-lookup"><span data-stu-id="a5538-111">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="a5538-112">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="a5538-112">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="a5538-113">Détermine si Windows doit être autorisé à ajouter une chaîne de requête à l’URI d’image fourni par **iconUri** lors de la récupération de l’image.</span><span class="sxs-lookup"><span data-stu-id="a5538-113">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="a5538-114">La chaîne de requête comprend des informations qui peuvent vous aider à sélectionner l’image idéale en fonction de la résolution de l’affichage de l’utilisateur, du paramètre de contraste élevé et de la langue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5538-114">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="a5538-115">Cette chaîne de requête spécifie la mise à l’échelle, le paramètre de contraste et la langue. par exemple, la valeur **iconUri** « www.website.com/images/hello.png » devient « www.website.com/images/hello.png ? MS-Scale = 100&MS-Contrast = standard&MS-lang = en-US ».</span><span class="sxs-lookup"><span data-stu-id="a5538-115">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="a5538-116">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a5538-116">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="a5538-117">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="a5538-117">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a5538-118">Crée une instance de cette classe avec un URI d’icône.</span><span class="sxs-lookup"><span data-stu-id="a5538-118">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a5538-119">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5538-119">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="a5538-120">Valeur de chaîne d’un URI d’icône qui appartient à l’instance créée.</span><span class="sxs-lookup"><span data-stu-id="a5538-120">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="a5538-121">Retours</span><span class="sxs-lookup"><span data-stu-id="a5538-121">Returns</span></span>
<span data-ttu-id="a5538-122">Retourne un objet MCDUserActivityAttribution initialisé avec un URI d’icône.</span><span class="sxs-lookup"><span data-stu-id="a5538-122">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="a5538-123">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="a5538-123">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a5538-124">Crée une instance de cette classe avec l’attribution d’un URI d’icône.</span><span class="sxs-lookup"><span data-stu-id="a5538-124">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a5538-125">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5538-125">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="a5538-126">Valeur de chaîne d’un URI d’icône qui appartient à l’instance créée.</span><span class="sxs-lookup"><span data-stu-id="a5538-126">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="a5538-127">Retours</span><span class="sxs-lookup"><span data-stu-id="a5538-127">Returns</span></span>
<span data-ttu-id="a5538-128">Retourne un objet MCDUserActivityAttribution attribuant avec un URI d’icône.</span><span class="sxs-lookup"><span data-stu-id="a5538-128">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>