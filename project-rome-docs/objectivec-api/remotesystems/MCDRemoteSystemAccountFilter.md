---
title: MCDRemoteSystemAccountFilter
description: Filtre pour les comptes découvrir des systèmes distants avec.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801551"
---
# <a name="class-mcdremotesystemaccountfilter"></a>Classe `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

Filtre pour les comptes découvrir des systèmes distants avec.

## <a name="properties"></a>Properties

### <a name="account"></a>compte
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

Le compte associé à cette MCDRemoteSystemAccountFilter.

## <a name="constructors"></a>Constructeurs

### <a name="filterwithaccount"></a>filterWithAccount
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Initialiser la classe avec le compte MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Paramètres 
* `account` 

Le compte MCDConnectedDevicesAccount utilisé.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemAccountFilter filtré à l’aide du compte.

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Initialiser la classe avec le compte MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Paramètres 
* `account` 

Le compte MCDConnectedDevicesAccount utilisé.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemAccountFilter initialisé filtrés à l’aide du compte.