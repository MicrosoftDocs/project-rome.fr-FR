---
title: MCDRemoteSystemUpdatedEventArgs
description: Arguments d’événement pour l’événement de remoteSystemUpdated MCDRemoteSystemWatcher.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 3bd52c73fcc8bc28f766b7f6261d726c65f938f9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801231"
---
# <a name="class-mcdremotesystemupdatedeventargs"></a><span data-ttu-id="26a02-104">Classe `MCDRemoteSystemUpdatedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="26a02-104">class `MCDRemoteSystemUpdatedEventArgs`</span></span> 

```
@interface MCDRemoteSystemUpdatedEventArgs : NSObject
```  

<span data-ttu-id="26a02-105">Arguments d’événement pour l’événement de remoteSystemUpdated MCDRemoteSystemWatcher.</span><span class="sxs-lookup"><span data-stu-id="26a02-105">Event arguments for the MCDRemoteSystemWatcher remoteSystemUpdated event.</span></span>

## <a name="properties"></a><span data-ttu-id="26a02-106">Properties</span><span class="sxs-lookup"><span data-stu-id="26a02-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="26a02-107">remoteSystem</span><span class="sxs-lookup"><span data-stu-id="26a02-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="26a02-108">Le système distant MCDRemoteSystem qui a été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="26a02-108">The MCDRemoteSystem remote system that was updated.</span></span>