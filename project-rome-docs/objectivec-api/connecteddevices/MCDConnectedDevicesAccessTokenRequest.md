---
title: MCDConnectedDevicesAccessTokenRequest
description: Demande de jeton d’accès de la relation contenant-contenu MCDConnectedDevicesAccount qui satisfait les étendues de relation contenant-contenus.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b1cd9b747e98d5e9ccf4885b33897e8c240d7673
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800831"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a><span data-ttu-id="2139f-104">Classe `MCDConnectedDevicesAccessTokenRequest`</span><span class="sxs-lookup"><span data-stu-id="2139f-104">class `MCDConnectedDevicesAccessTokenRequest`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
<span data-ttu-id="2139f-105">Demande de jeton d’accès de la relation contenant-contenu MCDConnectedDevicesAccount qui satisfait les étendues de relation contenant-contenus.</span><span class="sxs-lookup"><span data-stu-id="2139f-105">Request for an access token for the contained MCDConnectedDevicesAccount which satisfies the contained scopes.</span></span>

## <a name="properties"></a><span data-ttu-id="2139f-106">Properties</span><span class="sxs-lookup"><span data-stu-id="2139f-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="2139f-107">compte</span><span class="sxs-lookup"><span data-stu-id="2139f-107">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="2139f-108">Le compte associé à cette MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="2139f-108">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="2139f-109">Étendues</span><span class="sxs-lookup"><span data-stu-id="2139f-109">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="2139f-110">La liste des étendues pour laquelle le jeton doit couvrir lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="2139f-110">The list of scopes for which the token must cover when generated.</span></span>

## <a name="methods"></a><span data-ttu-id="2139f-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2139f-111">Methods</span></span>

### <a name="completewithaccesstoken"></a><span data-ttu-id="2139f-112">completeWithAccessToken</span><span class="sxs-lookup"><span data-stu-id="2139f-112">completeWithAccessToken</span></span>
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

<span data-ttu-id="2139f-113">Si un jeton avec les étendues demandés a été généré avec succès, appelez cette méthode avec le jeton pour terminer la demande.</span><span class="sxs-lookup"><span data-stu-id="2139f-113">If a token with the requested scopes was successfully generated, call this method with the token to complete the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2139f-114">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2139f-114">Parameters</span></span> 
* `token` 

<span data-ttu-id="2139f-115">Jeton généré avec succès</span><span class="sxs-lookup"><span data-stu-id="2139f-115">Successfully generated token</span></span>

### <a name="completewitherrormessage"></a><span data-ttu-id="2139f-116">completeWithErrorMessage</span><span class="sxs-lookup"><span data-stu-id="2139f-116">completeWithErrorMessage</span></span>
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

<span data-ttu-id="2139f-117">Si un jeton avec les étendues demandées n’a pas été correctement généré pour une raison quelconque, appelez cette méthode avec un message à utiliser pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="2139f-117">If a token with the requested scopes was not successfully generated for any reason, call this method with a message to be used for logging.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2139f-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2139f-118">Parameters</span></span> 
* `errorMessage`

<span data-ttu-id="2139f-119">Message décrivant la raison pour laquelle le jeton a échoué.</span><span class="sxs-lookup"><span data-stu-id="2139f-119">A message describing why the token was unsuccessful.</span></span>