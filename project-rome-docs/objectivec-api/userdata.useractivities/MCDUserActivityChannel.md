---
title: MCDUserActivityChannel
description: Cette classe gère l’ajout et l’interrogation des activités de l’utilisateur pour l’application.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b047af1da3ba79be88a53cf589c3894892b01ef4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907801"
---
# <a name="class-mcduseractivitychannel"></a>Classe `MCDUserActivityChannel`

```
@interface MCDUserActivityChannel : NSObject
```

Cette classe gère l’ajout et l’interrogation des activités de l’utilisateur pour l’application.

## <a name="properties"></a>Properties

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

Obtient la valeur de portée de synchronisation de données utilisateur pour les activités de l’utilisateur.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

Nom complet de l’application pour toutes les activités.

## <a name="constructors"></a>Constructeurs

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

Crée une instance de cette classe avec le flux de données utilisateur.

#### <a name="parameters"></a>Paramètres
* `userDataFeed` Les données utilisateur associées aux activités sur ce canal.

#### <a name="returns"></a>Returns
Retourne une nouvelle instance de cette classe.

## <a name="methods"></a>Méthodes

### <a name="getorcreateuseractivityasync"></a>getOrCreateUserActivityAsync
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

Crée l’activité de l’utilisateur spécifié ou obtient une référence à celui-ci s’il existe déjà.

#### <a name="parameters"></a>Paramètres
* `activityId` L’ID pour cette activité.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique. Fournit l’accès à l’activité récupérée.

### <a name="deleteactivityasync"></a>deleteActivityAsync
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Supprime l’activité utilisateur donné.

#### <a name="parameters"></a>Paramètres
* `activityId` ID de l’activité à supprimer.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.

### <a name="deleteallactivitiesasync"></a>deleteAllActivitiesAsync
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Supprime toutes les activités de l’utilisateur.

#### <a name="parameters"></a>Paramètres
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.

### <a name="getrecentuseractivitiesasync"></a>getRecentUserActivitiesAsync
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

Obtient un historique des activités récentes de l’utilisateur. 

#### <a name="parameters"></a>Paramètres
* `maxUniqueActivities` Le nombre maximal d’activités d’utilisateur à récupérer.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique. Fournit l’accès à l’historique de l’activité.

### <a name="getsessionhistoryitemsforuseractivityasync"></a>getSessionHistoryItemsForUserActivityAsync
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

Obtient des entrées d’historique de la session pour une activité donnée.

#### <a name="parameters"></a>Paramètres
* `activityId` L’ID de l’activité pour obtenir l’historique pour.
* `startTime` L’heure à laquelle à prendre en compte l’historique de session.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique. Fournit l’accès à l’historique de l’activité.

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a>getRecentSessionHistoryItemsForTimeRangeAsync
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

Obtient des entrées d’historique de la session pour une activité donnée.

#### <a name="parameters"></a>Paramètres
* `startTime` Heure à laquelle commencer à évaluer l’historique de session.
* `endTime` Heure à laquelle se termine en tenant compte de l’historique de session.
* `maxActivities` Le nombre maximal d’activités d’utilisateur à récupérer.
* `completion` Le bloc de code à exécuter en cas de saisie semi-automatique.
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique. Fournit l’accès à l’historique de l’activité.