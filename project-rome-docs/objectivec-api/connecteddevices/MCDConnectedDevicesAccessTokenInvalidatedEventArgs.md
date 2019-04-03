---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: Informer de ce jeton associé ConnectedDevicesAccount a signalé une erreur de jeton.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907491"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a><span data-ttu-id="5e491-104">Classe `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="5e491-104">class `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
<span data-ttu-id="5e491-105">Retourné par MCDConnectedDevicesAccount pour informer que le jeton associé MCDConnectedDevicesAccount a signalé une erreur de jeton pour les étendues de relation contenant-contenus.</span><span class="sxs-lookup"><span data-stu-id="5e491-105">Returned by MCDConnectedDevicesAccount to inform that the token associated with MCDConnectedDevicesAccount reported token error for the contained scopes.</span></span> <span data-ttu-id="5e491-106">Fournisseur de jetons doit actualiser son cache de jeton ou potentiellement affiche l’interface utilisateur de demander à l’utilisateur pour se connecter afin de corriger leur configuration de compte.</span><span class="sxs-lookup"><span data-stu-id="5e491-106">Token provider needs to either refresh their token cache or potentially pop up UI to ask user to sign in in order to fix their account setup.</span></span>

## <a name="properties"></a><span data-ttu-id="5e491-107">Properties</span><span class="sxs-lookup"><span data-stu-id="5e491-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="5e491-108">compte</span><span class="sxs-lookup"><span data-stu-id="5e491-108">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="5e491-109">Le compte associé à cette MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="5e491-109">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="5e491-110">Étendues</span><span class="sxs-lookup"><span data-stu-id="5e491-110">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="5e491-111">La liste des étendues pour laquelle le jeton doit couvrir lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="5e491-111">The list of scopes for which the token must cover when generated.</span></span>