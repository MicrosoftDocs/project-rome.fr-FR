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
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="431a6-104">Classe `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="431a6-104">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="431a6-105">Contient les données associées à un événement « demande reçue ».</span><span class="sxs-lookup"><span data-stu-id="431a6-105">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="431a6-106">Properties</span><span class="sxs-lookup"><span data-stu-id="431a6-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="431a6-107">demande</span><span class="sxs-lookup"><span data-stu-id="431a6-107">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="431a6-108">La demande envoyée par le périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="431a6-108">The request sent by the remote device.</span></span>