---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: Classe d’arguments événement pour l’événement MCDConnectedDevicesNotificationRegistration état modifié.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800691"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a><span data-ttu-id="8fffb-104">Classe `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="8fffb-104">class `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
<span data-ttu-id="8fffb-105">Classe d’arguments événement pour l’événement MCDConnectedDevicesNotificationRegistration état modifié.</span><span class="sxs-lookup"><span data-stu-id="8fffb-105">Event Args class for the MCDConnectedDevicesNotificationRegistration State Changed event.</span></span> <span data-ttu-id="8fffb-106">Cela permet de garantir que l’application obtient informée sur les nouveaux messages de plateforme d’appareils connectés via le mécanisme de notification correct.</span><span class="sxs-lookup"><span data-stu-id="8fffb-106">This is used to ensure that the application gets informed about new Connected Devices platform messages via the correct notification mechanism.</span></span>

## <a name="properties"></a><span data-ttu-id="8fffb-107">Properties</span><span class="sxs-lookup"><span data-stu-id="8fffb-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="8fffb-108">compte</span><span class="sxs-lookup"><span data-stu-id="8fffb-108">account</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="8fffb-109">Le compte pour lequel l’état d’inscription de notification a été modifiée pour.</span><span class="sxs-lookup"><span data-stu-id="8fffb-109">The Account for which the notification registration state has changed for.</span></span>

### <a name="registration"></a><span data-ttu-id="8fffb-110">registration</span><span class="sxs-lookup"><span data-stu-id="8fffb-110">registration</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

<span data-ttu-id="8fffb-111">Les informations pour l’inscription de l’instance dont l’état a changé.</span><span class="sxs-lookup"><span data-stu-id="8fffb-111">The information for registration instance whose state has changed.</span></span>

### <a name="state"></a><span data-ttu-id="8fffb-112">État</span><span class="sxs-lookup"><span data-stu-id="8fffb-112">state</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

<span data-ttu-id="8fffb-113">Le nouvel état de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="8fffb-113">The new registration state.</span></span>