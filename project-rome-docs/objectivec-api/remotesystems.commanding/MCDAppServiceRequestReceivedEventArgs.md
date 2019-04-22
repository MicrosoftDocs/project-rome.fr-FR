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
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="d92e9-104">Classe `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="d92e9-104">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="d92e9-105">Contient les données associées à un événement « demande reçue ».</span><span class="sxs-lookup"><span data-stu-id="d92e9-105">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="d92e9-106">Properties</span><span class="sxs-lookup"><span data-stu-id="d92e9-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="d92e9-107">demande</span><span class="sxs-lookup"><span data-stu-id="d92e9-107">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="d92e9-108">La demande envoyée par le périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="d92e9-108">The request sent by the remote device.</span></span>