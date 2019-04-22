---
title: MCDUserActivitySessionHistoryItem
description: Cette classe fournit l’heure de début et de fin un utilisateur a été engagée dans une activité particulière.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801631"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a><span data-ttu-id="38e86-104">Classe `MCDUserActivitySessionHistoryItem`</span><span class="sxs-lookup"><span data-stu-id="38e86-104">class `MCDUserActivitySessionHistoryItem`</span></span>

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

<span data-ttu-id="38e86-105">Cette classe fournit l’heure de début et de fin un utilisateur a été engagée dans une activité particulière.</span><span class="sxs-lookup"><span data-stu-id="38e86-105">This class provides the start and end time that a user was engaged in a particular activity.</span></span>


## <a name="properties"></a><span data-ttu-id="38e86-106">Properties</span><span class="sxs-lookup"><span data-stu-id="38e86-106">Properties</span></span>

### <a name="useractivity"></a><span data-ttu-id="38e86-107">UserActivity</span><span class="sxs-lookup"><span data-stu-id="38e86-107">userActivity</span></span>
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

<span data-ttu-id="38e86-108">L’activité des utilisateurs dont l’historique de cette instance de classe représente.</span><span class="sxs-lookup"><span data-stu-id="38e86-108">The user activity whose history this class instance represents.</span></span>

### <a name="starttime"></a><span data-ttu-id="38e86-109">startTime</span><span class="sxs-lookup"><span data-stu-id="38e86-109">startTime</span></span>
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

<span data-ttu-id="38e86-110">Heure de l’utilisateur démarrage attrayante dans l’activité associée.</span><span class="sxs-lookup"><span data-stu-id="38e86-110">The time when the user started engaging in the associated activity.</span></span>

### <a name="endtime"></a><span data-ttu-id="38e86-111">endTime</span><span class="sxs-lookup"><span data-stu-id="38e86-111">endTime</span></span>
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

<span data-ttu-id="38e86-112">L’heure lorsque l’utilisateur a arrêté impliqués dans l’activité associée.</span><span class="sxs-lookup"><span data-stu-id="38e86-112">The time when the user stopped engaging in the associated activity.</span></span>

### <a name="remotesystemid"></a><span data-ttu-id="38e86-113">remoteSystemId</span><span class="sxs-lookup"><span data-stu-id="38e86-113">remoteSystemId</span></span>
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

<span data-ttu-id="38e86-114">La chaîne indiquant l’id du système distant de l’appareil de l’utilisateur effectuant cette activité.</span><span class="sxs-lookup"><span data-stu-id="38e86-114">The string indicating the remote system id of the device the user engaged this activity on.</span></span>