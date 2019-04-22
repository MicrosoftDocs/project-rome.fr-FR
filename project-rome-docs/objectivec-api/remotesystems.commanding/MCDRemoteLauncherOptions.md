---
title: MCDRemoteLauncherOptions
description: Une classe pour représenter les options de la fonctionnalité de lancement à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801261"
---
# <a name="class-mcdremotelauncheroptions"></a>Classe `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

Une classe pour représenter les options de la fonctionnalité de lancement à distance.

## <a name="properties"></a>Properties

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.

### <a name="preferredpackageids"></a>preferredPackageIds
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI. Pour les applications Windows, l’ID sera nom de famille de packages de l’application.

## <a name="constructors"></a>Constructeurs

### <a name="optionswithfallbackuri"></a>optionsWithFallbackUri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

Crée et initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `fallbackUri` 

L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.

* `preferredPackageIds` 

Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI. Pour les applications Windows, l’ID sera nom de famille de packages de l’application.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) en cas de réussite, sinon nil.

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

Crée et initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `fallbackUri` 

L’URI de secours pour lancer sur le web dans le cas où l’application de lancement URI échoue.

* `preferredPackageIds` 

Une liste de **chaîne NSString** objets représentant les ID des applications qui doivent être en mesure de démarrer avec cet URI. Pour les applications Windows, l’ID sera nom de famille de packages de l’application.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) en cas de réussite, sinon nil.