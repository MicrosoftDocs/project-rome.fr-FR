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
# <a name="class-mcdusernotificationreader"></a>type`MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

Cette classe fournit les nouvelles notifications utilisateur entrantes et les mises à jour des notifications utilisateur. Il permet également d’accéder à la collection de notifications utilisateur conservées dans la plateforme d’appareil connectée.  

## <a name="properties"></a>Properties

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

Retourne l’état actuel du lecteur de modifications. Peut être utilisé pour construire un nouveau lecteur démarrant à partir du même État.
En fonction du dernier lot terminé de modifications de notification (ou de l’état initial, si aucune n’a été effectuée avec succès).

### <a name="datachanged"></a>dataChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

L’abonnement aux événements pour MCDUserNotificationReader a changé.

## <a name="methods"></a>Méthodes

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

Lire les modifications de notification, notamment les nouvelles notifications entrantes et les mises à jour sur les notifications existantes dans batch.