---
title: MCDRemoteSystemConnectionRequest
description: Une classe qui représente une tentative de communication avec un périphérique distant spécifique ou une application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907131"
---
# <a name="class-mcdremotesystemconnectionrequest"></a>Classe `MCDRemoteSystemConnectionRequest` 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

Une classe qui représente une tentative de communication avec un périphérique distant spécifique ou une application.

## <a name="constructors"></a>Constructeurs

### <a name="requestwithremotesystem"></a>requestWithRemoteSystem
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

Initialise le [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) avec un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance. Ce constructeur n’est pas recommandé, car il ne spécifie pas une application à la cible et par conséquent, peut entraîner une application inattendue sélectionnée pour traiter les demandes envoyées au système.

#### <a name="parameters"></a>Paramètres
* `remoteSystem` 

Le système distant à cibler dans cette demande de connexion.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.

### <a name="requestwithremotesystemapp"></a>requestWithRemoteSystemApp
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

Crée et initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `remoteSystemApp` 

L’application distante à cibler dans cette demande de connexion.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.

### <a name="initwithremotesystem"></a>initWithRemoteSystem
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

Initialise le [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) avec un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance. Ce constructeur n’est pas recommandé, car il ne spécifie pas une application à la cible et par conséquent, peut entraîner une application inattendue sélectionnée pour traiter les demandes envoyées au système.

#### <a name="parameters"></a>Paramètres
* `remoteSystem` Le système distant à cibler dans cette demande de connexion.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.

### <a name="initwithremotesystemapp"></a>initWithRemoteSystemApp
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

Crée et initialise une nouvelle instance de cette classe.

#### <a name="parameters"></a>Paramètres
* `remoteSystemApp` 

L’application distante à cibler dans cette demande de connexion.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.