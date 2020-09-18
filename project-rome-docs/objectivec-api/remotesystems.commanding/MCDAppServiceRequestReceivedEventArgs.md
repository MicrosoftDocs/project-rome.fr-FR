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
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="ccc3c-105">type `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="ccc3c-105">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="ccc3c-106">Contient les données associées à un événement « Request received ».</span><span class="sxs-lookup"><span data-stu-id="ccc3c-106">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="ccc3c-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ccc3c-107">Properties</span></span>

### <a name="request"></a><span data-ttu-id="ccc3c-108">request</span><span class="sxs-lookup"><span data-stu-id="ccc3c-108">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="ccc3c-109">Demande envoyée par le périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="ccc3c-109">The request sent by the remote device.</span></span>