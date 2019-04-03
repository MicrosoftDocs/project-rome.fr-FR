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
# <a name="protocol-mcdappserviceprovider"></a><span data-ttu-id="75d36-104">Protocole `MCDAppServiceProvider`</span><span class="sxs-lookup"><span data-stu-id="75d36-104">protocol `MCDAppServiceProvider`</span></span>

```
@protocol MCDAppServiceProvider<NSObject>
```

<span data-ttu-id="75d36-105">Ce protocole contient des méthodes pour rendre un service local d’application accessibles aux appareils distants.</span><span class="sxs-lookup"><span data-stu-id="75d36-105">This protocol contains methods for making a local app service accessible to remote devices.</span></span> <span data-ttu-id="75d36-106">Les développeurs doivent implémenter ce protocole pour rendre leurs services d’application disponible pour la connectivité à distance.</span><span class="sxs-lookup"><span data-stu-id="75d36-106">Developers must implement this protocol to make their app services available for remote connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="75d36-107">Properties</span><span class="sxs-lookup"><span data-stu-id="75d36-107">Properties</span></span>
 
### <a name="appserviceinfo"></a><span data-ttu-id="75d36-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="75d36-108">appServiceInfo</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="75d36-109">Les informations descriptives sur ce service de l’application.</span><span class="sxs-lookup"><span data-stu-id="75d36-109">The descriptive information about this app service.</span></span>

## <a name="methods"></a><span data-ttu-id="75d36-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="75d36-110">Methods</span></span>

### <a name="connectiondidopen"></a><span data-ttu-id="75d36-111">connectionDidOpen</span><span class="sxs-lookup"><span data-stu-id="75d36-111">connectionDidOpen</span></span>
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

<span data-ttu-id="75d36-112">Cette méthode est appelée lorsqu’une connexion de service application distante est ouverte à ce service de l’application.</span><span class="sxs-lookup"><span data-stu-id="75d36-112">This method is called when a remote app service connection is opened to this app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="75d36-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75d36-113">Parameters</span></span> 
* `openedInfo`

<span data-ttu-id="75d36-114">Une instance de MDCAppServiceConnectionOpenedInfo contenant des informations pour la messagerie à distance avec le service d’application.</span><span class="sxs-lookup"><span data-stu-id="75d36-114">A MDCAppServiceConnectionOpenedInfo instance containing information for remote messaging with the app service.</span></span>