---
title: MCDAppServiceClosedEventArgs
description: Retourné par MCDAppServiceConnection.serviceClosed afin d’informer que la MCDAppServiceConnection a été fermée et de fournir une raison pour laquelle l’événement de fermeture.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801291"
---
# <a name="class-mcdappserviceclosedeventargs"></a>Classe `MCDAppServiceClosedEventArgs` 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

Retourné par MCDAppServiceConnection.serviceClosed afin d’informer que la MCDAppServiceConnection a été fermée et de fournir une raison pour laquelle l’événement de fermeture.

## <a name="properties"></a>Properties

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

L’état de la façon dont le service d’application est fermé.