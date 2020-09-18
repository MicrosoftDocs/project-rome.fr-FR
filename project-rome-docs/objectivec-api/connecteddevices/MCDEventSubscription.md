---
title: MCDEventSubscription
description: En savoir plus sur la classe MCDEventSubscription. Cette interface fournit un moyen simple de gérer un abonnement aux événements.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8f44d1ca75ea247f2cb26fe5b2c136b4db0bd97f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761073"
---
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="2d77b-105">type `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="2d77b-105">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="2d77b-106">Cette interface fournit un abonnement aux événements simple.</span><span class="sxs-lookup"><span data-stu-id="2d77b-106">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="2d77b-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2d77b-107">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="2d77b-108">annuler</span><span class="sxs-lookup"><span data-stu-id="2d77b-108">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="2d77b-109">Annule un abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="2d77b-109">Cancels an event subscription.</span></span> <span data-ttu-id="2d77b-110">Après avoir effectué cet appel, le EventListener attaché ne recevra plus d’événements (les événements de vol peuvent toujours être remis).</span><span class="sxs-lookup"><span data-stu-id="2d77b-110">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="2d77b-111">Étant donné que la plupart des fonctionnalités ConnectedDevices sont effectuées en code natif, il est important de toujours s’assurer que Cancel est appelé ou WeakReferences sont utilisés pour garantir un nettoyage correct des ressources détenues par le EventListener.</span><span class="sxs-lookup"><span data-stu-id="2d77b-111">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
