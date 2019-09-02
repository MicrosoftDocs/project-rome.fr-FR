---
title: UserNotificationReaderOptions
description: Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801381"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="f8832-104">type`UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="f8832-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="f8832-105">Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.</span><span class="sxs-lookup"><span data-stu-id="f8832-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="f8832-106">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="f8832-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="f8832-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="f8832-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="f8832-108">Crée et Initialise une nouvelle instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="f8832-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="f8832-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="f8832-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="f8832-110">Crée et Initialise une nouvelle instance de UserNotificationReaderOptions avec les filtres et la position de début spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f8832-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="f8832-111">Properties</span><span class="sxs-lookup"><span data-stu-id="f8832-111">Properties</span></span>

|<span data-ttu-id="f8832-112">Nom</span><span class="sxs-lookup"><span data-stu-id="f8832-112">Name</span></span> | <span data-ttu-id="f8832-113">Description</span><span class="sxs-lookup"><span data-stu-id="f8832-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="f8832-114">StartPosition</span><span class="sxs-lookup"><span data-stu-id="f8832-114">StartPosition</span></span> |<span data-ttu-id="f8832-115">Obtient ou définit la position de départ de cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="f8832-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="f8832-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="f8832-116">StatusFilter</span></span> |<span data-ttu-id="f8832-117">Obtient ou définit le filtre d’État pour le lecteur de notifications utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="f8832-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="f8832-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="f8832-118">ReadStateFilter</span></span> |<span data-ttu-id="f8832-119">Obtient ou définit le filtre d’état de lecture défini pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="f8832-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="f8832-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="f8832-120">UserActionStateFilter</span></span>|<span data-ttu-id="f8832-121">Getor définit le filtre d’état des actions de l’utilisateur défini pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="f8832-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




