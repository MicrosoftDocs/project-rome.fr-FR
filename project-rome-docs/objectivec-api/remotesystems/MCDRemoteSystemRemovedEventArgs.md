---
title: MCDRemoteSystemRemovedEventArgs
description: Arguments d’événement pour l’événement RemoteSystemWatcher RemoteSystemRemoved.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801731"
---
# <a name="class-mcdremotesystemremovedeventargs"></a><span data-ttu-id="adee3-104">Classe `MCDRemoteSystemRemovedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="adee3-104">class `MCDRemoteSystemRemovedEventArgs`</span></span> 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

<span data-ttu-id="adee3-105">Arguments d’événement pour l’événement MCDRemoteSystemWatcher.remoteSystemRemoved.</span><span class="sxs-lookup"><span data-stu-id="adee3-105">Event arguments for the MCDRemoteSystemWatcher.remoteSystemRemoved event.</span></span>

## <a name="properties"></a><span data-ttu-id="adee3-106">Properties</span><span class="sxs-lookup"><span data-stu-id="adee3-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="adee3-107">remoteSystem</span><span class="sxs-lookup"><span data-stu-id="adee3-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="adee3-108">Le système distant MCDRemoteSystem qui a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="adee3-108">The MCDRemoteSystem remote system that was removed.</span></span> <span data-ttu-id="adee3-109">Ce système distant ne doit pas être utilisé après cet événement.</span><span class="sxs-lookup"><span data-stu-id="adee3-109">This remote system should not be used after this event.</span></span>