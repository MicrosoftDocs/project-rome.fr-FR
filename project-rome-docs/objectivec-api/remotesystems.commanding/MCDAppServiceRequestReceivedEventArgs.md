---
title: MCDAppServiceRequestReceivedEventArgs
description: Contient les données associées à un événement « demande reçue ».
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800641"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a>Classe `MCDAppServiceRequestReceivedEventArgs` 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
Contient les données associées à un événement « demande reçue ».

## <a name="properties"></a>Properties

### <a name="request"></a>demande
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

La demande envoyée par le périphérique distant.