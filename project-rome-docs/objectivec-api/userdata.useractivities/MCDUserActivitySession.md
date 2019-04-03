---
title: MCDUserActivitySession
description: Cette classe effectue le suivi d’une activité de l’utilisateur ([MCDUserActivity](MCDUserActivity.md) instance) pendant que l’utilisateur est engagé dans cette activité.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2ae85e637bb059e811a60e5bde5f33ea767c8314
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909631"
---
# <a name="class-mcduseractivitysession"></a><span data-ttu-id="01392-104">Classe `MCDUserActivitySession`</span><span class="sxs-lookup"><span data-stu-id="01392-104">class `MCDUserActivitySession`</span></span>

```
@interface MCDUserActivitySession : NSObject
```

<span data-ttu-id="01392-105">Cette classe effectue le suivi d’engagement pour une activité de l’utilisateur spécifié ([MCDUserActivity](MCDUserActivity.md) instance).</span><span class="sxs-lookup"><span data-stu-id="01392-105">This class tracks engagement for a specified user activity ([MCDUserActivity](MCDUserActivity.md) instance).</span></span>

<span data-ttu-id="01392-106">Un [MCDUserActivity](MCDUserActivity.md) est associé à une MCDUserActivitySession qui effectue le suivi de la durée pendant laquelle l’utilisateur est engagé dans cette activité.</span><span class="sxs-lookup"><span data-stu-id="01392-106">A [MCDUserActivity](MCDUserActivity.md) is associated with an MCDUserActivitySession which tracks how long the user is engaged in that activity.</span></span> <span data-ttu-id="01392-107">Par exemple, une activité telle que regarder un film peut apparaître activé et désactivé au cours de plusieurs jours.</span><span class="sxs-lookup"><span data-stu-id="01392-107">For example, an activity such as watching a movie can occur on-and-off over the course of multiple days.</span></span> <span data-ttu-id="01392-108">Lorsque l’utilisateur commence à la nouvelle activité de regarder un film, une MCDUserActivitySession doit être créée.</span><span class="sxs-lookup"><span data-stu-id="01392-108">When the user first starts the new activity of watching a movie, a MCDUserActivitySession must be created.</span></span> <span data-ttu-id="01392-109">Il doit être supprimé lorsque l’utilisateur bascule vers une autre activité.</span><span class="sxs-lookup"><span data-stu-id="01392-109">It should be disposed when the user switches to a different activity.</span></span> <span data-ttu-id="01392-110">Lorsque l’utilisateur reprend, l’application doit créer un autre **MCDUserActivitySession** à partir de la version d’origine [MCDUserActivity](MCDUserActivity.md) pour effectuer le suivi de l’activité tant que l’utilisateur est chargé d’observer le film.</span><span class="sxs-lookup"><span data-stu-id="01392-110">When the user resumes, the app should create another **MCDUserActivitySession** from the original [MCDUserActivity](MCDUserActivity.md) to track the activity as long as the user is watching the movie.</span></span>


## <a name="properties"></a><span data-ttu-id="01392-111">Properties</span><span class="sxs-lookup"><span data-stu-id="01392-111">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="01392-112">activityId</span><span class="sxs-lookup"><span data-stu-id="01392-112">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="01392-113">Un ID unique pour le MCDUserActivity associé à cette MCDUserActivitySession.</span><span class="sxs-lookup"><span data-stu-id="01392-113">A unique ID for the MCDUserActivity associated with this MCDUserActivitySession.</span></span>

## <a name="methods"></a><span data-ttu-id="01392-114">Méthodes</span><span class="sxs-lookup"><span data-stu-id="01392-114">Methods</span></span>

### <a name="stop"></a><span data-ttu-id="01392-115">stop</span><span class="sxs-lookup"><span data-stu-id="01392-115">stop</span></span>
`- (void)stop;`

<span data-ttu-id="01392-116">Arrête cette session de l’activité.</span><span class="sxs-lookup"><span data-stu-id="01392-116">Stops this activity session.</span></span> <span data-ttu-id="01392-117">Cela doit être appelée lorsque l’utilisateur n’est plus prend part à l’activité associée à cette session.</span><span class="sxs-lookup"><span data-stu-id="01392-117">This should be called when the user is no longer engaged in the activity associated with this session.</span></span>