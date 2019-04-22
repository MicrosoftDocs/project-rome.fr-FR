---
title: MCDAppServiceClosedEventArgs
description: Retourné par MCDAppServiceConnection.serviceClosed afin d’informer que la MCDAppServiceConnection a été fermée et de fournir une raison pour laquelle l’événement de fermeture.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801291"
---
# <a name="class-mcdappserviceclosedeventargs"></a><span data-ttu-id="78df8-104">Classe `MCDAppServiceClosedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="78df8-104">class `MCDAppServiceClosedEventArgs`</span></span> 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

<span data-ttu-id="78df8-105">Retourné par MCDAppServiceConnection.serviceClosed afin d’informer que la MCDAppServiceConnection a été fermée et de fournir une raison pour laquelle l’événement de fermeture.</span><span class="sxs-lookup"><span data-stu-id="78df8-105">Returned by MCDAppServiceConnection.serviceClosed to inform that the MCDAppServiceConnection has been closed and provide a reason behind the close event.</span></span>

## <a name="properties"></a><span data-ttu-id="78df8-106">Properties</span><span class="sxs-lookup"><span data-stu-id="78df8-106">Properties</span></span>

### <a name="status"></a><span data-ttu-id="78df8-107">status</span><span class="sxs-lookup"><span data-stu-id="78df8-107">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

<span data-ttu-id="78df8-108">L’état de la façon dont le service d’application est fermé.</span><span class="sxs-lookup"><span data-stu-id="78df8-108">The status of how the app service closed.</span></span>