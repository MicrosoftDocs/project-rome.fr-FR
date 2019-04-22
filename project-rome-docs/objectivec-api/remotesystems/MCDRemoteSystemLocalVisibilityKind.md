---
title: MCDRemoteSystemLocalVisibilityKind
description: Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801101"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a><span data-ttu-id="50704-104">Enum `MCDRemoteSystemLocalVisibilityKind`</span><span class="sxs-lookup"><span data-stu-id="50704-104">enum `MCDRemoteSystemLocalVisibilityKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
<span data-ttu-id="50704-105">Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="50704-105">Contains values that describe the local application visibility preference when discovering remote systems.</span></span>

## <a name="fields"></a><span data-ttu-id="50704-106">Champs</span><span class="sxs-lookup"><span data-stu-id="50704-106">Fields</span></span>

| <span data-ttu-id="50704-107">Nom</span><span class="sxs-lookup"><span data-stu-id="50704-107">Name</span></span>                              | <span data-ttu-id="50704-108">Value</span><span class="sxs-lookup"><span data-stu-id="50704-108">Value</span></span> | <span data-ttu-id="50704-109">Description</span><span class="sxs-lookup"><span data-stu-id="50704-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="50704-110">MCDRemoteSystemLocalVisibilityKindShowAll</span><span class="sxs-lookup"><span data-stu-id="50704-110">MCDRemoteSystemLocalVisibilityKindShowAll</span></span> | <span data-ttu-id="50704-111">0</span><span class="sxs-lookup"><span data-stu-id="50704-111">0</span></span> | <span data-ttu-id="50704-112">Afficher toutes les applications détectables, y compris l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="50704-112">Show all discoverable applications, including the calling app.</span></span>
| <span data-ttu-id="50704-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span><span class="sxs-lookup"><span data-stu-id="50704-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span></span> | <span data-ttu-id="50704-114">1</span><span class="sxs-lookup"><span data-stu-id="50704-114">1</span></span> | <span data-ttu-id="50704-115">Masquer l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="50704-115">Hide the calling application.</span></span>