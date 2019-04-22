---
title: MCDUserActivityVisualElements
description: Cette classe contient les informations visuelles, telles que la description et l’icône, ce qui peut être affichée dans la vignette « details » pour un MCDUserActivity.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801061"
---
# <a name="class-mcduseractivityvisualelements"></a>Classe `MCDUserActivityVisualElements`

```
@interface MCDUserActivityVisualElements : NSObject 
```

Cette classe contient les informations visuelles, telles que la description et l’icône, ce qui peut être affichée dans la vignette « details » pour un MCDUserActivity.

## <a name="properties"></a>Properties

### <a name="displaytext"></a>displayText
`@property(nonatomic, copy, nonnull) NSString* displayText;`

Le texte affiché pour la vignette « détails » de l’activité.

### <a name="descriptiontext"></a>descriptionText
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

Le texte de description de la vignette « détails » de l’activité.

### <a name="backgroundcolor"></a>backgroundColor
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

La couleur d’arrière-plan de la vignette de l’activité.

### <a name="attribution"></a>attribution
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

Les informations graphiques sur l’activité.

### <a name="adaptivecardjson"></a>adaptiveCardJson
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

Le contenu texte de la vignette « détails » de l’activité.

### <a name="attributiondisplaytext"></a>attributionDisplayText
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

Le texte affiché dans la bannière supérieure de la carte de l’activité.