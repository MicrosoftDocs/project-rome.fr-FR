---
title: MCDConnectedDevicesAccountManager
description: Fournit un point d’entrée unique pour toutes les fonctionnalités relatives aux comptes dans le Kit de développement.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908391"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="533df-104">Classe `MCDConnectedDevicesAccountManager`</span><span class="sxs-lookup"><span data-stu-id="533df-104">class `MCDConnectedDevicesAccountManager`</span></span> 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
<span data-ttu-id="533df-105">Fournit un point d’entrée unique pour toutes les fonctionnalités relatives aux comptes dans le Kit de développement.</span><span class="sxs-lookup"><span data-stu-id="533df-105">Provides a single entrypoint for all account-related features in the SDK.</span></span>

## <a name="properties"></a><span data-ttu-id="533df-106">Properties</span><span class="sxs-lookup"><span data-stu-id="533df-106">Properties</span></span>

### <a name="accesstokenrequested"></a><span data-ttu-id="533df-107">accessTokenRequested</span><span class="sxs-lookup"><span data-stu-id="533df-107">accessTokenRequested</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

<span data-ttu-id="533df-108">Cet événement est déclenché lorsqu’il est nécessaire pour demander un jeton.</span><span class="sxs-lookup"><span data-stu-id="533df-108">This event is fired when there is a need to request a token.</span></span> <span data-ttu-id="533df-109">Cet événement doit être souscrit et prêt à répondre avant toute demande est envoyée.</span><span class="sxs-lookup"><span data-stu-id="533df-109">This event should be subscribed and ready to respond before any request is sent out.</span></span>

### <a name="accesstokeninvalidated"></a><span data-ttu-id="533df-110">accessTokenInvalidated</span><span class="sxs-lookup"><span data-stu-id="533df-110">accessTokenInvalidated</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

<span data-ttu-id="533df-111">Cet événement est déclenché quand un consommateur de jeton signale une erreur de jeton.</span><span class="sxs-lookup"><span data-stu-id="533df-111">This event is fired when a token consumer reports a token error.</span></span> <span data-ttu-id="533df-112">Le fournisseur de jetons doit actualiser son cache de jeton ou demander une nouvelle connexion utilisateur à corriger leur configuration de compte.</span><span class="sxs-lookup"><span data-stu-id="533df-112">The token provider needs to either refresh their token cache or request a new user login to fix their account setup.</span></span>

### <a name="allaccounts"></a><span data-ttu-id="533df-113">allAccounts</span><span class="sxs-lookup"><span data-stu-id="533df-113">allAccounts</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

<span data-ttu-id="533df-114">Tous les MCDConnectedDevicesAccount qui sont actuellement suivies par ce gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="533df-114">All MCDConnectedDevicesAccount which are currently tracked by this manager.</span></span>

## <a name="methods"></a><span data-ttu-id="533df-115">Méthodes</span><span class="sxs-lookup"><span data-stu-id="533df-115">Methods</span></span>

### <a name="addaccountasync"></a><span data-ttu-id="533df-116">addAccountAsync</span><span class="sxs-lookup"><span data-stu-id="533df-116">addAccountAsync</span></span>
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="533df-117">Ajoutez un gestionnaire de compte à compte, de rappel sera appelé lorsqu’elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="533df-117">Add an account to account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="533df-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="533df-118">Parameters</span></span> 
* `callback`

<span data-ttu-id="533df-119">Le résultat de rappel indique si Ajout du compte a réussi ou non.</span><span class="sxs-lookup"><span data-stu-id="533df-119">The callback result indicates if Account addition is successful or not.</span></span> 

### <a name="removeaccountasync"></a><span data-ttu-id="533df-120">removeAccountAsync</span><span class="sxs-lookup"><span data-stu-id="533df-120">removeAccountAsync</span></span>
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="533df-121">Supprimer un compte de gestionnaire de compte, le rappel sera appelé lorsqu’elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="533df-121">Remove an account from account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="533df-122">Paramètres</span><span class="sxs-lookup"><span data-stu-id="533df-122">Parameters</span></span> 
* `callback` 

 <span data-ttu-id="533df-123">Le résultat de rappel indique si la suppression du compte a réussi ou non.</span><span class="sxs-lookup"><span data-stu-id="533df-123">The callback result indicates if Account removal is successful or not.</span></span> 