---
title: MCDAppServiceResponse
description: Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909201"
---
# <a name="class-mcdappserviceresponse"></a><span data-ttu-id="5c292-104">Classe `MCDAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="5c292-104">class `MCDAppServiceResponse`</span></span>

```
@interface MCDAppServiceResponse : NSObject
```

<span data-ttu-id="5c292-105">Une classe qui représente une réponse reçue à partir d’un service d’application distant connectée.</span><span class="sxs-lookup"><span data-stu-id="5c292-105">A class that represents a response received from a connected remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="5c292-106">Properties</span><span class="sxs-lookup"><span data-stu-id="5c292-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="5c292-107">message</span><span class="sxs-lookup"><span data-stu-id="5c292-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="5c292-108">Le message reçu à partir du service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="5c292-108">The message received from the remote app service.</span></span>

### <a name="status"></a><span data-ttu-id="5c292-109">status</span><span class="sxs-lookup"><span data-stu-id="5c292-109">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

<span data-ttu-id="5c292-110">L’état de la réponse reçue.</span><span class="sxs-lookup"><span data-stu-id="5c292-110">The status of the response received.</span></span>