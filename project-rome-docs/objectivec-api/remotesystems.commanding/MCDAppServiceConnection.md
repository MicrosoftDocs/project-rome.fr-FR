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
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="3a126-104">Classe `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="3a126-104">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="3a126-105">Cette classe gère une connexion à un service de l’application distante particulière.</span><span class="sxs-lookup"><span data-stu-id="3a126-105">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="3a126-106">Properties</span><span class="sxs-lookup"><span data-stu-id="3a126-106">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="3a126-107">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="3a126-107">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="3a126-108">Fournit des détails sur le service d’application cible pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="3a126-108">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="3a126-109">requestReceived</span><span class="sxs-lookup"><span data-stu-id="3a126-109">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="3a126-110">Événement lorsqu’une demande de service est reçue à partir d’une application à distance.</span><span class="sxs-lookup"><span data-stu-id="3a126-110">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="3a126-111">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="3a126-111">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="3a126-112">Événement lorsque la connexion au service d’application se ferme.</span><span class="sxs-lookup"><span data-stu-id="3a126-112">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="3a126-113">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="3a126-113">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="3a126-114">init</span><span class="sxs-lookup"><span data-stu-id="3a126-114">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="3a126-115">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3a126-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="3a126-116">Returns</span><span class="sxs-lookup"><span data-stu-id="3a126-116">Returns</span></span>
<span data-ttu-id="3a126-117">L’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="3a126-117">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="3a126-118">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="3a126-118">initWithAppServiceInfo</span></span>
- <span data-ttu-id="3a126-119">(instancetype nullable) initWithAppServiceInfo :(nonnull MCDAppServiceInfo\*) appServiceInfo ;</span><span class="sxs-lookup"><span data-stu-id="3a126-119">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="3a126-120">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a126-120">Parameters</span></span>
* <span data-ttu-id="3a126-121">`appServiceInfo` Description de service de l’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-121">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="3a126-122">Returns</span><span class="sxs-lookup"><span data-stu-id="3a126-122">Returns</span></span>
<span data-ttu-id="3a126-123">Retourne l’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="3a126-123">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="3a126-124">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="3a126-124">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="3a126-125">Crée et initialise une nouvelle instance de cette classe avec les informations de service d’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-125">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3a126-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a126-126">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="3a126-127">Description de service de l’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-127">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="3a126-128">Returns</span><span class="sxs-lookup"><span data-stu-id="3a126-128">Returns</span></span>
<span data-ttu-id="3a126-129">Retourne l’initialisé [MCDAppServiceConnection](MCDAppServiceConnection.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="3a126-129">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="3a126-130">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3a126-130">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="3a126-131">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="3a126-131">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="3a126-132">Ouvre la connexion de service d’application sur le périphérique distant spécifié ou l’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-132">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="3a126-133">Si la connexion ne parvient pas à ouvrir, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="3a126-133">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="3a126-134">**Remarque :** Cette méthode sera levé une exception si une des opérations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="3a126-134">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="3a126-135">La connexion est déjà ouverte ou est en cours d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="3a126-135">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="3a126-136">Description de service de l’application n’a pas été définie ou a été effacée.</span><span class="sxs-lookup"><span data-stu-id="3a126-136">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="3a126-137">La plateforme n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="3a126-137">The platform has not been initialized.</span></span>
> * <span data-ttu-id="3a126-138">L’application s’est abonnée à une méthode à l’événement de « demande reçue » de la connexion, mais n’a pas fourni un **MCDNotificationProvider** lors de l’initialisation de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="3a126-138">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="3a126-139">Tous les scénarios d’hébergement nécessitent un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="3a126-139">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3a126-140">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a126-140">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="3a126-141">La demande de connexion indiquant quelle application à distance à la cible ou le système distant.</span><span class="sxs-lookup"><span data-stu-id="3a126-141">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="3a126-142">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="3a126-142">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="3a126-143">Envoie un message au service application distante et attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="3a126-143">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="3a126-144">Cette méthode effectue une message unique/réponse et ne pas établit une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="3a126-144">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="3a126-145">Elle doit uniquement être appelée une fois que la connexion a été ouverte avec succès.</span><span class="sxs-lookup"><span data-stu-id="3a126-145">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3a126-146">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a126-146">Parameters</span></span>
* `message` 

<span data-ttu-id="3a126-147">Le jeu de clé-valeur de données à envoyer au service d’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-147">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="3a126-148">close</span><span class="sxs-lookup"><span data-stu-id="3a126-148">close</span></span>
`- (void)close;`

<span data-ttu-id="3a126-149">Ferme la connexion au service application distante.</span><span class="sxs-lookup"><span data-stu-id="3a126-149">Closes the connection to the remote app service.</span></span> <span data-ttu-id="3a126-150">L’application cliente doit appeler cette méthode chaque fois qu’elle est fermée ou arrêtée par l’utilisateur ou le système.</span><span class="sxs-lookup"><span data-stu-id="3a126-150">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="3a126-151">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="3a126-151">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="3a126-152">Envoie un message à un service d’application distant spécifié et attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="3a126-152">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3a126-153">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a126-153">Parameters</span></span>
* <span data-ttu-id="3a126-154">`message` Le jeu de clé-valeur de données à envoyer au service d’application.</span><span class="sxs-lookup"><span data-stu-id="3a126-154">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="3a126-155">`appServiceInfo` Les informations descriptives pour le service d’application cible.</span><span class="sxs-lookup"><span data-stu-id="3a126-155">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="3a126-156">`connectionRequest` La demande de connexion en spécifiant le service d’application pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="3a126-156">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="3a126-157">`completion` Le rappel d’achèvement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3a126-157">`completion` The async completion callback.</span></span>