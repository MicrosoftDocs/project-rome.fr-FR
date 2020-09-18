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
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="bca99-105">No `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="bca99-105">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="bca99-106">Cette classe gère la gestion d’un URI par le biais du lancement d’une application.</span><span class="sxs-lookup"><span data-stu-id="bca99-106">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="bca99-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bca99-107">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="bca99-108">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="bca99-108">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="bca99-109">Tableau de chaînes représentant les schémas d’URI pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bca99-109">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="bca99-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bca99-110">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="bca99-111">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="bca99-111">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="bca99-112">Cette méthode est appelée lorsqu’un appareil distant tente de lancer un URI sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="bca99-112">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="bca99-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bca99-113">Parameters</span></span> 
* <span data-ttu-id="bca99-114">`uri` URI à lancer.</span><span class="sxs-lookup"><span data-stu-id="bca99-114">`uri` The URI to launch.</span></span>
* <span data-ttu-id="bca99-115">`options` Ensemble d’options pour lancer l’URI.</span><span class="sxs-lookup"><span data-stu-id="bca99-115">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="bca99-116">L’URI de secours n’est qu’une des options possibles qui peuvent être définies.</span><span class="sxs-lookup"><span data-stu-id="bca99-116">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="bca99-117">`completionBlock` Bloc de code à exécuter à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="bca99-117">`completionBlock` The code block to execute upon completion.</span></span>