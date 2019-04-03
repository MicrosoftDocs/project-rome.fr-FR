---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: Informer de ce jeton associé ConnectedDevicesAccount a signalé une erreur de jeton.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907491"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a>Classe `MCDConnectedDevicesAccessTokenInvalidatedEventArgs` 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
Retourné par MCDConnectedDevicesAccount pour informer que le jeton associé MCDConnectedDevicesAccount a signalé une erreur de jeton pour les étendues de relation contenant-contenus. Fournisseur de jetons doit actualiser son cache de jeton ou potentiellement affiche l’interface utilisateur de demander à l’utilisateur pour se connecter afin de corriger leur configuration de compte.

## <a name="properties"></a>Properties

### <a name="account"></a>compte
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

Le compte associé à cette MCDConnectedDevicesAccessTokenInvalidatedEventArgs.

### <a name="scopes"></a>Étendues
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

La liste des étendues pour laquelle le jeton doit couvrir lors de la génération.