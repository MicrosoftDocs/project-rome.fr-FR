---
title: MCDAppServiceProvider
description: Ce protocole contient des méthodes pour rendre un service local d’application accessibles aux appareils distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: f5af56a2c87e3b4335a2a59a0130ef3622af6c26
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908661"
---
# <a name="protocol-mcdappserviceprovider"></a>Protocole `MCDAppServiceProvider`

```
@protocol MCDAppServiceProvider<NSObject>
```

Ce protocole contient des méthodes pour rendre un service local d’application accessibles aux appareils distants. Les développeurs doivent implémenter ce protocole pour rendre leurs services d’application disponible pour la connectivité à distance.

## <a name="properties"></a>Properties
 
### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

Les informations descriptives sur ce service de l’application.

## <a name="methods"></a>Méthodes

### <a name="connectiondidopen"></a>connectionDidOpen
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

Cette méthode est appelée lorsqu’une connexion de service application distante est ouverte à ce service de l’application.

#### <a name="parameters"></a>Paramètres 
* `openedInfo`

Une instance de MDCAppServiceConnectionOpenedInfo contenant des informations pour la messagerie à distance avec le service d’application.