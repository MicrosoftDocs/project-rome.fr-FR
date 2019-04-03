---
title: MCDRemoteLauncher
description: Une classe utilisée pour lancer une application sur un appareil distant à l’aide d’un URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: aa0211c1edc33e8a277c4954d94fbcbb6565c923
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907381"
---
# <a name="class-mcdremotelauncher"></a>Classe `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

Une classe utilisée pour lancer une application sur un appareil distant à l’aide d’un URI.


## <a name="methods"></a>Méthodes

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Lance un URI sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Paramètres
* `uri` L’URI qui entraîne le lancement d’une application.  Si la cible est Windows, l’application cible est choisie en fonction de schéma. Si la cible est non Windows, l’application cible est choisie en fonction de la MCDRemoteSystemConnectionRequest.

* `connection` Spécifie le système distant ou une application pour se connecter à.
* `completionBlock` Le bloc à appeler à l’achèvement.

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Lance un URI avec les options sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Paramètres
* `uri` L’URI qui entraîne le lancement d’une application, en fonction de son schéma.
* `connection` Spécifie le système distant ou une application pour se connecter à.
* `options` Les spécifications de lancement de l’application.
* `completionBlock` Le bloc à appeler à l’achèvement.