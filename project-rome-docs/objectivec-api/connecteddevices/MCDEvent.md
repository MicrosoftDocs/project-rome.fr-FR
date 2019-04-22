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
# <a name="class-mcdevent"></a>Classe `MCDEvent` 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 Cette interface fournit un modèle d’événement simple. Événements de produisent des éléments consommés par les EventListeners.
Le flux des éléments d’événement est contrôlé par la MCDEventSubscription.

## <a name="methods"></a>Méthodes

### <a name="subscribe"></a>subscribe
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

S’abonner à un donné d’événements dans la plateforme d’appareils connectés.

#### <a name="parameters"></a>Paramètres 
* `listener` 

Écoutez MCDEventSubscriptions.

#### <a name="returns"></a>Returns
Une instance de la MCDEventSubscription.