---
title: MCDLaunchUriProvider
description: En savoir plus sur le protocole MCDLaunchUriProvider. Ce protocole est utilisé pour gérer la gestion d’un URI via le lancement d’une application.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 3339f9b5c8ab14dddf519618795c4150b69dfe3e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760753"
---
# <a name="protocol-mcdlaunchuriprovider"></a>No `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

Cette classe gère la gestion d’un URI par le biais du lancement d’une application.

## <a name="properties"></a>Propriétés 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

Tableau de chaînes représentant les schémas d’URI pris en charge.

## <a name="methods"></a>Méthodes

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

Cette méthode est appelée lorsqu’un appareil distant tente de lancer un URI sur cet appareil.

#### <a name="parameters"></a>Paramètres 
* `uri` URI à lancer.
* `options` Ensemble d’options pour lancer l’URI. L’URI de secours n’est qu’une des options possibles qui peuvent être définies.
* `completionBlock` Bloc de code à exécuter à la fin de l’opération.