---
title: MCDUserNotification
description: Cette classe représente une notification utilisateur publiées par le serveur d’applications par le biais de Notifications de graphique et reçu par le client de l’application.
keywords: Microsoft, ios, notifications de graphique, ios procédures, procédures iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907891"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="89e77-104">Classe `MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="89e77-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="89e77-105">Cette classe représente une instance de la notification utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="89e77-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="89e77-106">Une notification de l’utilisateur est créée et publiée par votre serveur d’application ciblée sur un utilisateur, distribué à tous les points de terminaison de périphérique du même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="89e77-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="89e77-107">Une notification de l’utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et affichage d’une bannière de notification visuelle à l’aide des API de notification locale de la plateforme correspondante.</span><span class="sxs-lookup"><span data-stu-id="89e77-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="89e77-108">Properties</span><span class="sxs-lookup"><span data-stu-id="89e77-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="89e77-109">notificationId</span><span class="sxs-lookup"><span data-stu-id="89e77-109">notificationId</span></span>
<span data-ttu-id="89e77-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Obtient le développeur spécifié unique id pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="89e77-111">groupId</span><span class="sxs-lookup"><span data-stu-id="89e77-111">groupId</span></span>
<span data-ttu-id="89e77-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Obtient le développeur spécifié id de groupe pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="89e77-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="89e77-113">expirationTime</span></span>
<span data-ttu-id="89e77-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Obtient le délai d’expiration pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="89e77-115">status</span><span class="sxs-lookup"><span data-stu-id="89e77-115">status</span></span>
<span data-ttu-id="89e77-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Obtient l’état de la notification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="89e77-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="89e77-117">changeTime</span></span>
<span data-ttu-id="89e77-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Obtient l’heure de que la modification a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="89e77-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="89e77-119">priority</span><span class="sxs-lookup"><span data-stu-id="89e77-119">priority</span></span>
<span data-ttu-id="89e77-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Obtient le développeur spécifié priorité pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="89e77-121">content</span><span class="sxs-lookup"><span data-stu-id="89e77-121">content</span></span>
<span data-ttu-id="89e77-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Obtient la charge utile de contenu pour cette notification, qui est défini de développeur des données arbitraires.</span><span class="sxs-lookup"><span data-stu-id="89e77-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="89e77-123">readState</span><span class="sxs-lookup"><span data-stu-id="89e77-123">readState</span></span>
<span data-ttu-id="89e77-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique la notification est lu ou non lu.</span><span class="sxs-lookup"><span data-stu-id="89e77-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="89e77-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="89e77-125">userActionState</span></span>
<span data-ttu-id="89e77-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Obtient la valeur de l’état d’action utilisateur pour une notification de l’utilisateur déterminer si la notification n'est pas interagie, fermée, activée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="89e77-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="89e77-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="89e77-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="89e77-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="89e77-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="89e77-129">Cela doit être appelée lors de la publication des modifications de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e77-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="89e77-130">Cette méthode doit être appelée chaque fois que l’application modifie une propriété d’être mise à jour de la UserNotification.</span><span class="sxs-lookup"><span data-stu-id="89e77-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="89e77-131">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89e77-131">Parameters</span></span>
* <span data-ttu-id="89e77-132">`completion` Le bloc de code à exécuter en cas de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="89e77-132">`completion` The code block to execute upon completion.</span></span>
