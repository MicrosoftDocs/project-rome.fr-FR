---
title: MCDConnectedDevicesAccountType
description: Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801511"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a><span data-ttu-id="71f49-104">Enum `MCDConnectedDevicesAccountType`</span><span class="sxs-lookup"><span data-stu-id="71f49-104">enum `MCDConnectedDevicesAccountType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

<span data-ttu-id="71f49-105">Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="71f49-105">Contains values that describe the type of Microsoft-provided user account.</span></span>

## <a name="fields"></a><span data-ttu-id="71f49-106">Champs</span><span class="sxs-lookup"><span data-stu-id="71f49-106">Fields</span></span>

| <span data-ttu-id="71f49-107">Nom</span><span class="sxs-lookup"><span data-stu-id="71f49-107">Name</span></span>                              | <span data-ttu-id="71f49-108">Value</span><span class="sxs-lookup"><span data-stu-id="71f49-108">Value</span></span> | <span data-ttu-id="71f49-109">Description</span><span class="sxs-lookup"><span data-stu-id="71f49-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="71f49-110">MCDConnectedDevicesAccountTypeAAD</span><span class="sxs-lookup"><span data-stu-id="71f49-110">MCDConnectedDevicesAccountTypeAAD</span></span>       | <span data-ttu-id="71f49-111">0</span><span class="sxs-lookup"><span data-stu-id="71f49-111">0</span></span>     | <span data-ttu-id="71f49-112">Workplace Active Directory Azure compte</span><span class="sxs-lookup"><span data-stu-id="71f49-112">Azure Active Directory workplace Account</span></span>  |
| <span data-ttu-id="71f49-113">MCDConnectedDevicesAccountTypeMSA</span><span class="sxs-lookup"><span data-stu-id="71f49-113">MCDConnectedDevicesAccountTypeMSA</span></span>       | <span data-ttu-id="71f49-114">1</span><span class="sxs-lookup"><span data-stu-id="71f49-114">1</span></span>     | <span data-ttu-id="71f49-115">Compte du personnel de Microsoft</span><span class="sxs-lookup"><span data-stu-id="71f49-115">Microsoft Personal Account</span></span> |
| <span data-ttu-id="71f49-116">MCDConnectedDevicesAccountTypeAnonymous</span><span class="sxs-lookup"><span data-stu-id="71f49-116">MCDConnectedDevicesAccountTypeAnonymous</span></span> | <span data-ttu-id="71f49-117">2</span><span class="sxs-lookup"><span data-stu-id="71f49-117">2</span></span>     | <span data-ttu-id="71f49-118">Compte anonyme de (local, non authentifié)</span><span class="sxs-lookup"><span data-stu-id="71f49-118">Anonymous (local, non-authenticated) Account</span></span> |