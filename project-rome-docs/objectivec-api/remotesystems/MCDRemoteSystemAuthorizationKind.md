---
title: MCDRemoteSystemAuthorizationKind
description: Contient des valeurs qui décrivent les types d’autorisation potentiel (étendues d’autorisation basée sur le compte d’utilisateur) pour la découverte du système distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801321"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a><span data-ttu-id="a4917-104">Enum `MCDRemoteSystemAuthorizationKind`</span><span class="sxs-lookup"><span data-stu-id="a4917-104">enum `MCDRemoteSystemAuthorizationKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

<span data-ttu-id="a4917-105">Contient des valeurs qui décrivent les types d’autorisation potentiel (étendues d’autorisation basée sur le compte d’utilisateur) pour la découverte du système distant.</span><span class="sxs-lookup"><span data-stu-id="a4917-105">Contains values that describe the potential authorization kinds (user-account-based authorization scopes) for remote system discovery.</span></span> 

## <a name="fields"></a><span data-ttu-id="a4917-106">Champs</span><span class="sxs-lookup"><span data-stu-id="a4917-106">Fields</span></span>

| <span data-ttu-id="a4917-107">Nom</span><span class="sxs-lookup"><span data-stu-id="a4917-107">Name</span></span>                              | <span data-ttu-id="a4917-108">Value</span><span class="sxs-lookup"><span data-stu-id="a4917-108">Value</span></span> | <span data-ttu-id="a4917-109">Description</span><span class="sxs-lookup"><span data-stu-id="a4917-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="a4917-110">MCDRemoteSystemAuthorizationKindSameUser</span><span class="sxs-lookup"><span data-stu-id="a4917-110">MCDRemoteSystemAuthorizationKindSameUser</span></span>   | <span data-ttu-id="a4917-111">0</span><span class="sxs-lookup"><span data-stu-id="a4917-111">0</span></span>     | <span data-ttu-id="a4917-112">Le système peut uniquement découvrir et connexion d’appareils par le même compte d’utilisateur est connectés à.</span><span class="sxs-lookup"><span data-stu-id="a4917-112">The system can only discover and connect with devices signed onto by the same user account.</span></span>   |
| <span data-ttu-id="a4917-113">MCDRemoteSystemAuthorizationKindAnonymous</span><span class="sxs-lookup"><span data-stu-id="a4917-113">MCDRemoteSystemAuthorizationKindAnonymous</span></span> | <span data-ttu-id="a4917-114">1</span><span class="sxs-lookup"><span data-stu-id="a4917-114">1</span></span>     | <span data-ttu-id="a4917-115">Le système peut détecter et se connecter avec les appareils des autres utilisateurs autant qu’elles sont trouve à proximité et autoriser la détection anonyme.</span><span class="sxs-lookup"><span data-stu-id="a4917-115">The system can discover and connect with other users' devices, provided they are in proximity and allow anonymous discovery.</span></span>  |

