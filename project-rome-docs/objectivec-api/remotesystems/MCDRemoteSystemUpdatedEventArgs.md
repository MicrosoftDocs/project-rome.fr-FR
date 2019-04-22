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
# <a name="class-mcdremotesystemupdatedeventargs"></a>Classe `MCDRemoteSystemUpdatedEventArgs` 

```
@interface MCDRemoteSystemUpdatedEventArgs : NSObject
```  

Arguments d’événement pour l’événement de remoteSystemUpdated MCDRemoteSystemWatcher.

## <a name="properties"></a>Properties

### <a name="remotesystem"></a>remoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

Le système distant MCDRemoteSystem qui a été mis à jour.