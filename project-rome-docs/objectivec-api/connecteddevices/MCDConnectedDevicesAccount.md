---
title: MCDConnectedDevicesAccount
description: En savoir plus sur la classe MCDConnectedDevicesAccount. Cette classe représente un compte d’utilisateur unique connu par une application.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: b3004681c2bcbb0ad9d5b1dcb15fe8a711773767
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761043"
---
# <a name="class-mcdconnecteddevicesaccount"></a>type `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

Cette classe représente un compte d’utilisateur unique connu par une application.

## <a name="properties"></a>Propriétés

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

Instance singleton du compte anonyme.

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

Identificateur unique de ce compte d’utilisateur.

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

Valeur MCDConnectedDevicesAccountType décrivant le type de compte.

## <a name="constructors"></a>Constructeurs

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.

#### <a name="parameters"></a>Paramètres 

* `accountId` 

Chaîne d’identificateur unique pour ce compte d’utilisateur.

`type` 

MCDConnectedDevicesAccountType du compte (dépend du fournisseur d’ID à partir duquel le compte provient).

#### <a name="returns"></a>Retours
Retourne un objet MCDConnectedDevicesAccount avec l’identificateur de compte.

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.

#### <a name="parameters"></a>Paramètres 
* `type`

MCDConnectedDevicesAccountType du compte (dépend du fournisseur d’ID à partir duquel le compte provient).

#### <a name="returns"></a>Retours
Retourne un objet MCDConnectedDevicesAccount initialisé avec l’identificateur de compte.