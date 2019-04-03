---
title: MCDConnectedDevicesAccount
description: Cette classe représente un seul compte d’utilisateur connu par une application.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909151"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="f18eb-104">Classe `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="f18eb-104">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="f18eb-105">Cette classe représente un seul compte d’utilisateur connu par une application.</span><span class="sxs-lookup"><span data-stu-id="f18eb-105">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="f18eb-106">Properties</span><span class="sxs-lookup"><span data-stu-id="f18eb-106">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="f18eb-107">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="f18eb-107">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="f18eb-108">L’instance singleton du compte anonyme.</span><span class="sxs-lookup"><span data-stu-id="f18eb-108">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="f18eb-109">accountId</span><span class="sxs-lookup"><span data-stu-id="f18eb-109">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="f18eb-110">Identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f18eb-110">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="f18eb-111">Type</span><span class="sxs-lookup"><span data-stu-id="f18eb-111">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="f18eb-112">Une valeur MCDConnectedDevicesAccountType décrivant le type de compte.</span><span class="sxs-lookup"><span data-stu-id="f18eb-112">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="f18eb-113">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="f18eb-113">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="f18eb-114">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="f18eb-114">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="f18eb-115">Une nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f18eb-115">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f18eb-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f18eb-116">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="f18eb-117">Une chaîne d’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f18eb-117">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="f18eb-118">Le MCDConnectedDevicesAccountType du compte (repose sur le fournisseur de l’ID du compte provient de).</span><span class="sxs-lookup"><span data-stu-id="f18eb-118">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="f18eb-119">Returns</span><span class="sxs-lookup"><span data-stu-id="f18eb-119">Returns</span></span>
<span data-ttu-id="f18eb-120">Retourne un objet MCDConnectedDevicesAccount avec l’identificateur de compte.</span><span class="sxs-lookup"><span data-stu-id="f18eb-120">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="f18eb-121">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="f18eb-121">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="f18eb-122">Une nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f18eb-122">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f18eb-123">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f18eb-123">Parameters</span></span> 
* `type`

<span data-ttu-id="f18eb-124">Le MCDConnectedDevicesAccountType du compte (repose sur le fournisseur de l’ID du compte provient de).</span><span class="sxs-lookup"><span data-stu-id="f18eb-124">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="f18eb-125">Returns</span><span class="sxs-lookup"><span data-stu-id="f18eb-125">Returns</span></span>
<span data-ttu-id="f18eb-126">Retourne un objet MCDConnectedDevicesAccount initialisé avec le compte.</span><span class="sxs-lookup"><span data-stu-id="f18eb-126">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>