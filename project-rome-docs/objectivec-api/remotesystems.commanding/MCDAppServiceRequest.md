---
title: MCDAppServiceRequest
description: Représente un message entrant à partir d’une application / l’appareil distant à cette connexion de service d’application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800531"
---
# <a name="class-mcdappservicerequest"></a><span data-ttu-id="68bc1-104">Classe `MCDAppServiceRequest`</span><span class="sxs-lookup"><span data-stu-id="68bc1-104">class `MCDAppServiceRequest`</span></span>

```
@interface MCDAppServiceRequest : NSObject
```
<span data-ttu-id="68bc1-105">Représente un message entrant à partir d’une application / l’appareil distant à cette connexion de service d’application.</span><span class="sxs-lookup"><span data-stu-id="68bc1-105">Represents an incoming message from a remote app/device to this app service connection.</span></span>

## <a name="properties"></a><span data-ttu-id="68bc1-106">Properties</span><span class="sxs-lookup"><span data-stu-id="68bc1-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="68bc1-107">message</span><span class="sxs-lookup"><span data-stu-id="68bc1-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="68bc1-108">Le message pour le service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="68bc1-108">The message for the remote app service.</span></span>

## <a name="methods"></a><span data-ttu-id="68bc1-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="68bc1-109">Methods</span></span>

### <a name="sendresponseasync"></a><span data-ttu-id="68bc1-110">sendResponseAsync</span><span class="sxs-lookup"><span data-stu-id="68bc1-110">sendResponseAsync</span></span> 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

<span data-ttu-id="68bc1-111">Envoie un message de réponse au service application distante qui a envoyé la demande.</span><span class="sxs-lookup"><span data-stu-id="68bc1-111">Sends a response message to the remote app service that sent the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="68bc1-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68bc1-112">Parameters</span></span>
* `message` 

<span data-ttu-id="68bc1-113">Le message pour le service d’application à distance.</span><span class="sxs-lookup"><span data-stu-id="68bc1-113">The message for the remote app service.</span></span>

* `completion`     

<span data-ttu-id="68bc1-114">L’achèvement de l’opération asynchrone avec une valeur MCDAppServiceResponseStatus indiquant l’état de l’opération d’envoi.</span><span class="sxs-lookup"><span data-stu-id="68bc1-114">The completion of the asynchronous operation with an MCDAppServiceResponseStatus value indicating the status of the send operation.</span></span>