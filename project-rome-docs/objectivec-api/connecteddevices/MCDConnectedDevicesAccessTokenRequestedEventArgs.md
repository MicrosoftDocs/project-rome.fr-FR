---
title: MCDConnectedDevicesAccessTokenRequestedEventArgs
description: Retourné par MCDConnectedDevicesAccessTokenRequested, déclenché lorsqu’il est nécessaire pour demander un jeton.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d50b7dc75944e3c3df553c95247b0ec578a477a4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908321"
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