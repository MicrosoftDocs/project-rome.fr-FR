---
title: MCDConnectedDevicesNotificationRegistrationResult
description: Communique le résultat asynchrone de l’inscription des informations de notification pour un compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801351"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a><span data-ttu-id="d3a08-104">Classe `MCDConnectedDevicesNotificationRegistrationResult`</span><span class="sxs-lookup"><span data-stu-id="d3a08-104">class `MCDConnectedDevicesNotificationRegistrationResult`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
<span data-ttu-id="d3a08-105">MCDConnectedDevicesNotificationRegistrationResult communique le résultat asynchrone de l’inscription des informations de notification pour un compte.</span><span class="sxs-lookup"><span data-stu-id="d3a08-105">MCDConnectedDevicesNotificationRegistrationResult communicates the async result of registering notification information for an account.</span></span> <span data-ttu-id="d3a08-106">Les États d’erreur communiqués via ce résultat doivent servir par l’application à l’inscription de nouvelle tentative en cas de certaines conditions transitoires telles que le réseau ne soit pas disponible.</span><span class="sxs-lookup"><span data-stu-id="d3a08-106">The error statuses communicated through this result should be used by the app to retry registration in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="d3a08-107">Properties</span><span class="sxs-lookup"><span data-stu-id="d3a08-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="d3a08-108">status</span><span class="sxs-lookup"><span data-stu-id="d3a08-108">status</span></span>

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

<span data-ttu-id="d3a08-109">Énumération d’état de l’opération d’inscription.</span><span class="sxs-lookup"><span data-stu-id="d3a08-109">Status enum of the registration operation.</span></span>