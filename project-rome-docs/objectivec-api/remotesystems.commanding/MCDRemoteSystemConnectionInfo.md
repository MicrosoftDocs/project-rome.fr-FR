---
title: MCDRemoteSystemConnectionInfo
description: Une classe qui fournit des informations sur une instance donnée de MCDAppServiceConnection complémentaires.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801401"
---
# <a name="class-mcdremotesystemconnectioninfo"></a><span data-ttu-id="c6bae-104">Classe `MCDRemoteSystemConnectionInfo`</span><span class="sxs-lookup"><span data-stu-id="c6bae-104">class `MCDRemoteSystemConnectionInfo`</span></span> 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

<span data-ttu-id="c6bae-105">Une classe qui fournit des informations complémentaires sur une donnée **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instance.</span><span class="sxs-lookup"><span data-stu-id="c6bae-105">A class that provides further information about a given **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instance.</span></span>

## <a name="properties"></a><span data-ttu-id="c6bae-106">Properties</span><span class="sxs-lookup"><span data-stu-id="c6bae-106">Properties</span></span>

### <a name="proximal"></a><span data-ttu-id="c6bae-107">proximal</span><span class="sxs-lookup"><span data-stu-id="c6bae-107">proximal</span></span>
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

<span data-ttu-id="c6bae-108">Indique si la connexion associée est une connexion PROXIMALE (**Oui**) ou non (**non**).</span><span class="sxs-lookup"><span data-stu-id="c6bae-108">Displays whether the associated connection is a proximal connection (**YES**) or not (**NO**).</span></span>

## <a name="constructors"></a><span data-ttu-id="c6bae-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="c6bae-109">Constructors</span></span>

### <a name="trycreatefromappserviceconnection"></a><span data-ttu-id="c6bae-110">tryCreateFromAppServiceConnection</span><span class="sxs-lookup"><span data-stu-id="c6bae-110">tryCreateFromAppServiceConnection</span></span>
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

<span data-ttu-id="c6bae-111">Crée une instance de cette classe à partir de la connexion de service d’application donnée.</span><span class="sxs-lookup"><span data-stu-id="c6bae-111">Creates an instance of this class from the given app service connection.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c6bae-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6bae-112">Parameters</span></span>
* `appServiceConnection` 

<span data-ttu-id="c6bae-113">Un **MCDAppServiceConnection** instance.</span><span class="sxs-lookup"><span data-stu-id="c6bae-113">An **MCDAppServiceConnection** instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="c6bae-114">Returns</span><span class="sxs-lookup"><span data-stu-id="c6bae-114">Returns</span></span>
<span data-ttu-id="c6bae-115">Retourne une instance de cette classe correspondant à la connexion de service d’application.</span><span class="sxs-lookup"><span data-stu-id="c6bae-115">Returns an instance of this class corresponding to the app service connection.</span></span>