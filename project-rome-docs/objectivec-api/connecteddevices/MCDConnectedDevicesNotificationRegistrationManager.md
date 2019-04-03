---
title: MCDConnectedDevicesNotificationRegistrationManager
description: Gère l’inscription pour la notification de cloud Rome pour tous les comptes.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d4f5f7963514795e3e296d9bdb42b1811af4f7cc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909901"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a>Classe `MCDConnectedDevicesNotificationRegistrationManager` 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
Gère l’inscription pour la notification de cloud de plateforme appareils connectés pour tous les comptes.

MCDConnectedDevicesNotificationRegistrationManager gère les informations de notification inscrits pour chaque compte. N’importe quel moment les informations de notification d’une application changent (par exemple, avec APNS son jeton), ou lorsque les informations de notification arrive à expiration, une application doit réinscrire ses informations. Si une application considère uniquement les réponses pour les communications sortantes, une inscription d’interrogation peut être utilisée.

> [!NOTE] 
> Informations de notification doivent être enregistrées avant de nombreux scénarios ConnectedDevices ne fonctionnent pas correctement. 

## <a name="properties"></a>Properties

### <a name="registrationstatechanged"></a>registrationStateChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

Événements pour informer l’application quand état de l’inscription de notification change pour un compte. 

## <a name="methods"></a>Méthodes

### <a name="registerforaccountasync"></a>registerForAccountAsync
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

Inscrire le compte donné avec les informations d’inscription de notification donnée. Cette opération crée un canal de notification afin que cette application peut être avertie de nouvelles informations d’appareils connectés pour ce compte. Notez que les autres applications ne peuvent pas communiquer avec cette application à l’aide de ce canal de notification jusqu'à ce que les informations de MCDRemoteSystemAppRegistration sont publiées.

> [!WARNING]
> Cette fonction est déconseillée. Utilisez plutôt registerAsync.

#### <a name="parameters"></a>Paramètres 
* `account` 

Compte pour lequel enregistrer les informations de notification.

* `notificationRegistration` 

Informations de notification pour vous inscrire.

* `callback` 

Le rappel bénéficient ainsi d’if l’inscription s’est terminée correctement.

### <a name="registerasync"></a>registerAsync
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

Inscrire le compte donné avec les informations d’inscription de notification donnée. Cette opération crée un canal de notification afin que cette application peut être avertie de nouvelles informations d’appareils connectés pour ce compte. Notez que les autres applications ne peuvent pas communiquer avec cette application à l’aide de ce canal de notification jusqu'à ce que les informations de MCDRemoteSystemAppRegistration sont publiées.

#### <a name="parameters"></a>Paramètres 
* `account` 

Compte pour lequel enregistrer les informations de notification.

* `notificationRegistration` 

Informations de notification pour vous inscrire.

* `callback` 

Le rappel bénéficient ainsi d’if l’inscription s’est terminée correctement.

### <a name="getnotificationregistrationstateforaccount"></a>getNotificationRegistrationStateForAccount
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

Récupérer l’état de l’inscription de notification en cours pour le compte donné. Les informations de notification qui sont inscrit arriveront à expiration (utile si l’application est désinstallée ou pas exécutée dans beaucoup de temps). Une application doit enregistrez à nouveau ses informations de notification lors de l’inscription de l’état arrivant à expiration ou a expiré. 

#### <a name="parameters"></a>Paramètres 
* `account`

Compte pour lequel obtenir l’état de l’inscription.

#### <a name="returns"></a>Returns

État de l’inscription de notification.
