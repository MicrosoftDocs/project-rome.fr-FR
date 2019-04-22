---
title: MCDUserDataFeedSyncScope
description: Cette classe représente les données utilisateur qui sont synchronisées avec le backend de la plateforme de périphériques connectés lorsque l’application utilise certaines fonctionnalités de périphériques spécifiques à l’utilisateur.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801001"
---
# <a name="class-mcduserdatafeedsyncscope"></a>Classe `MCDUserDataFeedSyncScope`

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 Cette interface représente les données utilisateur qui sont synchronisées avec le backend de la plateforme de périphériques connectés lorsque l’application utilise certaines fonctionnalités des appareils connectés spécifiques à l’utilisateur, tels que les activités de l’utilisateur. Une instance est récupérée statiquement à partir de la classe qui gère ce type de fonctionnalité (par exemple, **MCDUserActivityChannel**), et il est utilisé dans la construction de **MCDUserDataFeed**.

## <a name="properties"></a>Properties

### <a name="platform"></a>Plateforme
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

Le **ConnectedDevicesPlatform** instance qui a été initialisé pour les fonctionnalités des appareils connectés de cette application.

### <a name="syncscopeflags"></a>syncScopeFlags
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

Définir des indicateurs facultatifs pour le filtrage des activités entrantes.

### <a name="notificationtype"></a>notificationType
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

Définir le type de modifier le type de notification pour recevoir de l’étendue de la synchronisation de flux de données d’utilisateur

```