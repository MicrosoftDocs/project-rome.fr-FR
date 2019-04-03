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
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="aca20-103">Protocole `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="aca20-103">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="aca20-104">Cette classe gère la gestion d’un URI via le lancement d’une application.</span><span class="sxs-lookup"><span data-stu-id="aca20-104">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="aca20-105">Properties</span><span class="sxs-lookup"><span data-stu-id="aca20-105">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="aca20-106">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="aca20-106">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="aca20-107">Un tableau de chaînes représentant pris en charge les schémas d’URI.</span><span class="sxs-lookup"><span data-stu-id="aca20-107">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="aca20-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aca20-108">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="aca20-109">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="aca20-109">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="aca20-110">Cette méthode est appelée lorsqu’un périphérique distant tente de lancer un URI sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="aca20-110">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="aca20-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aca20-111">Parameters</span></span> 
* <span data-ttu-id="aca20-112">`uri` URI à lancer.</span><span class="sxs-lookup"><span data-stu-id="aca20-112">`uri` The URI to launch.</span></span>
* <span data-ttu-id="aca20-113">`options` Un ensemble d’options pour le lancement de l’URI.</span><span class="sxs-lookup"><span data-stu-id="aca20-113">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="aca20-114">La procédure de secours URI est uniquement une des options possibles qui peuvent être définies.</span><span class="sxs-lookup"><span data-stu-id="aca20-114">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="aca20-115">`completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="aca20-115">`completionBlock` The code block to execute upon completion.</span></span>