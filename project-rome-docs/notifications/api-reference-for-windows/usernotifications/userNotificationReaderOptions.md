---
title: UserNotificationReaderOptions
description: Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.
keywords: Microsoft, windows, les Notifications de graphique, les procédures relatives à Windows
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801381"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="a920d-104">Classe `UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="a920d-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="a920d-105">Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="a920d-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="a920d-106">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a920d-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="a920d-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="a920d-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="a920d-108">Crée et initialise une nouvelle instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a920d-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="a920d-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="a920d-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="a920d-110">Crée et initialise une nouvelle instance de UserNotificationReaderOptions avec les filtres et la position de début spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a920d-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="a920d-111">Properties</span><span class="sxs-lookup"><span data-stu-id="a920d-111">Properties</span></span>

|<span data-ttu-id="a920d-112">Nom</span><span class="sxs-lookup"><span data-stu-id="a920d-112">Name</span></span> | <span data-ttu-id="a920d-113">Description</span><span class="sxs-lookup"><span data-stu-id="a920d-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="a920d-114">StartPosition</span><span class="sxs-lookup"><span data-stu-id="a920d-114">StartPosition</span></span> |<span data-ttu-id="a920d-115">Obtient ou définit la position de départ pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a920d-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="a920d-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="a920d-116">StatusFilter</span></span> |<span data-ttu-id="a920d-117">Obtient ou définit le filtre d’état pour ce lecteur de notification utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="a920d-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="a920d-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="a920d-118">ReadStateFilter</span></span> |<span data-ttu-id="a920d-119">Obtient ou définit le filtre d’état de lecture qui est défini pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a920d-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="a920d-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="a920d-120">UserActionStateFilter</span></span>|<span data-ttu-id="a920d-121">Getor définir le filtre d’état utilisateur action définie pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a920d-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




