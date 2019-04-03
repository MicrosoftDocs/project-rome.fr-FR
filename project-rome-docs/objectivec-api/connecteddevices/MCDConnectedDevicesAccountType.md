---
title: MCDConnectedDevicesAccountType
description: Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908901"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a><span data-ttu-id="ee503-104">Enum `MCDConnectedDevicesAccountType`</span><span class="sxs-lookup"><span data-stu-id="ee503-104">enum `MCDConnectedDevicesAccountType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

<span data-ttu-id="ee503-105">Contient des valeurs qui décrivent le type de compte d’utilisateur fournis par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ee503-105">Contains values that describe the type of Microsoft-provided user account.</span></span>

## <a name="fields"></a><span data-ttu-id="ee503-106">Champs</span><span class="sxs-lookup"><span data-stu-id="ee503-106">Fields</span></span>

| <span data-ttu-id="ee503-107">Nom</span><span class="sxs-lookup"><span data-stu-id="ee503-107">Name</span></span>                              | <span data-ttu-id="ee503-108">Value</span><span class="sxs-lookup"><span data-stu-id="ee503-108">Value</span></span> | <span data-ttu-id="ee503-109">Description</span><span class="sxs-lookup"><span data-stu-id="ee503-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="ee503-110">MCDConnectedDevicesAccountTypeAAD</span><span class="sxs-lookup"><span data-stu-id="ee503-110">MCDConnectedDevicesAccountTypeAAD</span></span>       | <span data-ttu-id="ee503-111">0</span><span class="sxs-lookup"><span data-stu-id="ee503-111">0</span></span>     | <span data-ttu-id="ee503-112">Workplace Active Directory Azure compte</span><span class="sxs-lookup"><span data-stu-id="ee503-112">Azure Active Directory workplace Account</span></span>  |
| <span data-ttu-id="ee503-113">MCDConnectedDevicesAccountTypeMSA</span><span class="sxs-lookup"><span data-stu-id="ee503-113">MCDConnectedDevicesAccountTypeMSA</span></span>       | <span data-ttu-id="ee503-114">1</span><span class="sxs-lookup"><span data-stu-id="ee503-114">1</span></span>     | <span data-ttu-id="ee503-115">Compte du personnel de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ee503-115">Microsoft Personal Account</span></span> |
| <span data-ttu-id="ee503-116">MCDConnectedDevicesAccountTypeAnonymous</span><span class="sxs-lookup"><span data-stu-id="ee503-116">MCDConnectedDevicesAccountTypeAnonymous</span></span> | <span data-ttu-id="ee503-117">2</span><span class="sxs-lookup"><span data-stu-id="ee503-117">2</span></span>     | <span data-ttu-id="ee503-118">Compte anonyme de (local, non authentifié)</span><span class="sxs-lookup"><span data-stu-id="ee503-118">Anonymous (local, non-authenticated) Account</span></span> |