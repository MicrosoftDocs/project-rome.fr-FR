---
title: MCDConnectedDevicesAccountType
description: Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801511"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a>Enum `MCDConnectedDevicesAccountType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountTypeAAD       | 0     | Workplace Active Directory Azure compte  |
| MCDConnectedDevicesAccountTypeMSA       | 1     | Compte du personnel de Microsoft |
| MCDConnectedDevicesAccountTypeAnonymous | 2     | Compte anonyme de (local, non authentifié) |