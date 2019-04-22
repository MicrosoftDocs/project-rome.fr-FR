---
title: MCDConnectedDevicesAccount
description: Cette classe représente un seul compte d’utilisateur connu par une application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800931"
---
# <a name="class-mcdconnecteddevicesaccount"></a>Classe `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

Cette classe représente un seul compte d’utilisateur connu par une application.

## <a name="properties"></a>Properties

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

L’instance singleton du compte anonyme.

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

Identificateur unique pour ce compte d’utilisateur.

### <a name="type"></a>Type
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

Une valeur MCDConnectedDevicesAccountType décrivant le type de compte.

## <a name="constructors"></a>Constructeurs

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Une nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.

#### <a name="parameters"></a>Paramètres 

* `accountId` 

Une chaîne d’identificateur unique pour ce compte d’utilisateur.

`type` 

Le MCDConnectedDevicesAccountType du compte (repose sur le fournisseur de l’ID du compte provient de).

#### <a name="returns"></a>Returns
Retourne un objet MCDConnectedDevicesAccount avec l’identificateur de compte.

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Une nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.

#### <a name="parameters"></a>Paramètres 
* `type`

Le MCDConnectedDevicesAccountType du compte (repose sur le fournisseur de l’ID du compte provient de).

#### <a name="returns"></a>Returns
Retourne un objet MCDConnectedDevicesAccount initialisé avec le compte.