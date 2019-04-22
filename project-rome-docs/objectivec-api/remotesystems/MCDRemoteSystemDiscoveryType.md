---
title: MCDRemoteSystemDiscoveryType
description: Contient des valeurs qui décrivent les systèmes distants comment sont en mesure d’être découverts.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800501"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a><span data-ttu-id="12c24-104">Enum `MCDRemoteSystemDiscoveryType`</span><span class="sxs-lookup"><span data-stu-id="12c24-104">enum `MCDRemoteSystemDiscoveryType`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

<span data-ttu-id="12c24-105">Contient des valeurs qui décrivent les systèmes distants comment sont en mesure d’être découverts.</span><span class="sxs-lookup"><span data-stu-id="12c24-105">Contains values that describe how remote systems are able to be discovered.</span></span> 

## <a name="fields"></a><span data-ttu-id="12c24-106">Champs</span><span class="sxs-lookup"><span data-stu-id="12c24-106">Fields</span></span>

| <span data-ttu-id="12c24-107">Nom</span><span class="sxs-lookup"><span data-stu-id="12c24-107">Name</span></span>                              | <span data-ttu-id="12c24-108">Value</span><span class="sxs-lookup"><span data-stu-id="12c24-108">Value</span></span> | <span data-ttu-id="12c24-109">Description</span><span class="sxs-lookup"><span data-stu-id="12c24-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="12c24-110">MCDRemoteSystemDiscoveryTypeAny</span><span class="sxs-lookup"><span data-stu-id="12c24-110">MCDRemoteSystemDiscoveryTypeAny</span></span>   | <span data-ttu-id="12c24-111">0</span><span class="sxs-lookup"><span data-stu-id="12c24-111">0</span></span>     | <span data-ttu-id="12c24-112">Systèmes distants sont détectables via toute connexion.</span><span class="sxs-lookup"><span data-stu-id="12c24-112">Remote systems are discoverable through any connection.</span></span>  |
| <span data-ttu-id="12c24-113">MCDRemoteSystemDiscoveryTypeProximal</span><span class="sxs-lookup"><span data-stu-id="12c24-113">MCDRemoteSystemDiscoveryTypeProximal</span></span> | <span data-ttu-id="12c24-114">1</span><span class="sxs-lookup"><span data-stu-id="12c24-114">1</span></span>     | <span data-ttu-id="12c24-115">Les systèmes à distance ne sont plus détectables via une connexion PROXIMALE, comme une variable locale</span><span class="sxs-lookup"><span data-stu-id="12c24-115">Remote systems are only discoverable through a proximal connection, such as a local</span></span>
<span data-ttu-id="12c24-116">réseau ou une connexion Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="12c24-116">network or Bluetooth connection.</span></span> |
| <span data-ttu-id="12c24-117">MCDRemoteSystemDiscoveryTypeCloud</span><span class="sxs-lookup"><span data-stu-id="12c24-117">MCDRemoteSystemDiscoveryTypeCloud</span></span> | <span data-ttu-id="12c24-118">2</span><span class="sxs-lookup"><span data-stu-id="12c24-118">2</span></span>     | <span data-ttu-id="12c24-119">Systèmes distants ne sont pas identifiables par la connexion de cloud.</span><span class="sxs-lookup"><span data-stu-id="12c24-119">Remote systems are only discoverable through cloud connection.</span></span> |
| <span data-ttu-id="12c24-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span><span class="sxs-lookup"><span data-stu-id="12c24-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span></span> | <span data-ttu-id="12c24-121">3</span><span class="sxs-lookup"><span data-stu-id="12c24-121">3</span></span>     | <span data-ttu-id="12c24-122">Systèmes distants sont détectables via une connexion PROXIMALE et sont supposés être</span><span class="sxs-lookup"><span data-stu-id="12c24-122">Remote systems are discoverable through a proximal connection and are expected to be</span></span>
<span data-ttu-id="12c24-123">dans l’espace proche de l’appareil client (dans la plage de Bluetooth, par exemple).</span><span class="sxs-lookup"><span data-stu-id="12c24-123">spatially near to the client device (in Bluetooth range, for example).</span></span>  |

