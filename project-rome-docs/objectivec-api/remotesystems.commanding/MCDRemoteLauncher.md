---
title: MCDRemoteLauncher
description: En savoir plus sur la classe MCDRemoteLauncher. Cette classe est utilisée pour lancer une application sur un périphérique distant à l’aide d’un URI.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: e5231897241e54c44b4f3fb299adf68af396cac9
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760743"
---
# <a name="class-mcdremotelauncher"></a>type `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

Classe utilisée pour lancer une application sur un périphérique distant à l’aide d’un URI.


## <a name="methods"></a>Méthodes

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Lance un URI sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Paramètres
* `uri` URI qui déclenchera le lancement d’une application.  Si la cible est Windows, l’application cible est choisie en fonction du schéma. Si la cible n’est pas Windows, l’application cible est choisie en fonction du MCDRemoteSystemConnectionRequest.

* `connection` Spécifie le système distant ou l’application à laquelle se connecter.
* `completionBlock` Bloc à appeler à la fin de l’opération.

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Lance un URI avec des options sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Paramètres
* `uri` URI qui provoquera le lancement d’une application, en fonction de son schéma.
* `connection` Spécifie le système distant ou l’application à laquelle se connecter.
* `options` Spécifications de lancement de l’application.
* `completionBlock` Bloc à appeler à la fin de l’opération.