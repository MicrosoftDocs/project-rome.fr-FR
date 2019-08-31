---
title: MCDUserNotification
description: Cette classe représente une notification utilisateur publiée par le serveur d’applications par le biais de notifications de graphique et reçue par le client d’application.
keywords: notifications Microsoft, iOS, Graph, procédures iOS, iPhone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907891"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="51cfb-104">type`MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="51cfb-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="51cfb-105">Cette classe représente une instance de notification d’utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="51cfb-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="51cfb-106">Une notification utilisateur est créée et publiée par votre serveur d’applications ciblé sur un utilisateur et distribuée à tous les points de terminaison d’appareil du même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="51cfb-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="51cfb-107">Une notification utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et l’utilisation d’une bannière de notification visuelle à l’aide des API de notification locales de la plateforme correspondante.</span><span class="sxs-lookup"><span data-stu-id="51cfb-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="51cfb-108">Properties</span><span class="sxs-lookup"><span data-stu-id="51cfb-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="51cfb-109">ID</span><span class="sxs-lookup"><span data-stu-id="51cfb-109">notificationId</span></span>
<span data-ttu-id="51cfb-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;`Obtient l’ID unique spécifié par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="51cfb-111">groupId</span><span class="sxs-lookup"><span data-stu-id="51cfb-111">groupId</span></span>
<span data-ttu-id="51cfb-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;`Obtient l’ID de groupe spécifié par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="51cfb-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="51cfb-113">expirationTime</span></span>
<span data-ttu-id="51cfb-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`Obtient l’heure d’expiration de cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="51cfb-115">status</span><span class="sxs-lookup"><span data-stu-id="51cfb-115">status</span></span>
<span data-ttu-id="51cfb-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;`Obtient l’état de la notification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="51cfb-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="51cfb-117">changeTime</span></span>
<span data-ttu-id="51cfb-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`Obtient l’heure à laquelle la modification a été apportée.</span><span class="sxs-lookup"><span data-stu-id="51cfb-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="51cfb-119">priority</span><span class="sxs-lookup"><span data-stu-id="51cfb-119">priority</span></span>
<span data-ttu-id="51cfb-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`Obtient la priorité spécifiée par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="51cfb-121">content</span><span class="sxs-lookup"><span data-stu-id="51cfb-121">content</span></span>
<span data-ttu-id="51cfb-122">`@property(nonatomic, readonly, nonnull) NSString* content;`Obtient la charge utile de contenu pour cette notification, qui est une donnée arbitraire définie par le développeur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="51cfb-123">readState</span><span class="sxs-lookup"><span data-stu-id="51cfb-123">readState</span></span>
<span data-ttu-id="51cfb-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique que la notification est lue ou non.</span><span class="sxs-lookup"><span data-stu-id="51cfb-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="51cfb-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="51cfb-125">userActionState</span></span>
<span data-ttu-id="51cfb-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`Obtient la valeur de l’état de l’action utilisateur pour une notification utilisateur afin de déterminer si la notification n’est pas interactive, fermée, activée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="51cfb-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="51cfb-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="51cfb-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="51cfb-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="51cfb-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="51cfb-129">Cela doit être appelé lors de la publication des modifications de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51cfb-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="51cfb-130">Cette méthode doit être appelée chaque fois que l’application modifie une propriété pouvant être mise à jour de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="51cfb-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="51cfb-131">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51cfb-131">Parameters</span></span>
* <span data-ttu-id="51cfb-132">`completion`Bloc de code à exécuter à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="51cfb-132">`completion` The code block to execute upon completion.</span></span>
