---
title: MCDAppServiceResponse
description: Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800791"
---
# <a name="class-mcdappserviceresponse"></a><span data-ttu-id="8a456-104">Classe `MCDAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="8a456-104">class `MCDAppServiceResponse`</span></span>

```
@interface MCDAppServiceResponse : NSObject
```

<span data-ttu-id="8a456-105">Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.</span><span class="sxs-lookup"><span data-stu-id="8a456-105">A class that represents a response received from a connected remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="8a456-106">Properties</span><span class="sxs-lookup"><span data-stu-id="8a456-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="8a456-107">message</span><span class="sxs-lookup"><span data-stu-id="8a456-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="8a456-108">Le message reçu à partir du service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="8a456-108">The message received from the remote app service.</span></span>

### <a name="status"></a><span data-ttu-id="8a456-109">status</span><span class="sxs-lookup"><span data-stu-id="8a456-109">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

<span data-ttu-id="8a456-110">L’état de la réponse reçue.</span><span class="sxs-lookup"><span data-stu-id="8a456-110">The status of the response received.</span></span>