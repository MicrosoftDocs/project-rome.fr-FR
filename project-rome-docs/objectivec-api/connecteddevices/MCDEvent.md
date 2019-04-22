---
title: MCDEvent
description: Cette interface fournit un modèle d’événement simple. Événements de produisent des éléments consommés par les EventListeners.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: eabe9464a104593b06460153ed30f42f7cc103eb
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801391"
---
# <a name="class-mcdevent"></a><span data-ttu-id="f441f-105">Classe `MCDEvent`</span><span class="sxs-lookup"><span data-stu-id="f441f-105">class `MCDEvent`</span></span> 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 <span data-ttu-id="f441f-106">Cette interface fournit un modèle d’événement simple.</span><span class="sxs-lookup"><span data-stu-id="f441f-106">This interface provides a simple event model.</span></span> <span data-ttu-id="f441f-107">Événements de produisent des éléments consommés par les EventListeners.</span><span class="sxs-lookup"><span data-stu-id="f441f-107">Events produce items consumed by EventListeners.</span></span>
<span data-ttu-id="f441f-108">Le flux des éléments d’événement est contrôlé par la MCDEventSubscription.</span><span class="sxs-lookup"><span data-stu-id="f441f-108">The flow of event items is controlled by the MCDEventSubscription.</span></span>

## <a name="methods"></a><span data-ttu-id="f441f-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f441f-109">Methods</span></span>

### <a name="subscribe"></a><span data-ttu-id="f441f-110">subscribe</span><span class="sxs-lookup"><span data-stu-id="f441f-110">subscribe</span></span>
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

<span data-ttu-id="f441f-111">S’abonner à un donné d’événements dans la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="f441f-111">Subscribe to given events in the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f441f-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f441f-112">Parameters</span></span> 
* `listener` 

<span data-ttu-id="f441f-113">Écoutez MCDEventSubscriptions.</span><span class="sxs-lookup"><span data-stu-id="f441f-113">Listen to MCDEventSubscriptions.</span></span>

#### <a name="returns"></a><span data-ttu-id="f441f-114">Returns</span><span class="sxs-lookup"><span data-stu-id="f441f-114">Returns</span></span>
<span data-ttu-id="f441f-115">Une instance de la MCDEventSubscription.</span><span class="sxs-lookup"><span data-stu-id="f441f-115">An instance of the MCDEventSubscription.</span></span>