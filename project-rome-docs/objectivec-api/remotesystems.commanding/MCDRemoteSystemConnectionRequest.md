---
title: MCDRemoteSystemConnectionRequest
description: Une classe qui représente une tentative de communication avec un périphérique distant spécifique ou une application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907131"
---
# <a name="class-mcdremotesystemconnectionrequest"></a><span data-ttu-id="eb787-104">Classe `MCDRemoteSystemConnectionRequest`</span><span class="sxs-lookup"><span data-stu-id="eb787-104">class `MCDRemoteSystemConnectionRequest`</span></span> 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

<span data-ttu-id="eb787-105">Une classe qui représente une tentative de communication avec un périphérique distant spécifique ou une application.</span><span class="sxs-lookup"><span data-stu-id="eb787-105">A class that represents an attempt to communicate with a specific remote device or application.</span></span>

## <a name="constructors"></a><span data-ttu-id="eb787-106">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="eb787-106">Constructors</span></span>

### <a name="requestwithremotesystem"></a><span data-ttu-id="eb787-107">requestWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="eb787-107">requestWithRemoteSystem</span></span>
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="eb787-108">Initialise le [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) avec un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span><span class="sxs-lookup"><span data-stu-id="eb787-108">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="eb787-109">Ce constructeur n’est pas recommandé, car il ne spécifie pas une application à la cible et par conséquent, peut entraîner une application inattendue sélectionnée pour traiter les demandes envoyées au système.</span><span class="sxs-lookup"><span data-stu-id="eb787-109">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="eb787-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb787-110">Parameters</span></span>
* `remoteSystem` 

<span data-ttu-id="eb787-111">Le système distant à cibler dans cette demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="eb787-111">The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="eb787-112">Returns</span><span class="sxs-lookup"><span data-stu-id="eb787-112">Returns</span></span>
<span data-ttu-id="eb787-113">Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="eb787-113">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="requestwithremotesystemapp"></a><span data-ttu-id="eb787-114">requestWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="eb787-114">requestWithRemoteSystemApp</span></span>
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="eb787-115">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="eb787-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="eb787-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb787-116">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="eb787-117">L’application distante à cibler dans cette demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="eb787-117">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="eb787-118">Returns</span><span class="sxs-lookup"><span data-stu-id="eb787-118">Returns</span></span>
<span data-ttu-id="eb787-119">Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="eb787-119">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystem"></a><span data-ttu-id="eb787-120">initWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="eb787-120">initWithRemoteSystem</span></span>
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="eb787-121">Initialise le [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) avec un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span><span class="sxs-lookup"><span data-stu-id="eb787-121">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="eb787-122">Ce constructeur n’est pas recommandé, car il ne spécifie pas une application à la cible et par conséquent, peut entraîner une application inattendue sélectionnée pour traiter les demandes envoyées au système.</span><span class="sxs-lookup"><span data-stu-id="eb787-122">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="eb787-123">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb787-123">Parameters</span></span>
* <span data-ttu-id="eb787-124">`remoteSystem` Le système distant à cibler dans cette demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="eb787-124">`remoteSystem` The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="eb787-125">Returns</span><span class="sxs-lookup"><span data-stu-id="eb787-125">Returns</span></span>
<span data-ttu-id="eb787-126">Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="eb787-126">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystemapp"></a><span data-ttu-id="eb787-127">initWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="eb787-127">initWithRemoteSystemApp</span></span>
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="eb787-128">Crée et initialise une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="eb787-128">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="eb787-129">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb787-129">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="eb787-130">L’application distante à cibler dans cette demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="eb787-130">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="eb787-131">Returns</span><span class="sxs-lookup"><span data-stu-id="eb787-131">Returns</span></span>
<span data-ttu-id="eb787-132">Retourne l’initialisé [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) en cas de réussite, sinon nil.</span><span class="sxs-lookup"><span data-stu-id="eb787-132">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>