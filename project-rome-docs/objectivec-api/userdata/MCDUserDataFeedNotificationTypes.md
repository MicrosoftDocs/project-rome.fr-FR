---
title: MCDUserDataFeedNotificationTypes
description: En savoir plus sur la classe MCDUserDataFeedNotificationTypes. Cette classe est chargée de fournir les types de notifications.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a9bb9b41309e32a429926c52769da9bc767ef5bc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760983"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>type `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

Cette classe fournit les types de notification valides pour MCDUserDataFeedSyncScope. notificationType.


## <a name="properties"></a>Propriétés

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

Représente les notifications push entrantes.  Il n’existe aucun rescrictions pour les notifications push autres que les restrictions de domaine/serveur.

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

Rétrograder toutes les notifications push vers une notification uniquement indiquant au système de se synchroniser pour recevoir les données, même si les données peuvent être contenues dans la notification push.


### <a name="nonotification"></a>nonotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

Empêcher les notifications pour les nouvelles données utilisateur, recevoir uniquement les nouvelles données lorsque UserDataFeed. startSync est appelé, ou lors de l’interaction avec le serveur d’une autre manière
