---
title: MCDAppServiceRequest
description: Représente un message entrant à partir d’une application / l’appareil distant à cette connexion de service d’application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907571"
---
# <a name="class-mcdappservicerequest"></a>Classe `MCDAppServiceRequest`

```
@interface MCDAppServiceRequest : NSObject
```
Représente un message entrant à partir d’une application / l’appareil distant à cette connexion de service d’application.

## <a name="properties"></a>Properties

### <a name="message"></a>message 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

Le message pour le service d’application à distance.

## <a name="methods"></a>Méthodes

### <a name="sendresponseasync"></a>sendResponseAsync 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

Envoie un message de réponse au service application distante qui a envoyé la demande.

#### <a name="parameters"></a>Paramètres
* `message` 

Le message pour le service d’application à distance.

* `completion`     

L’achèvement de l’opération asynchrone avec une valeur MCDAppServiceResponseStatus indiquant l’état de l’opération d’envoi.