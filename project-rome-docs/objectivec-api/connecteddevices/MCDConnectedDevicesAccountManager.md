---
title: MCDConnectedDevicesAccountManager
description: Fournit un point d’entrée unique pour toutes les fonctionnalités relatives aux comptes dans le Kit de développement.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908391"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a>Classe `MCDConnectedDevicesAccountManager` 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
Fournit un point d’entrée unique pour toutes les fonctionnalités relatives aux comptes dans le Kit de développement.

## <a name="properties"></a>Properties

### <a name="accesstokenrequested"></a>accessTokenRequested
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

Cet événement est déclenché lorsqu’il est nécessaire pour demander un jeton. Cet événement doit être souscrit et prêt à répondre avant toute demande est envoyée.

### <a name="accesstokeninvalidated"></a>accessTokenInvalidated
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

Cet événement est déclenché quand un consommateur de jeton signale une erreur de jeton. Le fournisseur de jetons doit actualiser son cache de jeton ou demander une nouvelle connexion utilisateur à corriger leur configuration de compte.

### <a name="allaccounts"></a>allAccounts
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

Tous les MCDConnectedDevicesAccount qui sont actuellement suivies par ce gestionnaire.

## <a name="methods"></a>Méthodes

### <a name="addaccountasync"></a>addAccountAsync
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

Ajoutez un gestionnaire de compte à compte, de rappel sera appelé lorsqu’elle est terminée.

#### <a name="parameters"></a>Paramètres 
* `callback`

Le résultat de rappel indique si Ajout du compte a réussi ou non. 

### <a name="removeaccountasync"></a>removeAccountAsync
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

Supprimer un compte de gestionnaire de compte, le rappel sera appelé lorsqu’elle est terminée.

#### <a name="parameters"></a>Paramètres 
* `callback` 

 Le résultat de rappel indique si la suppression du compte a réussi ou non. 