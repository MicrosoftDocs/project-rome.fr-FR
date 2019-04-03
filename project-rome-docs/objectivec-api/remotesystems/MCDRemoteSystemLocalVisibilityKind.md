---
title: MCDRemoteSystemLocalVisibilityKind
description: Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908861"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a><span data-ttu-id="6c0dd-104">Enum `MCDRemoteSystemLocalVisibilityKind`</span><span class="sxs-lookup"><span data-stu-id="6c0dd-104">enum `MCDRemoteSystemLocalVisibilityKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
<span data-ttu-id="6c0dd-105">Contient des valeurs qui décrivent la préférence de visibilité application locale lors de la découverte des systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="6c0dd-105">Contains values that describe the local application visibility preference when discovering remote systems.</span></span>

## <a name="fields"></a><span data-ttu-id="6c0dd-106">Champs</span><span class="sxs-lookup"><span data-stu-id="6c0dd-106">Fields</span></span>

| <span data-ttu-id="6c0dd-107">Nom</span><span class="sxs-lookup"><span data-stu-id="6c0dd-107">Name</span></span>                              | <span data-ttu-id="6c0dd-108">Value</span><span class="sxs-lookup"><span data-stu-id="6c0dd-108">Value</span></span> | <span data-ttu-id="6c0dd-109">Description</span><span class="sxs-lookup"><span data-stu-id="6c0dd-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="6c0dd-110">MCDRemoteSystemLocalVisibilityKindShowAll</span><span class="sxs-lookup"><span data-stu-id="6c0dd-110">MCDRemoteSystemLocalVisibilityKindShowAll</span></span> | <span data-ttu-id="6c0dd-111">0</span><span class="sxs-lookup"><span data-stu-id="6c0dd-111">0</span></span> | <span data-ttu-id="6c0dd-112">Afficher toutes les applications détectables, y compris l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="6c0dd-112">Show all discoverable applications, including the calling app.</span></span>
| <span data-ttu-id="6c0dd-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span><span class="sxs-lookup"><span data-stu-id="6c0dd-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span></span> | <span data-ttu-id="6c0dd-114">1</span><span class="sxs-lookup"><span data-stu-id="6c0dd-114">1</span></span> | <span data-ttu-id="6c0dd-115">Masquer l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="6c0dd-115">Hide the calling application.</span></span>