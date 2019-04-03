---
title: MCDConnectedDevicesProcessNotificationOperation
description: Le résultat de donner une notification à la plateforme Rome pour traitement.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: cb482e7b00cd5fe090de1708388d140cfd45777b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909891"
---
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a><span data-ttu-id="b2839-104">Classe `MCDConnectedDevicesProcessNotificationOperation`</span><span class="sxs-lookup"><span data-stu-id="b2839-104">class `MCDConnectedDevicesProcessNotificationOperation`</span></span> 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
<span data-ttu-id="b2839-105">Le résultat de donner une notification APNS à la plateforme d’appareils connectés pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="b2839-105">The result of giving an APNS notification to the Connected Devices platform for processing.</span></span>

> [!NOTE] 
> <span data-ttu-id="b2839-106">Cette classe est déconseillée, utilisez MCDConnectedDevicesNotification à la place.</span><span class="sxs-lookup"><span data-stu-id="b2839-106">This class is deprecated, use MCDConnectedDevicesNotification instead.</span></span> 

## <a name="properties"></a><span data-ttu-id="b2839-107">Properties</span><span class="sxs-lookup"><span data-stu-id="b2839-107">Properties</span></span>

### <a name="connecteddevicesnotification"></a><span data-ttu-id="b2839-108">connectedDevicesNotification</span><span class="sxs-lookup"><span data-stu-id="b2839-108">connectedDevicesNotification</span></span>
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

<span data-ttu-id="b2839-109">Il s’agit d’un indicateur qui spécifie si la notification a été conçue pour la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="b2839-109">This is a flag indicating whether the notification was intended for the Connected Devices platform.</span></span>

## <a name="methods"></a><span data-ttu-id="b2839-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b2839-110">Methods</span></span>

### <a name="waitforcompletionasync"></a><span data-ttu-id="b2839-111">waitForCompletionAsync</span><span class="sxs-lookup"><span data-stu-id="b2839-111">waitForCompletionAsync</span></span>
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 <span data-ttu-id="b2839-112">Attendez que la notification se termine en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="b2839-112">Wait for the notification to finish being handled.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b2839-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2839-113">Parameters</span></span> 
* `callback` 

<span data-ttu-id="b2839-114">Le résultat de rappel d’achèvement de la notification.</span><span class="sxs-lookup"><span data-stu-id="b2839-114">The callback result for notification completion.</span></span>
