---
title: MCDUserNotificationChannel
description: Cette classe gère le cycle de vie des notifications à l’utilisateur.
keywords: Microsoft, windows, relais de l’appareil, iOS procédures, procédures iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907181"
---
# <a name="class-mcdusernotificationchannel"></a>Classe `MCDUserNotificationChannel`

```
@interface MCDUserNotificationChannel : NSObject
```

Cette classe fournit le lecteur de modification de notification qui gère la réception et la gestion des notifications à l’utilisateur pour l’application. 

## <a name="properties"></a>Properties

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

SyncScope utilisée pour garantir la Qu'usernotifications sont incluses dans le flux.

## <a name="constructors"></a>Constructeurs

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a>Paramètres

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed utilisée pour initialiser cette classe.

### <a name="initwithuserdatafeed"></a>initWithUserDataFeed
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed utilisée pour initialiser cette classe.

## <a name="methods"></a>Méthodes

### <a name="createreader"></a>createReader
`- (MCDUserNotificationReader* _Nullable)createReader`

Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application.

### <a name="createreaderwithoptions"></a>createReaderWithOptions
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

Créer un lecteur de notification utilisateur avec les options.

### <a name="createreaderwithstate"></a>createReaderWithState
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

Créer un lecteur de notification utilisateur pour recevoir et gérer les notifications utilisateur publiées par le serveur d’application. Le lecteur démarre à l’état de suivi.  

### <a name="getusernotificationasync"></a>getUserNotificationAsync
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

Recevez une notification de l’utilisateur en fonction de son id.

### <a name="deleteusernotificationasync"></a>deleteUserNotificationAsync
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

Supprimer une notification à l’utilisateur en fonction de son id. 