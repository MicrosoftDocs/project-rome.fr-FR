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
# <a name="class-mcdremotesystemremovedeventargs"></a>Classe `MCDRemoteSystemRemovedEventArgs` 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

Arguments d’événement pour l’événement MCDRemoteSystemWatcher.remoteSystemRemoved.

## <a name="properties"></a>Properties

### <a name="remotesystem"></a>remoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

Le système distant MCDRemoteSystem qui a été supprimé. Ce système distant ne doit pas être utilisé après cet événement.