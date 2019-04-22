---
title: MCDUserDataFeed
description: Cette classe est chargée pour la synchronisation des données spécifiques à l’utilisateur avec le backend de la plateforme de périphériques connectés.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 66898563bdad8adb2f1ebfe75f010cd5ef1d9ca2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58908991"
---
# <a name="class-mcduserdatafeed"></a>Classe `MCDUserDataFeed`

```
@interface MCDUserDataFeed : NSObject
```

Cette classe est chargée pour la synchronisation des données spécifiques à l’utilisateur avec le backend de la plateforme de périphériques connectés. Les données sont synchronisées varie en fonction **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances sont contenues.

## <a name="properties"></a>Properties

### <a name="syncstatus"></a>syncStatus
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

Décrit l’état actuel de la synchronisation des données utilisateur.

### <a name="syncstatuschanged"></a>syncStatusChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

Événement de modification du statut de la synchronisation de la UserDataFeed.

### <a name="daystosync"></a>daysToSync
`@property(nonatomic, readwrite) NSInteger daysToSync;`

Le nombre de jours de données à synchroniser, qui doivent être de moins de 30.  Il représente la valeur par défaut, qui est déterminée par le serveur.

## <a name="constructors"></a>Constructeurs

### <a name="getforaccount"></a>getForAccount
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

Crée et initialise une nouvelle instance de cette classe avec un compte d’utilisateur, instance de la plateforme et l’ID d’application multiplateforme.

#### <a name="parameters"></a>Paramètres
* `userAccount` 

Le compte d’utilisateur qui seront associées ces données.

* `platform` 

Le **MCDPlatform** instance qui a été initialisé pour les fonctionnalités des appareils connectés de cette application.

* `activitySourceHost` 

L’ID d’application multiplateforme. Cette valeur est extraite via l’inscription de tableau de bord de développement Microsoft.

#### <a name="returns"></a>Returns
Retourne une instance de cette classe.

## <a name="methods"></a>Méthodes

### <a name="subscribetosyncscopesasync"></a>subscribeToSyncScopesAsync
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback;`

Ajoute **MCDUserDataFeedSyncScope** instances à cette MCDUserDataFeed.  Cette MCDUserDataFeed est synchronisé en fonction de la **MCDUserDataFeedSyncScope** instances spécifiées.

#### <a name="parameters"></a>Paramètres

* `syncScopes` Un tableau de **MCDSyncScope** instances.

* `callback`

Le résultat de rappel indique si l’abonnement est réussie, ou non. 

### <a name="startsync"></a>startSync
`- (void)startSync;`

Démarre le processus de synchronisation avec la plateforme d’appareils connectés. Pendant cette opération, le **syncStatus** propriété sera actualisée et les événements de modification seront déclenchés.