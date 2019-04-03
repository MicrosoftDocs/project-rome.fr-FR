---
title: MCDLaunchUriProvider
description: ''
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4cbfaa9fd1e88345f4ce35987508b061e479854e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907461"
---
# <a name="protocol-mcdlaunchuriprovider"></a>Protocole `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

Cette classe gère la gestion d’un URI via le lancement d’une application.

## <a name="properties"></a>Properties 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

Un tableau de chaînes représentant pris en charge les schémas d’URI.

## <a name="methods"></a>Méthodes

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

Cette méthode est appelée lorsqu’un périphérique distant tente de lancer un URI sur cet appareil.

#### <a name="parameters"></a>Paramètres 
* `uri` URI à lancer.
* `options` Un ensemble d’options pour le lancement de l’URI. La procédure de secours URI est uniquement une des options possibles qui peuvent être définies.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.