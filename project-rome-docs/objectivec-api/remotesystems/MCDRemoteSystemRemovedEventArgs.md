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
# <a name="class-mcdremotesystemremovedeventargs"></a>Classe `MCDRemoteSystemRemovedEventArgs` 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

Arguments d’événement pour l’événement MCDRemoteSystemWatcher.remoteSystemRemoved.

## <a name="properties"></a>Properties

### <a name="remotesystem"></a>remoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

Le système distant MCDRemoteSystem qui a été supprimé. Ce système distant ne doit pas être utilisé après cet événement.