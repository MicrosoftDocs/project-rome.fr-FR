---
title: UserNotificationReaderOptions
description: Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.
keywords: Microsoft, windows, les Notifications de graphique, les procédures relatives à Windows
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909681"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="9c39e-104">Classe `UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="9c39e-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="9c39e-105">Cette classe permet à l’application fournir des options sur le lecteur de notification, par exemple recevoir uniquement des nouvelles notifications d’utilisateur et les mises à jour de notification n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="9c39e-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="9c39e-106">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9c39e-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="9c39e-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="9c39e-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="9c39e-108">Crée et initialise une nouvelle instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9c39e-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="9c39e-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="9c39e-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="9c39e-110">Crée et initialise une nouvelle instance de UserNotificationReaderOptions avec les filtres et la position de début spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9c39e-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="9c39e-111">Properties</span><span class="sxs-lookup"><span data-stu-id="9c39e-111">Properties</span></span>

|<span data-ttu-id="9c39e-112">Nom</span><span class="sxs-lookup"><span data-stu-id="9c39e-112">Name</span></span> | <span data-ttu-id="9c39e-113">Description</span><span class="sxs-lookup"><span data-stu-id="9c39e-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="9c39e-114">StartPosition</span><span class="sxs-lookup"><span data-stu-id="9c39e-114">StartPosition</span></span> |<span data-ttu-id="9c39e-115">Obtient ou définit la position de départ pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9c39e-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="9c39e-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="9c39e-116">StatusFilter</span></span> |<span data-ttu-id="9c39e-117">Obtient ou définit le filtre d’état pour ce lecteur de notification utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="9c39e-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="9c39e-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="9c39e-118">ReadStateFilter</span></span> |<span data-ttu-id="9c39e-119">Obtient ou définit le filtre d’état de lecture qui est défini pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9c39e-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="9c39e-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="9c39e-120">UserActionStateFilter</span></span>|<span data-ttu-id="9c39e-121">Getor définir le filtre d’état utilisateur action définie pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9c39e-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




