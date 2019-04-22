---
title: MCDConnectedDevicesAccessTokenRequestedEventArgs
description: Retourné par MCDConnectedDevicesAccessTokenRequested, déclenché lorsqu’il est nécessaire pour demander un jeton.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d50b7dc75944e3c3df553c95247b0ec578a477a4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800741"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequestedeventargs"></a>Classe `MCDConnectedDevicesAccessTokenRequestedEventArgs` 

```
@interface MCDConnectedDevicesAccessTokenRequestedEventArgs : NSObject
```  

Retourné par MCDConnectedDevicesAccessTokenRequested, déclenché lorsqu’il est nécessaire pour demander un jeton. 

## <a name="properties"></a>Properties

### <a name="request"></a>demande
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccessTokenRequest* request;`

La demande associée à cette MCDConnectedDevicesAccessTokenRequest.