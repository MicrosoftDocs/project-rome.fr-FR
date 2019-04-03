---
title: MCDRemoteSystemApp
description: Représente une application sur un système distant qui est disponible pour la connectivité.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907651"
---
# <a name="class-mcdremotesystemapp"></a>Classe `MCDRemoteSystemApp` 

```
@interface MCDRemoteSystemApp : NSObject
```  

Représente une application sur un système distant qui est disponible pour la connectivité.

## <a name="properties"></a>Properties

### <a name="appid"></a>appId
`@property(nonatomic, readonly, nonnull) NSString* appId;`

Un identificateur unique pour cette application.

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

Le nom complet convivial pour cette application. Il s’agit du nom utilisé par l’appareil pour l’identification de Bluetooth. Si cela n’a pas été défini ou l’appareil ne prend pas en charge le Bluetooth, ce champ sera vide.

### <a name="availablebyproximity"></a>availableByProximity
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

Indique si cette application est actuellement disponible pour la connexion PROXIMALE.

### <a name="availablebyspatialproximity"></a>availableBySpatialProximity
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

Indique si cette application est actuellement disponible pour la connexion partage spatiale.

### <a name="attributes"></a>attributs
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

Dictionnaire de paires clé/valeur qui définit les attributs de cette application.

### <a name="appservices"></a>appServices
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

Un tableau d’instances de MCDAppServiceDescription décrivant les services d’application fournies par cette application pour la connectivité à distance.

### <a name="accounts"></a>comptes
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

Le compte associé à MCDRemoteSystemApp que vous êtes autorisé à connaître. Élément qui détermine les autorisations est si le MCDConnectedDevicesAccount existe dans le MCDConnectedDevicesAccountManager lorsque le MCDRemoteSystemWatcher est démarré.