---
title: MCDRemoteSystemAccountFilter
description: Découvrez comment filtrer les comptes pour découvrir des systèmes distants à l’aide de constructeurs comme « filterwithAccount ».
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760723"
---
# <a name="class-mcdremotesystemaccountfilter"></a>type `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

Filtrez les comptes pour découvrir les systèmes distants.

## <a name="properties"></a>Propriétés

### <a name="account"></a>account
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

Compte associé à ce MCDRemoteSystemAccountFilter.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithaccount"></a>filterWithAccount
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Initialisez la classe avec le compte MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Paramètres 
* `account` 

Compte MCDConnectedDevicesAccount utilisé.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemAccountFilter filtré avec le compte.

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Initialisez la classe avec le compte MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Paramètres 
* `account` 

Compte MCDConnectedDevicesAccount utilisé.

#### <a name="returns"></a>Retours
Retourne un objet MCDRemoteSystemAccountFilter initialisé par le compte.