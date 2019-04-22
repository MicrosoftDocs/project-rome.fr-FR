---
title: MCDRemoteSystemAccountFilter
description: Filtre pour les comptes découvrir des systèmes distants avec.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801551"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="7e121-104">Classe `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="7e121-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="7e121-105">Filtre pour les comptes découvrir des systèmes distants avec.</span><span class="sxs-lookup"><span data-stu-id="7e121-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="7e121-106">Properties</span><span class="sxs-lookup"><span data-stu-id="7e121-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="7e121-107">compte</span><span class="sxs-lookup"><span data-stu-id="7e121-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="7e121-108">Le compte associé à cette MCDRemoteSystemAccountFilter.</span><span class="sxs-lookup"><span data-stu-id="7e121-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="7e121-109">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="7e121-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="7e121-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="7e121-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="7e121-111">Initialiser la classe avec le compte MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="7e121-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="7e121-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e121-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="7e121-113">Le compte MCDConnectedDevicesAccount utilisé.</span><span class="sxs-lookup"><span data-stu-id="7e121-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="7e121-114">Returns</span><span class="sxs-lookup"><span data-stu-id="7e121-114">Returns</span></span>
<span data-ttu-id="7e121-115">Retourne un objet MCDRemoteSystemAccountFilter filtré à l’aide du compte.</span><span class="sxs-lookup"><span data-stu-id="7e121-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="7e121-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="7e121-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="7e121-117">Initialiser la classe avec le compte MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="7e121-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="7e121-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e121-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="7e121-119">Le compte MCDConnectedDevicesAccount utilisé.</span><span class="sxs-lookup"><span data-stu-id="7e121-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="7e121-120">Returns</span><span class="sxs-lookup"><span data-stu-id="7e121-120">Returns</span></span>
<span data-ttu-id="7e121-121">Retourne un objet MCDRemoteSystemAccountFilter initialisé filtrés à l’aide du compte.</span><span class="sxs-lookup"><span data-stu-id="7e121-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>