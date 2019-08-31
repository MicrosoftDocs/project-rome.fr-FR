---
title: MCDUserNotification
description: Cette classe représente une notification utilisateur publiée par le serveur d’applications par le biais de notifications de graphique et reçue par le client d’application.
keywords: notifications Microsoft, iOS, Graph, procédures iOS, iPhone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907891"
---
# <a name="class-mcdusernotification"></a>type`MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


Cette classe représente une instance de notification d’utilisateur unique. Une notification utilisateur est créée et publiée par votre serveur d’applications ciblé sur un utilisateur et distribuée à tous les points de terminaison d’appareil du même utilisateur connecté.
Une notification utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et l’utilisation d’une bannière de notification visuelle à l’aide des API de notification locales de la plateforme correspondante.

## <a name="properties"></a>Properties

### <a name="notificationid"></a>ID
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`Obtient l’ID unique spécifié par le développeur pour cette notification utilisateur.

### <a name="groupid"></a>groupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;`Obtient l’ID de groupe spécifié par le développeur pour cette notification utilisateur.

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`Obtient l’heure d’expiration de cette notification utilisateur.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;`Obtient l’état de la notification de l’utilisateur.

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`Obtient l’heure à laquelle la modification a été apportée.

### <a name="priority"></a>priority
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`Obtient la priorité spécifiée par le développeur pour cette notification utilisateur.

### <a name="content"></a>content
`@property(nonatomic, readonly, nonnull) NSString* content;`Obtient la charge utile de contenu pour cette notification, qui est une donnée arbitraire définie par le développeur.

###  <a name="readstate"></a>readState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique que la notification est lue ou non.

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`Obtient la valeur de l’état de l’action utilisateur pour une notification utilisateur afin de déterminer si la notification n’est pas interactive, fermée, activée ou répétée. 

## <a name="methods"></a>Méthodes

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

Cela doit être appelé lors de la publication des modifications de notification utilisateur. Cette méthode doit être appelée chaque fois que l’application modifie une propriété pouvant être mise à jour de UserNotification.

#### <a name="parameters"></a>Paramètres
* `completion`Bloc de code à exécuter à la fin de l’opération.
