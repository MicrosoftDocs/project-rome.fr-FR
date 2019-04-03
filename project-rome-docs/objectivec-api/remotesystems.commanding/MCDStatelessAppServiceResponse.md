---
title: MCDStatelessAppServiceResponse
description: Représente un message transmis à partir d’un service d’application à distance à l’application cliente en réponse à un appel précédent à MCDAppServiceConnection.sendStatelessMessageAsync.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907231"
---
# <a name="class-mcdstatelessappserviceresponse"></a>Classe `MCDStatelessAppServiceResponse` 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

Représente un message transmis à partir d’un service d’application à distance à l’application cliente en réponse à un appel précédent à MCDAppServiceConnection.sendStatelessMessageAsync.


## <a name="properties"></a>Properties

### <a name="message"></a>message
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

Le message envoyé par le service d’application à distance, constitué de paires clé/valeur.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

L’état de la réponse à partir du service d’application à distance.

