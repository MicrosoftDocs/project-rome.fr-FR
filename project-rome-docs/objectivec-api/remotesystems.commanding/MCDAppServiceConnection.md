---
title: MCDAppServiceConnection
description: En savoir plus sur la classe MCDAppServiceConnection. Cette classe gère une connexion à un service d’application distant particulier.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 2d9153eeddb9010ac40ab37d9adb433edd11b0ca
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761053"
---
# <a name="class-mcdappserviceconnection"></a>type `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
Cette classe gère une connexion à un service d’application distant particulier.

## <a name="properties"></a>Propriétés

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

Fournit des détails sur le service APP service cible auquel se connecter.

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

Événement lors de la réception d’une demande de service à partir d’une application distante.

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

Événement de la fermeture de la connexion à App service.

## <a name="constructors"></a>Constructeurs

### <a name="init"></a>init
`- (nullable instancetype)init;`

Crée et Initialise une nouvelle instance de cette classe.

#### <a name="returns"></a>Retours
[MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (Nullable instanceType) initWithAppServiceInfo : (MCDAppServiceInfo non null *) appServiceInfo ;

#### <a name="parameters"></a>Paramètres
* `appServiceInfo` Description d’App service.

#### <a name="returns"></a>Retours
Retourne le [MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

Crée et Initialise une nouvelle instance de cette classe avec les informations du service d’application.

#### <a name="parameters"></a>Paramètres
* `appServiceInfo` 

Description d’App service.

#### <a name="returns"></a>Retours
Retourne le [MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.

## <a name="methods"></a>Méthodes

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

Ouvre la connexion App service sur l’application ou le périphérique distant spécifié. Si la connexion ne parvient pas à s’ouvrir, une exception est levée.

>**Remarque :** Cette méthode lève une exception si l’une des conditions suivantes est vraie :
> * La connexion est déjà ouverte ou est en cours d’ouverture.
> * La description app service n’a pas été définie ou a été effacée.
> * La plateforme n’a pas été initialisée.
> * L’application a souscrit une méthode à l’événement « Request received » de la connexion, mais n’a pas fourni de **MCDNotificationProvider** lors de l’initialisation de la plateforme. Tous les scénarios d’hébergement requièrent un **MCDNotificationProvider**.

#### <a name="parameters"></a>Paramètres
* `connectionRequest` 

Demande de connexion indiquant le système distant ou l’application distante à cibler.

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

Envoie un message à Remote App service et commence à écouter une réponse.  Cette méthode exécute un message/une réponse unique et n’établit pas de connexion persistante.  Elle doit uniquement être appelée une fois que la connexion a été ouverte avec succès.

#### <a name="parameters"></a>Paramètres
* `message` 

Jeu de données clé-valeur à envoyer à App service.

### <a name="close"></a>fermer
`- (void)close;`

Ferme la connexion à Remote App service. L’application cliente doit appeler cette méthode chaque fois qu’elle est fermée ou arrêtée par l’utilisateur ou le système.

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

Envoie un message à un service d’application distant spécifié et commence à écouter une réponse.

#### <a name="parameters"></a>Paramètres
* `message` Jeu de données clé-valeur à envoyer à App service.
* `appServiceInfo` Informations descriptives de l’app service cible.
* `connectionRequest` Demande de connexion spécifiant l’app service auquel se connecter.
* `completion` Rappel d’achèvement asynchrone.