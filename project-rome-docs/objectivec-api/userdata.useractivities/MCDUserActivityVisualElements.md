---
title: MCDUserActivityVisualElements
description: Cette classe contient les informations visuelles, telles que la description et l’icône, ce qui peut être affichée dans la vignette « details » pour un MCDUserActivity.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907411"
---
# <a name="class-mcduseractivityvisualelements"></a><span data-ttu-id="9bb01-104">Classe `MCDUserActivityVisualElements`</span><span class="sxs-lookup"><span data-stu-id="9bb01-104">class `MCDUserActivityVisualElements`</span></span>

```
@interface MCDUserActivityVisualElements : NSObject 
```

<span data-ttu-id="9bb01-105">Cette classe contient les informations visuelles, telles que la description et l’icône, ce qui peut être affichée dans la vignette « details » pour un MCDUserActivity.</span><span class="sxs-lookup"><span data-stu-id="9bb01-105">This class contains the visual information, such as the description and icon, that can be shown in the "details" tile for a MCDUserActivity.</span></span>

## <a name="properties"></a><span data-ttu-id="9bb01-106">Properties</span><span class="sxs-lookup"><span data-stu-id="9bb01-106">Properties</span></span>

### <a name="displaytext"></a><span data-ttu-id="9bb01-107">displayText</span><span class="sxs-lookup"><span data-stu-id="9bb01-107">displayText</span></span>
`@property(nonatomic, copy, nonnull) NSString* displayText;`

<span data-ttu-id="9bb01-108">Le texte affiché pour la vignette « détails » de l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-108">The display text for the "details" tile of the activity.</span></span>

### <a name="descriptiontext"></a><span data-ttu-id="9bb01-109">descriptionText</span><span class="sxs-lookup"><span data-stu-id="9bb01-109">descriptionText</span></span>
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

<span data-ttu-id="9bb01-110">Le texte de description de la vignette « détails » de l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-110">The description text for the "details" tile of the activity.</span></span>

### <a name="backgroundcolor"></a><span data-ttu-id="9bb01-111">backgroundColor</span><span class="sxs-lookup"><span data-stu-id="9bb01-111">backgroundColor</span></span>
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

<span data-ttu-id="9bb01-112">La couleur d’arrière-plan de la vignette de l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-112">The background color for the tile of the activity.</span></span>

### <a name="attribution"></a><span data-ttu-id="9bb01-113">attribution</span><span class="sxs-lookup"><span data-stu-id="9bb01-113">attribution</span></span>
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

<span data-ttu-id="9bb01-114">Les informations graphiques sur l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-114">The graphical information about the activity.</span></span>

### <a name="adaptivecardjson"></a><span data-ttu-id="9bb01-115">adaptiveCardJson</span><span class="sxs-lookup"><span data-stu-id="9bb01-115">adaptiveCardJson</span></span>
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

<span data-ttu-id="9bb01-116">Le contenu texte de la vignette « détails » de l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-116">The content text for the "details" tile of the activity.</span></span>

### <a name="attributiondisplaytext"></a><span data-ttu-id="9bb01-117">attributionDisplayText</span><span class="sxs-lookup"><span data-stu-id="9bb01-117">attributionDisplayText</span></span>
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

<span data-ttu-id="9bb01-118">Le texte affiché dans la bannière supérieure de la carte de l’activité.</span><span class="sxs-lookup"><span data-stu-id="9bb01-118">The text that is shown in the top banner of the activity card.</span></span>