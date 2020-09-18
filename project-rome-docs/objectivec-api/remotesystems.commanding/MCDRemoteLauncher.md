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
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="c897f-105">type `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="c897f-105">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="c897f-106">Classe utilisée pour lancer une application sur un périphérique distant à l’aide d’un URI.</span><span class="sxs-lookup"><span data-stu-id="c897f-106">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="c897f-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c897f-107">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="c897f-108">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="c897f-108">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="c897f-109">Lance un URI sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="c897f-109">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="c897f-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c897f-110">Parameters</span></span>
* <span data-ttu-id="c897f-111">`uri` URI qui déclenchera le lancement d’une application.</span><span class="sxs-lookup"><span data-stu-id="c897f-111">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="c897f-112">Si la cible est Windows, l’application cible est choisie en fonction du schéma.</span><span class="sxs-lookup"><span data-stu-id="c897f-112">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="c897f-113">Si la cible n’est pas Windows, l’application cible est choisie en fonction du MCDRemoteSystemConnectionRequest.</span><span class="sxs-lookup"><span data-stu-id="c897f-113">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="c897f-114">`connection` Spécifie le système distant ou l’application à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="c897f-114">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="c897f-115">`completionBlock` Bloc à appeler à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="c897f-115">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="c897f-116">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="c897f-116">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="c897f-117">Lance un URI avec des options sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="c897f-117">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="c897f-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c897f-118">Parameters</span></span>
* <span data-ttu-id="c897f-119">`uri` URI qui provoquera le lancement d’une application, en fonction de son schéma.</span><span class="sxs-lookup"><span data-stu-id="c897f-119">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="c897f-120">`connection` Spécifie le système distant ou l’application à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="c897f-120">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="c897f-121">`options` Spécifications de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="c897f-121">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="c897f-122">`completionBlock` Bloc à appeler à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="c897f-122">`completionBlock` The block to invoke upon completion.</span></span>