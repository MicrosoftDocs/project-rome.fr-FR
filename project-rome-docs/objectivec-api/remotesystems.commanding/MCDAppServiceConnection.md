---
title: MCDAppServiceConnection
description: Cette classe gère une connexion à un service de l’application distante particulière.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 22e253f137642ad609a22af33aa62e2ef9543503
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908541"
---
# <a name="class-mcdappserviceconnection"></a>Classe `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
Cette classe gère une connexion à un service de l’application distante particulière.

## <a name="properties"></a>Properties

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

Fournit des détails sur le service d’application cible pour se connecter à.

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

Événement lorsqu’une demande de service est reçue à partir d’une application à distance.

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

Événement lorsque la connexion au service d’application se ferme.

## <a name="constructors"></a>Constructeurs

### <a name="init"></a>init
`- (nullable instancetype)init;`

Crée et initialise une nouvelle instance de cette classe.

#### <a name="returns"></a>Returns
L’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (instancetype nullable) initWithAppServiceInfo :(nonnull MCDAppServiceInfo*) appServiceInfo ;

#### <a name="parameters"></a>Paramètres
* `appServiceInfo` Description de service de l’application.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

Crée et initialise une nouvelle instance de cette classe avec les informations de service d’application.

#### <a name="parameters"></a>Paramètres
* `appServiceInfo` 

Description de service de l’application.

#### <a name="returns"></a>Returns
Retourne l’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.

## <a name="methods"></a>Méthodes

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

Ouvre la connexion de service d’application sur le périphérique distant spécifié ou l’application. Si la connexion ne parvient pas à ouvrir, une exception est levée.

>**Remarque :** Cette méthode sera levé une exception si une des opérations suivantes est vraie :
> * La connexion est déjà ouverte ou est en cours d’ouverture.
> * Description de service de l’application n’a pas été définie ou a été effacée.
> * La plateforme n’a pas été initialisée.
> * L’application s’est abonnée à une méthode à l’événement de « demande reçue » de la connexion, mais n’a pas fourni un **MCDNotificationProvider** lors de l’initialisation de la plateforme. Tous les scénarios d’hébergement nécessitent un **MCDNotificationProvider**.

#### <a name="parameters"></a>Paramètres
* `connectionRequest` 

La demande de connexion indiquant quelle application à distance à la cible ou le système distant.

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

Envoie un message au service application distante et attend une réponse.  Cette méthode effectue une message unique/réponse et ne pas établit une connexion persistante.  Elle doit uniquement être appelée une fois que la connexion a été ouverte avec succès.

#### <a name="parameters"></a>Paramètres
* `message` 

Le jeu de clé-valeur de données à envoyer au service d’application.

### <a name="close"></a>close
`- (void)close;`

Ferme la connexion au service application distante. L’application cliente doit appeler cette méthode chaque fois qu’elle est fermée ou arrêtée par l’utilisateur ou le système.

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

Envoie un message à un service d’application distant spécifié et attend une réponse.

#### <a name="parameters"></a>Paramètres
* `message` Le jeu de clé-valeur de données à envoyer au service d’application.
* `appServiceInfo` Les informations descriptives pour le service d’application cible.
* `connectionRequest` La demande de connexion en spécifiant le service d’application pour se connecter à.
* `completion` Le rappel d’achèvement asynchrone.