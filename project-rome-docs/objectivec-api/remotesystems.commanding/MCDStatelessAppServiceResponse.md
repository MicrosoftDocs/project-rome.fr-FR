---
title: MCDStatelessAppServiceResponse
description: Représente un message transmis à partir d’un service d’application à distance à l’application cliente en réponse à un appel précédent à MCDAppServiceConnection.sendStatelessMessageAsync.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907231"
---
# <a name="class-mcdstatelessappserviceresponse"></a><span data-ttu-id="e8236-104">Classe `MCDStatelessAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="e8236-104">class `MCDStatelessAppServiceResponse`</span></span> 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

<span data-ttu-id="e8236-105">Représente un message transmis à partir d’un service d’application à distance à l’application cliente en réponse à un appel précédent à MCDAppServiceConnection.sendStatelessMessageAsync.</span><span class="sxs-lookup"><span data-stu-id="e8236-105">Represents a message passed from a remote app service to the client app in response to a previous call to MCDAppServiceConnection.sendStatelessMessageAsync.</span></span>


## <a name="properties"></a><span data-ttu-id="e8236-106">Properties</span><span class="sxs-lookup"><span data-stu-id="e8236-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="e8236-107">message</span><span class="sxs-lookup"><span data-stu-id="e8236-107">message</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="e8236-108">Le message envoyé par le service d’application à distance, constitué de paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="e8236-108">The message sent by the remote app service, consisting of key/value pairs.</span></span>

### <a name="status"></a><span data-ttu-id="e8236-109">status</span><span class="sxs-lookup"><span data-stu-id="e8236-109">status</span></span>
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

<span data-ttu-id="e8236-110">L’état de la réponse à partir du service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="e8236-110">The status of the response from the remote app service.</span></span>

