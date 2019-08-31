---
title: MCDUserNotificationReader
description: Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur. Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.
keywords: Microsoft, Windows, appareil Relay, procédure iOS, iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800731"
---
# <a name="class-mcdusernotificationreader"></a><span data-ttu-id="5a2bb-105">type`MCDUserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="5a2bb-105">class `MCDUserNotificationReader`</span></span>

```
@interface MCDUserNotificationReader : NSObject
```

<span data-ttu-id="5a2bb-106">Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="5a2bb-107">Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="properties"></a><span data-ttu-id="5a2bb-108">Properties</span><span class="sxs-lookup"><span data-stu-id="5a2bb-108">Properties</span></span>

### <a name="serializedstate"></a><span data-ttu-id="5a2bb-109">serializedState</span><span class="sxs-lookup"><span data-stu-id="5a2bb-109">serializedState</span></span>
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

<span data-ttu-id="5a2bb-110">Retourne l’état actuel du lecteur de modifications.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-110">Returns the current state of the change reader.</span></span> <span data-ttu-id="5a2bb-111">Peut être utilisé pour construire un nouveau lecteur démarrant à partir du même État.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-111">Can be used to construct a new reader starting from the same state.</span></span>
<span data-ttu-id="5a2bb-112">En fonction du dernier lot terminé de modifications de notification (ou de l’état initial, si aucune n’a été effectuée avec succès).</span><span class="sxs-lookup"><span data-stu-id="5a2bb-112">Based upon the last completed batch of notification changes (or initial state, if none have completed successfully).</span></span>

### <a name="datachanged"></a><span data-ttu-id="5a2bb-113">dataChanged</span><span class="sxs-lookup"><span data-stu-id="5a2bb-113">dataChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

<span data-ttu-id="5a2bb-114">L’abonnement aux événements pour MCDUserNotificationReader a changé.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-114">Event subscription for MCDUserNotificationReader changed.</span></span>

## <a name="methods"></a><span data-ttu-id="5a2bb-115">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5a2bb-115">Methods</span></span>

### <a name="readbatchasyncwithmaxsize"></a><span data-ttu-id="5a2bb-116">readBatchAsyncWithMaxSize</span><span class="sxs-lookup"><span data-stu-id="5a2bb-116">readBatchAsyncWithMaxSize</span></span>
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="5a2bb-117">Lire les modifications de notification, notamment les nouvelles notifications entrantes et les mises à jour sur les notifications existantes dans batch.</span><span class="sxs-lookup"><span data-stu-id="5a2bb-117">Read notification changes including new incoming notifications and updates on existing notifications in batch.</span></span>