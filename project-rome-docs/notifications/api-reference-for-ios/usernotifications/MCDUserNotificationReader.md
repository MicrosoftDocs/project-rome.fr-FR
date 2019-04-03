---
title: MCDUserNotificationReader
description: Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour. Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.
keywords: Microsoft, windows, relais de l’appareil, iOS procédures, procédures iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909021"
---
# <a name="class-mcdusernotificationreader"></a>Classe `MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

Cette classe fournit les nouvelles notifications utilisateur entrantes et notification utilisateur mises à jour. Il donne également accès à la collection de l’utilisateur notifications conservées dans la plateforme d’appareils connectés.  

## <a name="properties"></a>Properties

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

Retourne l’état actuel du lecteur de modification. Peut être utilisé pour construire un nouveau lecteur à partir de l’état.
Basé sur le dernier lot terminé de modifications de notification (ou état initial, si aucun terminées avec succès).

### <a name="datachanged"></a>dataChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

Abonnement aux événements pour MCDUserNotificationReader modifié.

## <a name="methods"></a>Méthodes

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

Lire les modifications de notification, y compris les nouvelles notifications entrantes et les mises à jour sur les notifications existantes dans le lot.