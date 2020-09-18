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
# <a name="class-mcduseractivityattribution"></a>type `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

Cette classe gère les éléments graphiques d’une activité utilisateur.

## <a name="properties"></a>Propriétés

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

URI de l’image d’icône.

### <a name="alternatetext"></a>alternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

Texte qui décrit l’image d’icône (pour une utilisation avec les lecteurs d’écran).

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

Détermine si Windows doit être autorisé à ajouter une chaîne de requête à l’URI d’image fourni par **iconUri** lors de la récupération de l’image. La chaîne de requête comprend des informations qui peuvent vous aider à sélectionner l’image idéale en fonction de la résolution de l’affichage de l’utilisateur, du paramètre de contraste élevé et de la langue de l’utilisateur. Cette chaîne de requête spécifie la mise à l’échelle, le paramètre de contraste et la langue. par exemple, la valeur **iconUri** « www.website.com/images/hello.png » devient « www.website.com/images/hello.png ? MS-Scale = 100&MS-Contrast = standard&MS-lang = en-US ».

## <a name="constructors"></a>Constructeurs

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

Crée une instance de cette classe avec un URI d’icône.

#### <a name="parameters"></a>Paramètres
* `iconUri` 

Valeur de chaîne d’un URI d’icône qui appartient à l’instance créée.

#### <a name="returns"></a>Retours
Retourne un objet MCDUserActivityAttribution initialisé avec un URI d’icône.

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

Crée une instance de cette classe avec l’attribution d’un URI d’icône.

#### <a name="parameters"></a>Paramètres
* `iconUri` 

Valeur de chaîne d’un URI d’icône qui appartient à l’instance créée.

#### <a name="returns"></a>Retours
Retourne un objet MCDUserActivityAttribution attribuant avec un URI d’icône.