---
title: MCDAppServiceClosedEventArgs
description: Retourné par MCDAppServiceConnection.serviceClosed afin d’informer que la MCDAppServiceConnection a été fermée et de fournir une raison pour laquelle l’événement de fermeture.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909181"
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