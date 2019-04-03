---
title: MCDRemoteSystemAppRegistrationPublishResult
description: Une classe communique le résultat asynchrone de publication informations sur l’application système distant pour un compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909921"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a><span data-ttu-id="6e6a4-104">Classe `MCDRemoteSystemAppRegistrationPublishResult`</span><span class="sxs-lookup"><span data-stu-id="6e6a4-104">class `MCDRemoteSystemAppRegistrationPublishResult`</span></span> 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

<span data-ttu-id="6e6a4-105">Cette classe communique le résultat asynchrone de publication informations sur l’application système distant pour un compte.</span><span class="sxs-lookup"><span data-stu-id="6e6a4-105">This class communicates the async result of publishing remote system app information for an account.</span></span> <span data-ttu-id="6e6a4-106">Les États d’erreur communiqués via ce résultat doivent servir par l’application à la nouvelle tentative de publication en cas de certaines conditions transitoires telles que le réseau ne soit pas disponible.</span><span class="sxs-lookup"><span data-stu-id="6e6a4-106">The error statuses communicated through this result should be used by the app to retry publishing in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="6e6a4-107">Properties</span><span class="sxs-lookup"><span data-stu-id="6e6a4-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="6e6a4-108">status</span><span class="sxs-lookup"><span data-stu-id="6e6a4-108">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

<span data-ttu-id="6e6a4-109">Énumération d’état de l’opération de publication.</span><span class="sxs-lookup"><span data-stu-id="6e6a4-109">Status enum of the publish operation.</span></span>