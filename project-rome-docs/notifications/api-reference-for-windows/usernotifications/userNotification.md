---
title: UserNotification
description: Cette classe représente une notification utilisateur publiées par le serveur d’applications par le biais de Notifications de graphique et reçu par le client de l’application.
keywords: Microsoft, windows, des notifications de graphique, des conseils pour windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801591"
---
# <a name="class-usernotification"></a><span data-ttu-id="6b03a-104">Classe `UserNotification`</span><span class="sxs-lookup"><span data-stu-id="6b03a-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="6b03a-105">Cette classe représente une instance de la notification utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="6b03a-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="6b03a-106">Une notification de l’utilisateur est créée et publiée par votre serveur d’application ciblée sur un utilisateur, distribué à tous les points de terminaison de périphérique du même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="6b03a-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="6b03a-107">Une notification de l’utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et affichage d’une bannière de notification visuelle à l’aide des API de notification locale de la plateforme correspondante.</span><span class="sxs-lookup"><span data-stu-id="6b03a-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="6b03a-108">Properties</span><span class="sxs-lookup"><span data-stu-id="6b03a-108">Properties</span></span>

|<span data-ttu-id="6b03a-109">Nom</span><span class="sxs-lookup"><span data-stu-id="6b03a-109">Name</span></span> | <span data-ttu-id="6b03a-110">Description</span><span class="sxs-lookup"><span data-stu-id="6b03a-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="6b03a-111">Id</span><span class="sxs-lookup"><span data-stu-id="6b03a-111">Id</span></span> |<span data-ttu-id="6b03a-112">Obtient le développeur spécifié unique id pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b03a-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="6b03a-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="6b03a-113">GroupId</span></span> |<span data-ttu-id="6b03a-114">Obtient le développeur spécifié id de groupe pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b03a-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="6b03a-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="6b03a-115">ExpirationTime</span></span> |<span data-ttu-id="6b03a-116">Obtient le délai d’expiration pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b03a-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="6b03a-117">Priority</span><span class="sxs-lookup"><span data-stu-id="6b03a-117">Priority</span></span>|<span data-ttu-id="6b03a-118">Obtient le développeur spécifié priorité pour cette notification à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b03a-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="6b03a-119">Contenu</span><span class="sxs-lookup"><span data-stu-id="6b03a-119">Content</span></span>|<span data-ttu-id="6b03a-120">Obtient la charge utile de contenu pour cette notification, qui est défini de développeur des données arbitraires.</span><span class="sxs-lookup"><span data-stu-id="6b03a-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="6b03a-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="6b03a-121">ReadState</span></span>|<span data-ttu-id="6b03a-122">Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique la notification est lu ou non lu.</span><span class="sxs-lookup"><span data-stu-id="6b03a-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="6b03a-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="6b03a-123">UserActionState</span></span>|<span data-ttu-id="6b03a-124">Obtient la valeur de l’état d’action utilisateur pour une notification de l’utilisateur déterminer si la notification n'est pas interagie, fermée, activée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="6b03a-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="6b03a-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6b03a-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="6b03a-126">SaveAsync()</span><span class="sxs-lookup"><span data-stu-id="6b03a-126">SaveAsync()</span></span> 
<span data-ttu-id="6b03a-127">Cela doit être appelée lors de la publication des modifications de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b03a-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="6b03a-128">Cette méthode doit être appelée chaque fois que l’application modifie une propriété d’être mise à jour de la UserNotification.</span><span class="sxs-lookup"><span data-stu-id="6b03a-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```

