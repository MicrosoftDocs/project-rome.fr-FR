---
title: MCDRemoteSystemAccountFilter
description: Découvrez comment filtrer les comptes pour découvrir des systèmes distants à l’aide de constructeurs comme « filterwithAccount ».
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760723"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="cde8e-104">type `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="cde8e-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="cde8e-105">Filtrez les comptes pour découvrir les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="cde8e-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="cde8e-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="cde8e-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="cde8e-107">account</span><span class="sxs-lookup"><span data-stu-id="cde8e-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="cde8e-108">Compte associé à ce MCDRemoteSystemAccountFilter.</span><span class="sxs-lookup"><span data-stu-id="cde8e-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="cde8e-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="cde8e-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="cde8e-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="cde8e-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="cde8e-111">Initialisez la classe avec le compte MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="cde8e-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="cde8e-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cde8e-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="cde8e-113">Compte MCDConnectedDevicesAccount utilisé.</span><span class="sxs-lookup"><span data-stu-id="cde8e-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="cde8e-114">Retours</span><span class="sxs-lookup"><span data-stu-id="cde8e-114">Returns</span></span>
<span data-ttu-id="cde8e-115">Retourne un objet MCDRemoteSystemAccountFilter filtré avec le compte.</span><span class="sxs-lookup"><span data-stu-id="cde8e-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="cde8e-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="cde8e-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="cde8e-117">Initialisez la classe avec le compte MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="cde8e-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="cde8e-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cde8e-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="cde8e-119">Compte MCDConnectedDevicesAccount utilisé.</span><span class="sxs-lookup"><span data-stu-id="cde8e-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="cde8e-120">Retours</span><span class="sxs-lookup"><span data-stu-id="cde8e-120">Returns</span></span>
<span data-ttu-id="cde8e-121">Retourne un objet MCDRemoteSystemAccountFilter initialisé par le compte.</span><span class="sxs-lookup"><span data-stu-id="cde8e-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>