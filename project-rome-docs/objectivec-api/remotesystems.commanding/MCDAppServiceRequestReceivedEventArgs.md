---
title: MCDAppServiceRequestReceivedEventArgs
description: En savoir plus sur la classe MCDAppServiceRequestReceivedEventArgs. Cette classe contient des données associées à un événement « Request received ».
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 9a4a64ae163a0cc553196914da2f42d8d32e6ade
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760763"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a>type `MCDAppServiceRequestReceivedEventArgs` 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
Contient les données associées à un événement « Request received ».

## <a name="properties"></a>Propriétés

### <a name="request"></a>request
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

Demande envoyée par le périphérique distant.