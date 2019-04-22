---
title: MCDAppServiceConnectionOpenedInfo
description: Cette classe fournit des données pour l’événement MCDAppServiceProvider.connectionDidOpen, qui est déclenché quand un appareil distant ouvre une connexion à un service de l’application locale.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801071"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a><span data-ttu-id="142c0-104">Classe `MCDAppServiceConnectionOpenedInfo`</span><span class="sxs-lookup"><span data-stu-id="142c0-104">class `MCDAppServiceConnectionOpenedInfo`</span></span> 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

<span data-ttu-id="142c0-105">Cette classe fournit des données pour l’événement MCDAppServiceProvider.connectionDidOpen, qui est déclenché quand un appareil distant ouvre une connexion à un service de l’application locale.</span><span class="sxs-lookup"><span data-stu-id="142c0-105">This class provides data for the MCDAppServiceProvider.connectionDidOpen event, which is raised when a remote device opens a connection to a local app service.</span></span>

## <a name="properties"></a><span data-ttu-id="142c0-106">Properties</span><span class="sxs-lookup"><span data-stu-id="142c0-106">Properties</span></span>

### <a name="appserviceconnection"></a><span data-ttu-id="142c0-107">appServiceConnection</span><span class="sxs-lookup"><span data-stu-id="142c0-107">appServiceConnection</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

<span data-ttu-id="142c0-108">Une instance de MCDAppServiceConnection qui représente la connexion entre le service d’application local et le périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="142c0-108">An MCDAppServiceConnection instance representing the connection between the local app service and the remote device.</span></span>

### <a name="remotesystemapp"></a><span data-ttu-id="142c0-109">remoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="142c0-109">remoteSystemApp</span></span>
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

<span data-ttu-id="142c0-110">L’application distante MCDRemoteSystemApp qui a lancé une connexion au service d’application local.</span><span class="sxs-lookup"><span data-stu-id="142c0-110">The MCDRemoteSystemApp remote application that initiated a connection to the local app service.</span></span>