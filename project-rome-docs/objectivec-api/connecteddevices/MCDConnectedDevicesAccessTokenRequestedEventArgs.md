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
# <a name="class-mcdconnecteddevicesaccesstokenrequestedeventargs"></a><span data-ttu-id="b868f-104">Classe `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="b868f-104">class `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequestedEventArgs : NSObject
```  

<span data-ttu-id="b868f-105">Retourné par MCDConnectedDevicesAccessTokenRequested, déclenché lorsqu’il est nécessaire pour demander un jeton.</span><span class="sxs-lookup"><span data-stu-id="b868f-105">Returned by MCDConnectedDevicesAccessTokenRequested, fired when there is a need to request a token.</span></span> 

## <a name="properties"></a><span data-ttu-id="b868f-106">Properties</span><span class="sxs-lookup"><span data-stu-id="b868f-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="b868f-107">demande</span><span class="sxs-lookup"><span data-stu-id="b868f-107">request</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccessTokenRequest* request;`

<span data-ttu-id="b868f-108">La demande associée à cette MCDConnectedDevicesAccessTokenRequest.</span><span class="sxs-lookup"><span data-stu-id="b868f-108">The request associated with this MCDConnectedDevicesAccessTokenRequest.</span></span>