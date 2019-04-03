---
title: MCDAppServiceRequestReceivedEventArgs
description: Contient les données associées à un événement « demande reçue ».
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908561"
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