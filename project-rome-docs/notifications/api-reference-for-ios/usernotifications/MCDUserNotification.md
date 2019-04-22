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
# <a name="class-mcdusernotification"></a>Classe `MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


Cette classe représente une instance de la notification utilisateur unique. Une notification de l’utilisateur est créée et publiée par votre serveur d’application ciblée sur un utilisateur, distribué à tous les points de terminaison de périphérique du même utilisateur connecté.
Une notification de l’utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et affichage d’une bannière de notification visuelle à l’aide des API de notification locale de la plateforme correspondante.

## <a name="properties"></a>Properties

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Obtient le développeur spécifié unique id pour cette notification à l’utilisateur.

### <a name="groupid"></a>groupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;` Obtient le développeur spécifié id de groupe pour cette notification à l’utilisateur.

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Obtient le délai d’expiration pour cette notification à l’utilisateur.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Obtient l’état de la notification de l’utilisateur.

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Obtient l’heure de que la modification a été effectuée.

### <a name="priority"></a>priority
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Obtient le développeur spécifié priorité pour cette notification à l’utilisateur.

### <a name="content"></a>content
`@property(nonatomic, readonly, nonnull) NSString* content;` Obtient la charge utile de contenu pour cette notification, qui est défini de développeur des données arbitraires.

###  <a name="readstate"></a>readState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique la notification est lu ou non lu.

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Obtient la valeur de l’état d’action utilisateur pour une notification de l’utilisateur déterminer si la notification n'est pas interagie, fermée, activée ou répétée. 

## <a name="methods"></a>Méthodes

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

Cela doit être appelée lors de la publication des modifications de notification utilisateur. Cette méthode doit être appelée chaque fois que l’application modifie une propriété d’être mise à jour de la UserNotification.

#### <a name="parameters"></a>Paramètres
* `completion` Le bloc de code à exécuter en cas de saisie semi-automatique.
