---
title: MCDAppServiceResponse
description: Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800791"
---
# <a name="class-mcdappserviceresponse"></a>Classe `MCDAppServiceResponse`

```
@interface MCDAppServiceResponse : NSObject
```

Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.

## <a name="properties"></a>Properties

### <a name="message"></a>message 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

Le message reçu à partir du service d’application à distance.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

L’état de la réponse reçue.