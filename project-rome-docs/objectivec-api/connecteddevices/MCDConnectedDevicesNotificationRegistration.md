---
title: MCDConnectedDevicesNotificationRegistration
description: Cette classe représente l’inscription de l’application avec un service de notification push (nécessaire pour certains scénarios de Project Rome).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908881"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a><span data-ttu-id="8022e-104">Classe `MCDConnectedDevicesNotificationRegistration`</span><span class="sxs-lookup"><span data-stu-id="8022e-104">class `MCDConnectedDevicesNotificationRegistration`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 <span data-ttu-id="8022e-105">Cette classe représente l’inscription de l’application avec un service de notification push (nécessaire pour certains scénarios de Project Rome).</span><span class="sxs-lookup"><span data-stu-id="8022e-105">This class represents the app's registration with a push notification service (necessary for some Project Rome scenarios).</span></span> <span data-ttu-id="8022e-106">Il communique cette information à la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="8022e-106">It conveys this information to the Connected Devices Platform.</span></span>

## <a name="properties"></a><span data-ttu-id="8022e-107">Properties</span><span class="sxs-lookup"><span data-stu-id="8022e-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="8022e-108">Type</span><span class="sxs-lookup"><span data-stu-id="8022e-108">type</span></span>
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

<span data-ttu-id="8022e-109">Les types de notifications dans cette configuration.</span><span class="sxs-lookup"><span data-stu-id="8022e-109">The type of notifications in this setup.</span></span>

### <a name="token"></a><span data-ttu-id="8022e-110">Jeton</span><span class="sxs-lookup"><span data-stu-id="8022e-110">token</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* token;`

<span data-ttu-id="8022e-111">Le jeton d’inscription.</span><span class="sxs-lookup"><span data-stu-id="8022e-111">The registration token.</span></span>

### <a name="appid"></a><span data-ttu-id="8022e-112">appId</span><span class="sxs-lookup"><span data-stu-id="8022e-112">appId</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

<span data-ttu-id="8022e-113">L’ID d’application pour l’inscription aux notifications push.</span><span class="sxs-lookup"><span data-stu-id="8022e-113">The app ID for push notification registration.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="8022e-114">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="8022e-114">appDisplayName</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

<span data-ttu-id="8022e-115">Le surnom d’application.</span><span class="sxs-lookup"><span data-stu-id="8022e-115">The app display name.</span></span> <span data-ttu-id="8022e-116">Il doit s’agir du nom de l’application qui a été utilisé pour l’inscription sur le portail de développement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8022e-116">This should be the name of the app that was used for registration on the Microsoft dev portal.</span></span>