---
title: MCDConnectedDevicesNotification
description: En savoir plus sur la classe MCDConnectedDevicesNotification. Cette classe est le résultat du traitement d’une notification.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761013"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="d8678-105">type `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="d8678-105">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="d8678-106">Résultat du traitement d’une notification.</span><span class="sxs-lookup"><span data-stu-id="d8678-106">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="d8678-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d8678-107">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="d8678-108">tryParse</span><span class="sxs-lookup"><span data-stu-id="d8678-108">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="d8678-109">Tente d’analyser un MCDConnectedDevicesNotification à partir d’une carte mise en forme APNS.</span><span class="sxs-lookup"><span data-stu-id="d8678-109">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d8678-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8678-110">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="d8678-111">Carte reçue de la notification APNS à la plateforme d’appareils connectés pour traitement.</span><span class="sxs-lookup"><span data-stu-id="d8678-111">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
