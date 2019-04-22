---
title: MCDConnectedDevicesAccessTokenRequest
description: Demande de jeton d’accès de la relation contenant-contenu MCDConnectedDevicesAccount qui satisfait les étendues de relation contenant-contenus.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b1cd9b747e98d5e9ccf4885b33897e8c240d7673
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800831"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a>Classe `MCDConnectedDevicesAccessTokenRequest` 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
Demande de jeton d’accès de la relation contenant-contenu MCDConnectedDevicesAccount qui satisfait les étendues de relation contenant-contenus.

## <a name="properties"></a>Properties

### <a name="account"></a>compte
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

Le compte associé à cette MCDConnectedDevicesAccessTokenInvalidatedEventArgs.

### <a name="scopes"></a>Étendues
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

La liste des étendues pour laquelle le jeton doit couvrir lors de la génération.

## <a name="methods"></a>Méthodes

### <a name="completewithaccesstoken"></a>completeWithAccessToken
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

Si un jeton avec les étendues demandés a été généré avec succès, appelez cette méthode avec le jeton pour terminer la demande.

#### <a name="parameters"></a>Paramètres 
* `token` 

Jeton généré avec succès

### <a name="completewitherrormessage"></a>completeWithErrorMessage
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

Si un jeton avec les étendues demandées n’a pas été correctement généré pour une raison quelconque, appelez cette méthode avec un message à utiliser pour la journalisation.

#### <a name="parameters"></a>Paramètres 
* `errorMessage`

Message décrivant la raison pour laquelle le jeton a échoué.