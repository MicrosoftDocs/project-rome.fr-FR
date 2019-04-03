---
title: MCDRemoteSystemAppRegistration
description: Cette classe représente une application qui doit être enregistré avec la plateforme d’appareils connectés.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909911"
---
# <a name="class-mcdremotesystemappregistration"></a>Classe `MCDRemoteSystemAppRegistration` 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

Cette classe contient toutes les informations sur cette application qui a un autre peut détecter et utiliser.

> [!NOTE] 
> MCDRemoteSystemAppRegistration informations doivent être publiées avant la fidèlement les communications sortantes vers une autre application. Il s’agit afin que l’autre application peut savoir comment répondre à cette communication.

## <a name="properties"></a>Properties

### <a name="account"></a>compte
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

Compte auquel appartient cette inscription.

### <a name="attributes"></a>attributs
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 Dictionnaire de chaînes qui décrivent les attributs de cette application.

### <a name="appserviceproviders"></a>appServiceProviders
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

Tableau de AppServiceProviders qui prend en charge de cette application.

> [!NOTE] 
> Un fournisseur de services d’application doit être présent dans ce tableau d’afin de recevoir des connexions entrantes.  MCDRemoteSystemAppRegistration.publishAsync() n’a pas besoin d’être appelée pour le fournisseur de services d’application recevoir les demandes.  

### <a name="launchuriprovider"></a>launchUriProvider
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

Lancer les Uri du fournisseur pour cette application.

> [!NOTE] 
> Un fournisseur d’uri de lancement doit être stocké dans cette propriété afin de recevoir les demandes entrantes.  MCDRemoteSystemAppRegistration.publishAsync() n’a pas besoin d’être appelée pour le fournisseur de services d’application recevoir les demandes.  

## <a name="constructors"></a>Constructeurs

### <a name="getforaccount"></a>getForAccount
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

Obtient l’inscription de l’application actuelle du système distant pour le compte.

#### <a name="parameters"></a>Paramètres
* `account` 

Compte afin de récupérer l’inscription.

* `platform` 

Plateforme pour obtenir de l’inscription à partir de.

#### <a name="returns"></a>Returns
Retourne un objet MCDRemoteSystemAppRegistration pour le compte fourni.

## <a name="methods"></a>Méthodes

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

Enregistre les informations actuellement stockées dans la RemoteSystemAppRegistration telles que les autres applications peuvent les découvrir.

> [!NOTE] 
> MCDConnectedDevicesNotificationRegistration doit être inscrit pour cet appel réussisse.

> [!WARNING] 
> Déconseillé. Utilisez publishAsync à la place.

#### <a name="parameters"></a>Paramètres

* `callback`

Le rappel indique le résultat de l’enregistrement des informations.

### <a name="publishasync"></a>publishAsync
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

Publie les informations actuellement stockées dans la MCDRemoteSystemAppRegistration telles que les autres applications peuvent les découvrir.

> [!NOTE] 
> MCDConnectedDevicesNotificationRegistration doit être inscrit pour cet appel réussisse.

#### <a name="parameters"></a>Paramètres

* `callback`

Le rappel indique le résultat de l’enregistrement des informations.
