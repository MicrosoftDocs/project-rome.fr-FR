---
title: MCDRemoteSystemRemovedEventArgs
description: Arguments d’événement pour l’événement RemoteSystemWatcher RemoteSystemRemoved.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907041"
---
# <a name="class-mcdremotesystemremovedeventargs"></a><span data-ttu-id="83bdd-104">Classe `MCDRemoteSystemRemovedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="83bdd-104">class `MCDRemoteSystemRemovedEventArgs`</span></span> 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

<span data-ttu-id="83bdd-105">Arguments d’événement pour l’événement MCDRemoteSystemWatcher.remoteSystemRemoved.</span><span class="sxs-lookup"><span data-stu-id="83bdd-105">Event arguments for the MCDRemoteSystemWatcher.remoteSystemRemoved event.</span></span>

## <a name="properties"></a><span data-ttu-id="83bdd-106">Properties</span><span class="sxs-lookup"><span data-stu-id="83bdd-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="83bdd-107">remoteSystem</span><span class="sxs-lookup"><span data-stu-id="83bdd-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="83bdd-108">Le système distant MCDRemoteSystem qui a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="83bdd-108">The MCDRemoteSystem remote system that was removed.</span></span> <span data-ttu-id="83bdd-109">Ce système distant ne doit pas être utilisé après cet événement.</span><span class="sxs-lookup"><span data-stu-id="83bdd-109">This remote system should not be used after this event.</span></span>