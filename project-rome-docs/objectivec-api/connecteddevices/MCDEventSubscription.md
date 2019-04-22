---
title: MCDEventSubscription
description: Cette interface fournit un abonnement d’événement simple.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: ce5a5782f80b54e78a6e3890cd68d9e92c52226c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801613"
---
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="738b7-104">Classe `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="738b7-104">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="738b7-105">Cette interface fournit un abonnement d’événement simple.</span><span class="sxs-lookup"><span data-stu-id="738b7-105">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="738b7-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="738b7-106">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="738b7-107">annuler</span><span class="sxs-lookup"><span data-stu-id="738b7-107">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="738b7-108">Annule un abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="738b7-108">Cancels an event subscription.</span></span> <span data-ttu-id="738b7-109">Après avoir apporté cet appel, le EventListener attaché ne recevra pas de tous les événements plus (Already in événements de vol peut toujours être remis).</span><span class="sxs-lookup"><span data-stu-id="738b7-109">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="738b7-110">Étant donné que la plupart des fonctionnalités ConnectedDevices s’effectue en code natif, il est important de toujours vérifier Annuler est appelée ou WeakReferences sont utilisés pour garantir la correcte de nettoyage des ressources détenues par le EventListener.</span><span class="sxs-lookup"><span data-stu-id="738b7-110">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
