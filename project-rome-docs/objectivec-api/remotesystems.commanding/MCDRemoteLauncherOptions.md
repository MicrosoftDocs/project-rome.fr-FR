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
# <a name="class-mcdremotelauncheroptions"></a>type `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

Classe qui représente les options de la fonctionnalité de lancement à distance.

## <a name="properties"></a>Propriétés

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.

### <a name="preferredpackageids"></a>preferredPackageIds
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI. Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.

## <a name="constructors"></a>Constructeurs

### <a name="optionswithfallbackuri"></a>optionsWithFallbackUri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

Crée et Initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `fallbackUri` 

URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.

* `preferredPackageIds` 

Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI. Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.

#### <a name="returns"></a>Retours
Retourne le [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) initialisé en cas de réussite, sinon Nil.

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

Crée et Initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `fallbackUri` 

URI de secours à lancer sur le Web en cas d’échec de l’URI de lancement de l’application.

* `preferredPackageIds` 

Liste d’objets **chaîne NSString** représentant les ID des applications qui doivent pouvoir être lancées avec cet URI. Pour les applications Windows, l’ID sera le nom de la famille de packages de l’application.

#### <a name="returns"></a>Retours
Retourne le [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) initialisé en cas de réussite, sinon Nil.