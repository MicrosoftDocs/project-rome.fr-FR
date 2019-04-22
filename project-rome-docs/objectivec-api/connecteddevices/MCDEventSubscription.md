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
# <a name="class-mcdeventsubscription"></a>Classe `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
Cette interface fournit un abonnement d’événement simple.

## <a name="methods"></a>Méthodes

### <a name="cancel"></a>annuler
`- (void)cancel;`

Annule un abonnement aux événements. Après avoir apporté cet appel, le EventListener attaché ne recevra pas de tous les événements plus (Already in événements de vol peut toujours être remis).
Étant donné que la plupart des fonctionnalités ConnectedDevices s’effectue en code natif, il est important de toujours vérifier Annuler est appelée ou WeakReferences sont utilisés pour garantir la correcte de nettoyage des ressources détenues par le EventListener.
