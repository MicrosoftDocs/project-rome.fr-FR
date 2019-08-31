---
title: MCDUserNotificationChannel
description: Cette classe gère le cycle de vie des notifications utilisateur.
keywords: Microsoft, Windows, appareil Relay, procédure iOS, iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801241"
---
# <a name="class-mcdusernotificationchannel"></a>type`MCDUserNotificationChannel`

```
@interface MCDUserNotificationChannel : NSObject
```

Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications de l’utilisateur pour l’application. 

## <a name="properties"></a>Properties

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

SyncScope utilisé pour garantir que les UserNotifications sont inclus dans le flux.

## <a name="constructors"></a>Constructeurs

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a>Paramètres

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed utilisé pour initialiser cette classe.

### <a name="initwithuserdatafeed"></a>initWithUserDataFeed
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed utilisé pour initialiser cette classe.

## <a name="methods"></a>Méthodes

### <a name="createreader"></a>createReader
`- (MCDUserNotificationReader* _Nullable)createReader`

Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications.

### <a name="createreaderwithoptions"></a>createReaderWithOptions
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

Créez un lecteur de notifications utilisateur avec des options.

### <a name="createreaderwithstate"></a>createReaderWithState
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

Créez un lecteur de notifications utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’applications. Le lecteur démarre à l’état de suivi fourni.  

### <a name="getusernotificationasync"></a>getUserNotificationAsync
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

Obtenir une notification utilisateur en fonction de son ID.

### <a name="deleteusernotificationasync"></a>deleteUserNotificationAsync
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

Supprimer une notification utilisateur en fonction de son ID. 