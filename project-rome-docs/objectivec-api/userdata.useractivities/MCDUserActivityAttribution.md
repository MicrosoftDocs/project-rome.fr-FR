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
# <a name="class-mcduseractivityattribution"></a>Classe `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

Cette classe gère les éléments graphiques d’une activité de l’utilisateur.

## <a name="properties"></a>Properties

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

URI de l’image d’icône.

### <a name="alternatetext"></a>alternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

Le texte qui décrit l’image d’icône (pour une utilisation avec les lecteurs d’écran).

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

Détermine s’il faut autoriser Windows à ajouter une chaîne de requête à l’image URI fourni à partir de **IconUri** lors de la récupération de l’image. La chaîne de requête inclut des informations qui peuvent aider à sélectionner l’image idéale basée sur la résolution de l’affichage de l’utilisateur, le paramètre de contraste élevé et langue de l’utilisateur. Cette chaîne de requête spécifie l’échelle, paramètre de contraste et la langue ; par exemple, un **IconUri** devient la valeur de "www.website.com/images/hello.png" "www.website.com/images/hello.png?ms-scale=100&ms-contraste=standard&ms-lang=en-us".

## <a name="constructors"></a>Constructeurs

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

Crée une instance de cette classe avec un URI de l’icône.

#### <a name="parameters"></a>Paramètres
* `iconUri` 

Valeur de chaîne d’un URI de l’icône d’appartenir à l’instance créée.

#### <a name="returns"></a>Returns
Retourne un objet MCDUserActivityAttribution initialisé avec un uri de l’icône.

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

Crée une instance de cette classe avec l’attribution à un uri de l’icône.

#### <a name="parameters"></a>Paramètres
* `iconUri` 

Valeur de chaîne d’un URI de l’icône d’appartenir à l’instance créée.

#### <a name="returns"></a>Returns
Retourne un objet MCDUserActivityAttribution attribution avec un uri de l’icône.