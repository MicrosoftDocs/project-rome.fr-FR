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
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="8a44f-105">type `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="8a44f-105">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="8a44f-106">Cette classe gère une connexion à un service d’application distant particulier.</span><span class="sxs-lookup"><span data-stu-id="8a44f-106">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="8a44f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8a44f-107">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="8a44f-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="8a44f-108">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="8a44f-109">Fournit des détails sur le service APP service cible auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="8a44f-109">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="8a44f-110">requestReceived</span><span class="sxs-lookup"><span data-stu-id="8a44f-110">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="8a44f-111">Événement lors de la réception d’une demande de service à partir d’une application distante.</span><span class="sxs-lookup"><span data-stu-id="8a44f-111">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="8a44f-112">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="8a44f-112">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="8a44f-113">Événement de la fermeture de la connexion à App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-113">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="8a44f-114">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="8a44f-114">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="8a44f-115">init</span><span class="sxs-lookup"><span data-stu-id="8a44f-115">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="8a44f-116">Crée et Initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="8a44f-116">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="8a44f-117">Retours</span><span class="sxs-lookup"><span data-stu-id="8a44f-117">Returns</span></span>
<span data-ttu-id="8a44f-118">[MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.</span><span class="sxs-lookup"><span data-stu-id="8a44f-118">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="8a44f-119">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="8a44f-119">initWithAppServiceInfo</span></span>
- <span data-ttu-id="8a44f-120">(Nullable instanceType) initWithAppServiceInfo : (MCDAppServiceInfo non null \*) appServiceInfo ;</span><span class="sxs-lookup"><span data-stu-id="8a44f-120">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a44f-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a44f-121">Parameters</span></span>
* <span data-ttu-id="8a44f-122">`appServiceInfo` Description d’App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-122">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="8a44f-123">Retours</span><span class="sxs-lookup"><span data-stu-id="8a44f-123">Returns</span></span>
<span data-ttu-id="8a44f-124">Retourne le [MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.</span><span class="sxs-lookup"><span data-stu-id="8a44f-124">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="8a44f-125">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="8a44f-125">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="8a44f-126">Crée et Initialise une nouvelle instance de cette classe avec les informations du service d’application.</span><span class="sxs-lookup"><span data-stu-id="8a44f-126">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a44f-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a44f-127">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="8a44f-128">Description d’App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-128">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="8a44f-129">Retours</span><span class="sxs-lookup"><span data-stu-id="8a44f-129">Returns</span></span>
<span data-ttu-id="8a44f-130">Retourne le [MCDAppServiceConnection](MCDAppServiceConnection.md) initialisé en cas de réussite, sinon Nil.</span><span class="sxs-lookup"><span data-stu-id="8a44f-130">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="8a44f-131">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8a44f-131">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="8a44f-132">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="8a44f-132">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="8a44f-133">Ouvre la connexion App service sur l’application ou le périphérique distant spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a44f-133">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="8a44f-134">Si la connexion ne parvient pas à s’ouvrir, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="8a44f-134">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="8a44f-135">**Remarque :** Cette méthode lève une exception si l’une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="8a44f-135">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="8a44f-136">La connexion est déjà ouverte ou est en cours d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="8a44f-136">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="8a44f-137">La description app service n’a pas été définie ou a été effacée.</span><span class="sxs-lookup"><span data-stu-id="8a44f-137">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="8a44f-138">La plateforme n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="8a44f-138">The platform has not been initialized.</span></span>
> * <span data-ttu-id="8a44f-139">L’application a souscrit une méthode à l’événement « Request received » de la connexion, mais n’a pas fourni de **MCDNotificationProvider** lors de l’initialisation de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="8a44f-139">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="8a44f-140">Tous les scénarios d’hébergement requièrent un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="8a44f-140">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a44f-141">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a44f-141">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="8a44f-142">Demande de connexion indiquant le système distant ou l’application distante à cibler.</span><span class="sxs-lookup"><span data-stu-id="8a44f-142">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="8a44f-143">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="8a44f-143">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="8a44f-144">Envoie un message à Remote App service et commence à écouter une réponse.</span><span class="sxs-lookup"><span data-stu-id="8a44f-144">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="8a44f-145">Cette méthode exécute un message/une réponse unique et n’établit pas de connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="8a44f-145">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="8a44f-146">Elle doit uniquement être appelée une fois que la connexion a été ouverte avec succès.</span><span class="sxs-lookup"><span data-stu-id="8a44f-146">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a44f-147">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a44f-147">Parameters</span></span>
* `message` 

<span data-ttu-id="8a44f-148">Jeu de données clé-valeur à envoyer à App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-148">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="8a44f-149">fermer</span><span class="sxs-lookup"><span data-stu-id="8a44f-149">close</span></span>
`- (void)close;`

<span data-ttu-id="8a44f-150">Ferme la connexion à Remote App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-150">Closes the connection to the remote app service.</span></span> <span data-ttu-id="8a44f-151">L’application cliente doit appeler cette méthode chaque fois qu’elle est fermée ou arrêtée par l’utilisateur ou le système.</span><span class="sxs-lookup"><span data-stu-id="8a44f-151">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="8a44f-152">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="8a44f-152">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="8a44f-153">Envoie un message à un service d’application distant spécifié et commence à écouter une réponse.</span><span class="sxs-lookup"><span data-stu-id="8a44f-153">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a44f-154">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a44f-154">Parameters</span></span>
* <span data-ttu-id="8a44f-155">`message` Jeu de données clé-valeur à envoyer à App service.</span><span class="sxs-lookup"><span data-stu-id="8a44f-155">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="8a44f-156">`appServiceInfo` Informations descriptives de l’app service cible.</span><span class="sxs-lookup"><span data-stu-id="8a44f-156">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="8a44f-157">`connectionRequest` Demande de connexion spécifiant l’app service auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="8a44f-157">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="8a44f-158">`completion` Rappel d’achèvement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8a44f-158">`completion` The async completion callback.</span></span>