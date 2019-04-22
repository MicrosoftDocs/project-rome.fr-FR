---
title: MCDConnectedDevicesNotification
description: Résultat du traitement d’une notification.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800601"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="44f87-104">Classe `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="44f87-104">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="44f87-105">Résultat du traitement d’une notification.</span><span class="sxs-lookup"><span data-stu-id="44f87-105">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="44f87-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="44f87-106">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="44f87-107">tryParse</span><span class="sxs-lookup"><span data-stu-id="44f87-107">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="44f87-108">Tentatives d’analyse une MCDConnectedDevicesNotification à partir d’un APNS mise en forme de carte.</span><span class="sxs-lookup"><span data-stu-id="44f87-108">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="44f87-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44f87-109">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="44f87-110">La carte a reçu de la notification APNS de la plateforme d’appareils connectés pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="44f87-110">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
