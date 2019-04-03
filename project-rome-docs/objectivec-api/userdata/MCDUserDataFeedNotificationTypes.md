---
title: MCDUserDataFeedNotificationTypes
description: Cette classe est chargée de fournir les types de notification
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908911"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>Classe `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

Cette classe fournit les types de notification valide pour MCDUserDataFeedSyncScope.notificationType.


## <a name="properties"></a>Properties

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

Représente les notifications push entrantes.  Il n’y a aucun rescrictions pour envoyer des notifications autres que des restrictions de domaine/serveur.

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

Rétrograder tous les notifications push à une notification n'indiquant que le système de synchronisation pour recevoir les données, même si les données pourraient être contenues dans les notifications push.


### <a name="nonotification"></a>noNotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

Empêcher les notifications pour les nouvelles données utilisateur, de recevoir uniquement les nouvelles données lorsque UserDataFeed.startSync est appelée, ou lors de l’interaction avec le serveur par d’autres moyens
