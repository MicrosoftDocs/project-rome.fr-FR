---
title: MCDConnectedDevicesPlatform
description: Une classe pour représenter la plateforme d’appareils connectés et de gérer la connexion de l’application à celui-ci.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801781"
---
# <a name="class-mcdconnecteddevicesplatform"></a>Classe `MCDConnectedDevicesPlatform` 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
Cette classe pour représenter la plateforme d’appareils connectés et de gérer la connexion de l’application à celui-ci.

## <a name="properties"></a>Properties

### <a name="accountmanager"></a>accountManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

Instance MCDConnectedDevicesAccountManager détenue par la plateforme.

### <a name="notificationregistrationmanager"></a>notificationRegistrationManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

Instance MCDConnectedDevicesNotificationRegistrationManager détenue par la plateforme.

## <a name="constructors"></a>Constructeurs

### <a name="platformwithsettings"></a>platformWithSettings
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

Une nouvelle instance de cette classe avec les paramètres de plateforme spécifié.

#### <a name="parameters"></a>Paramètres 
* `settings` 

L’objet MCDConnectedDevicesPlatformSettings qui stocke les paramètres de l’application de la plateforme.

#### <a name="returns"></a>Returns

Retourne un objet MCDConnectedDevicesPlatform contenant des paramètres de plateforme de l’application.

### <a name="initwithsettings"></a>initWithSettings
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

Une nouvelle instance de cette classe avec les paramètres de plateforme.

#### <a name="parameters"></a>Paramètres 
* `settings` 

L’objet MCDConnectedDevicesPlatformSettings qui stocke les paramètres de l’application de la plateforme.

#### <a name="returns"></a>Returns

Retourne un objet MCDConnectedDevicesPlatform initialisé avec les paramètres de plateforme de l’application.

## <a name="methods"></a>Méthodes

### <a name="processnotification"></a>processNotification
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

Traiter la notification APNs entrante.

#### <a name="parameters"></a>Paramètres 
* `notification` 

Contient la notification APNs à traiter.

#### <a name="returns"></a>Returns

Une instance de la classe MCDConnectedDevicesProcessNotificationOperation.

### <a name="start"></a>start
`- (void) start;`

Démarrer la plateforme.

### <a name="shutdownasync"></a>shutdownAsync
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

Arrête la plateforme d’appareils connectés.

#### <a name="parameters"></a>Paramètres 
* `completionBlock` 

Le bloc à appeler à l’achèvement.