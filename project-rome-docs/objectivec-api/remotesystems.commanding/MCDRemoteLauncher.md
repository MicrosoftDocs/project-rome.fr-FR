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
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="67571-104">Classe `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="67571-104">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="67571-105">Une classe utilisée pour lancer une application sur un appareil distant à l’aide d’un URI.</span><span class="sxs-lookup"><span data-stu-id="67571-105">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="67571-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="67571-106">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="67571-107">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="67571-107">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="67571-108">Lance un URI sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="67571-108">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="67571-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67571-109">Parameters</span></span>
* <span data-ttu-id="67571-110">`uri` L’URI qui entraîne le lancement d’une application.</span><span class="sxs-lookup"><span data-stu-id="67571-110">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="67571-111">Si la cible est Windows, l’application cible est choisie en fonction de schéma.</span><span class="sxs-lookup"><span data-stu-id="67571-111">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="67571-112">Si la cible est non Windows, l’application cible est choisie en fonction de la MCDRemoteSystemConnectionRequest.</span><span class="sxs-lookup"><span data-stu-id="67571-112">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="67571-113">`connection` Spécifie le système distant ou une application pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="67571-113">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="67571-114">`completionBlock` Le bloc à appeler à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="67571-114">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="67571-115">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="67571-115">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="67571-116">Lance un URI avec les options sur le système distant spécifié dans un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="67571-116">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="67571-117">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67571-117">Parameters</span></span>
* <span data-ttu-id="67571-118">`uri` L’URI qui entraîne le lancement d’une application, en fonction de son schéma.</span><span class="sxs-lookup"><span data-stu-id="67571-118">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="67571-119">`connection` Spécifie le système distant ou une application pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="67571-119">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="67571-120">`options` Les spécifications de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="67571-120">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="67571-121">`completionBlock` Le bloc à appeler à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="67571-121">`completionBlock` The block to invoke upon completion.</span></span>