---
title: MCDUserNotificationReaderOptions
description: Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.
keywords: Microsoft, Windows, notifications de graphiques, procédures iOS, iPhone de savoir-faire
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907981"
---
# <a name="class-mcdusernotificationreaderoptions"></a><span data-ttu-id="12397-104">type`MCDUserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="12397-104">class `MCDUserNotificationReaderOptions`</span></span>

```
@interface MCDUserNotificationReaderOptions : NSObject
```

<span data-ttu-id="12397-105">Cette classe permet à l’application de fournir des options sur le lecteur de notification, telles que la réception de nouvelles notifications utilisateur et non les mises à jour de notification existantes.</span><span class="sxs-lookup"><span data-stu-id="12397-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="properties"></a><span data-ttu-id="12397-106">Properties</span><span class="sxs-lookup"><span data-stu-id="12397-106">Properties</span></span>

### <a name="startposition"></a><span data-ttu-id="12397-107">startPosition</span><span class="sxs-lookup"><span data-stu-id="12397-107">startPosition</span></span>
<span data-ttu-id="12397-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`Obtient ou définit la position de départ de cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="12397-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>

### <a name="statusfilter"></a><span data-ttu-id="12397-109">statusFilter</span><span class="sxs-lookup"><span data-stu-id="12397-109">statusFilter</span></span>
<span data-ttu-id="12397-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`Obtient ou définit le filtre d’État pour le lecteur de notifications utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="12397-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Get or set the status filter for this user notification reader you desire to create.</span></span>

### <a name="readstatefilter"></a><span data-ttu-id="12397-111">readStateFilter</span><span class="sxs-lookup"><span data-stu-id="12397-111">readStateFilter</span></span>
<span data-ttu-id="12397-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`Obtient ou définit le filtre d’état de lecture défini pour cette instance de UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="12397-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions</span></span>

### <a name="useractionstatefilter"></a><span data-ttu-id="12397-113">userActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="12397-113">userActionStateFilter</span></span>
<span data-ttu-id="12397-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`Getor définit le filtre d’état des actions de l’utilisateur défini pour cette instance de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="12397-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>

## <a name="constructors"></a><span data-ttu-id="12397-115">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="12397-115">Constructors</span></span>

### <a name="options"></a><span data-ttu-id="12397-116">options</span><span class="sxs-lookup"><span data-stu-id="12397-116">options</span></span>
<span data-ttu-id="12397-117">`+ (nullable instancetype)options;`Crée et Initialise une nouvelle instance d’options pour les notifications utilisateur.</span><span class="sxs-lookup"><span data-stu-id="12397-117">`+ (nullable instancetype)options;` Creates and initializes a new instance of options for User Notifications.</span></span>