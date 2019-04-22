---
title: MCDUserDataFeedSyncScope
description: Cette classe représente les données utilisateur qui sont synchronisées avec le backend de la plateforme de périphériques connectés lorsque l’application utilise certaines fonctionnalités de périphériques spécifiques à l’utilisateur.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801001"
---
# <a name="class-mcduserdatafeedsyncscope"></a><span data-ttu-id="17ec8-104">Classe `MCDUserDataFeedSyncScope`</span><span class="sxs-lookup"><span data-stu-id="17ec8-104">class `MCDUserDataFeedSyncScope`</span></span>

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 <span data-ttu-id="17ec8-105">Cette interface représente les données utilisateur qui sont synchronisées avec le backend de la plateforme de périphériques connectés lorsque l’application utilise certaines fonctionnalités des appareils connectés spécifiques à l’utilisateur, tels que les activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="17ec8-105">This interface represents the user data that is synchronized with the Connected Devices Platform backend when the app uses certain user-specific Connected Devices functionality, such as user activities.</span></span> <span data-ttu-id="17ec8-106">Une instance est récupérée statiquement à partir de la classe qui gère ce type de fonctionnalité (par exemple, **MCDUserActivityChannel**), et il est utilisé dans la construction de **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="17ec8-106">An instance is retrieved statically from the class that manages such functionality (e.g. **MCDUserActivityChannel**), and it is used in the construction of **MCDUserDataFeed**.</span></span>

## <a name="properties"></a><span data-ttu-id="17ec8-107">Properties</span><span class="sxs-lookup"><span data-stu-id="17ec8-107">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="17ec8-108">Plateforme</span><span class="sxs-lookup"><span data-stu-id="17ec8-108">platform</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

<span data-ttu-id="17ec8-109">Le **ConnectedDevicesPlatform** instance qui a été initialisé pour les fonctionnalités des appareils connectés de cette application.</span><span class="sxs-lookup"><span data-stu-id="17ec8-109">The **ConnectedDevicesPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

### <a name="syncscopeflags"></a><span data-ttu-id="17ec8-110">syncScopeFlags</span><span class="sxs-lookup"><span data-stu-id="17ec8-110">syncScopeFlags</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

<span data-ttu-id="17ec8-111">Définir des indicateurs facultatifs pour le filtrage des activités entrantes.</span><span class="sxs-lookup"><span data-stu-id="17ec8-111">Set any optional flags for filtering incoming activities.</span></span>

### <a name="notificationtype"></a><span data-ttu-id="17ec8-112">notificationType</span><span class="sxs-lookup"><span data-stu-id="17ec8-112">notificationType</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

<span data-ttu-id="17ec8-113">Définir le type de modifier le type de notification pour recevoir de l’étendue de la synchronisation de flux de données d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="17ec8-113">Set type of change notification type to receive for user data feed sync scope</span></span>

```