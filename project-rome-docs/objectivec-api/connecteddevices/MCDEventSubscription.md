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
# <a name="class-mcdeventsubscription"></a>type `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
Cette interface fournit un abonnement aux événements simple.

## <a name="methods"></a>Méthodes

### <a name="cancel"></a>annuler
`- (void)cancel;`

Annule un abonnement aux événements. Après avoir effectué cet appel, le EventListener attaché ne recevra plus d’événements (les événements de vol peuvent toujours être remis).
Étant donné que la plupart des fonctionnalités ConnectedDevices sont effectuées en code natif, il est important de toujours s’assurer que Cancel est appelé ou WeakReferences sont utilisés pour garantir un nettoyage correct des ressources détenues par le EventListener.
