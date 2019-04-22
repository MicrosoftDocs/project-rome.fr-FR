---
title: MCDUserNotificationReader
description: Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour. Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.
keywords: Microsoft, windows, relais de l’appareil, iOS procédures, procédures iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800731"
---
# <a name="class-mcdusernotificationreader"></a><span data-ttu-id="6cc01-105">Classe `MCDUserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="6cc01-105">class `MCDUserNotificationReader`</span></span>

```
@interface MCDUserNotificationReader : NSObject
```

<span data-ttu-id="6cc01-106">Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour.</span><span class="sxs-lookup"><span data-stu-id="6cc01-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="6cc01-107">Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="6cc01-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="properties"></a><span data-ttu-id="6cc01-108">Properties</span><span class="sxs-lookup"><span data-stu-id="6cc01-108">Properties</span></span>

### <a name="serializedstate"></a><span data-ttu-id="6cc01-109">serializedState</span><span class="sxs-lookup"><span data-stu-id="6cc01-109">serializedState</span></span>
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

<span data-ttu-id="6cc01-110">Retourne l’état actuel du lecteur de modification.</span><span class="sxs-lookup"><span data-stu-id="6cc01-110">Returns the current state of the change reader.</span></span> <span data-ttu-id="6cc01-111">Peut être utilisé pour construire un nouveau lecteur à partir de l’état.</span><span class="sxs-lookup"><span data-stu-id="6cc01-111">Can be used to construct a new reader starting from the same state.</span></span>
<span data-ttu-id="6cc01-112">Basé sur le dernier lot terminé de modifications de notification (ou état initial, si aucun terminées avec succès).</span><span class="sxs-lookup"><span data-stu-id="6cc01-112">Based upon the last completed batch of notification changes (or initial state, if none have completed successfully).</span></span>

### <a name="datachanged"></a><span data-ttu-id="6cc01-113">dataChanged</span><span class="sxs-lookup"><span data-stu-id="6cc01-113">dataChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

<span data-ttu-id="6cc01-114">Abonnement aux événements pour MCDUserNotificationReader modifié.</span><span class="sxs-lookup"><span data-stu-id="6cc01-114">Event subscription for MCDUserNotificationReader changed.</span></span>

## <a name="methods"></a><span data-ttu-id="6cc01-115">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6cc01-115">Methods</span></span>

### <a name="readbatchasyncwithmaxsize"></a><span data-ttu-id="6cc01-116">readBatchAsyncWithMaxSize</span><span class="sxs-lookup"><span data-stu-id="6cc01-116">readBatchAsyncWithMaxSize</span></span>
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="6cc01-117">Lire les modifications de notification, y compris les nouvelles notifications entrantes et les mises à jour sur les notifications existantes dans le lot.</span><span class="sxs-lookup"><span data-stu-id="6cc01-117">Read notification changes including new incoming notifications and updates on existing notifications in batch.</span></span>