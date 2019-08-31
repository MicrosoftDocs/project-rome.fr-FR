---
title: UserNotification
description: Cette classe représente une notification utilisateur publiée par le serveur d’applications par le biais de notifications de graphique et reçue par le client d’application.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801591"
---
# <a name="class-usernotification"></a><span data-ttu-id="edd8c-104">type`UserNotification`</span><span class="sxs-lookup"><span data-stu-id="edd8c-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="edd8c-105">Cette classe représente une instance de notification d’utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="edd8c-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="edd8c-106">Une notification utilisateur est créée et publiée par votre serveur d’applications ciblé sur un utilisateur et distribuée à tous les points de terminaison d’appareil du même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="edd8c-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="edd8c-107">Une notification utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et l’utilisation d’une bannière de notification visuelle à l’aide des API de notification locales de la plateforme correspondante.</span><span class="sxs-lookup"><span data-stu-id="edd8c-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="edd8c-108">Properties</span><span class="sxs-lookup"><span data-stu-id="edd8c-108">Properties</span></span>

|<span data-ttu-id="edd8c-109">Name</span><span class="sxs-lookup"><span data-stu-id="edd8c-109">Name</span></span> | <span data-ttu-id="edd8c-110">Description</span><span class="sxs-lookup"><span data-stu-id="edd8c-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="edd8c-111">Id</span><span class="sxs-lookup"><span data-stu-id="edd8c-111">Id</span></span> |<span data-ttu-id="edd8c-112">Obtient l’ID unique spécifié par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="edd8c-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="edd8c-113">GroupId</span></span> |<span data-ttu-id="edd8c-114">Obtient l’ID de groupe spécifié par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="edd8c-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="edd8c-115">ExpirationTime</span></span> |<span data-ttu-id="edd8c-116">Obtient l’heure d’expiration de cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="edd8c-117">Priority</span><span class="sxs-lookup"><span data-stu-id="edd8c-117">Priority</span></span>|<span data-ttu-id="edd8c-118">Obtient la priorité spécifiée par le développeur pour cette notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="edd8c-119">Contenu</span><span class="sxs-lookup"><span data-stu-id="edd8c-119">Content</span></span>|<span data-ttu-id="edd8c-120">Obtient la charge utile de contenu pour cette notification, qui est une donnée arbitraire définie par le développeur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="edd8c-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="edd8c-121">ReadState</span></span>|<span data-ttu-id="edd8c-122">Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique que la notification est lue ou non.</span><span class="sxs-lookup"><span data-stu-id="edd8c-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="edd8c-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="edd8c-123">UserActionState</span></span>|<span data-ttu-id="edd8c-124">Obtient la valeur de l’état de l’action utilisateur pour une notification utilisateur afin de déterminer si la notification n’est pas interactive, fermée, activée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="edd8c-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="edd8c-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="edd8c-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="edd8c-126">SaveAsync ()</span><span class="sxs-lookup"><span data-stu-id="edd8c-126">SaveAsync()</span></span> 
<span data-ttu-id="edd8c-127">Cela doit être appelé lors de la publication des modifications de notification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd8c-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="edd8c-128">Cette méthode doit être appelée chaque fois que l’application modifie une propriété pouvant être mise à jour de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="edd8c-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```

