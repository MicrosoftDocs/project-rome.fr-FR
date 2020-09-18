---
title: MCDConnectedDevicesAccount
description: En savoir plus sur la classe MCDConnectedDevicesAccount. Cette classe représente un compte d’utilisateur unique connu par une application.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: b3004681c2bcbb0ad9d5b1dcb15fe8a711773767
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761043"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="5e5d9-105">type `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="5e5d9-105">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="5e5d9-106">Cette classe représente un compte d’utilisateur unique connu par une application.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-106">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="5e5d9-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5e5d9-107">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="5e5d9-108">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="5e5d9-108">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="5e5d9-109">Instance singleton du compte anonyme.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-109">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="5e5d9-110">accountId</span><span class="sxs-lookup"><span data-stu-id="5e5d9-110">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="5e5d9-111">Identificateur unique de ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-111">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="5e5d9-112">type</span><span class="sxs-lookup"><span data-stu-id="5e5d9-112">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="5e5d9-113">Valeur MCDConnectedDevicesAccountType décrivant le type de compte.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-113">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="5e5d9-114">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="5e5d9-114">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="5e5d9-115">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="5e5d9-115">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="5e5d9-116">Nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-116">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5e5d9-117">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e5d9-117">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="5e5d9-118">Chaîne d’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-118">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="5e5d9-119">MCDConnectedDevicesAccountType du compte (dépend du fournisseur d’ID à partir duquel le compte provient).</span><span class="sxs-lookup"><span data-stu-id="5e5d9-119">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="5e5d9-120">Retours</span><span class="sxs-lookup"><span data-stu-id="5e5d9-120">Returns</span></span>
<span data-ttu-id="5e5d9-121">Retourne un objet MCDConnectedDevicesAccount avec l’identificateur de compte.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-121">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="5e5d9-122">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="5e5d9-122">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="5e5d9-123">Nouvelle instance de cette classe avec l’identificateur unique pour ce compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-123">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5e5d9-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e5d9-124">Parameters</span></span> 
* `type`

<span data-ttu-id="5e5d9-125">MCDConnectedDevicesAccountType du compte (dépend du fournisseur d’ID à partir duquel le compte provient).</span><span class="sxs-lookup"><span data-stu-id="5e5d9-125">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="5e5d9-126">Retours</span><span class="sxs-lookup"><span data-stu-id="5e5d9-126">Returns</span></span>
<span data-ttu-id="5e5d9-127">Retourne un objet MCDConnectedDevicesAccount initialisé avec l’identificateur de compte.</span><span class="sxs-lookup"><span data-stu-id="5e5d9-127">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>