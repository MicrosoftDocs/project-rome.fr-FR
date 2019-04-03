---
title: MCDConnectedDevicesPlatformSettings
description: Une interface pour permettre des paramètres de plateforme de périphériques connectés à stocker dans un emplacement particulier.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9753553cefbbeaff598550687b8dfa5100d2006e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908891"
---
# <a name="class-mcdconnecteddevicesplatformsettings"></a><span data-ttu-id="fcbf5-104">Classe `MCDConnectedDevicesPlatformSettings`</span><span class="sxs-lookup"><span data-stu-id="fcbf5-104">class `MCDConnectedDevicesPlatformSettings`</span></span> 

```
@interface MCDConnectedDevicesPlatformSettings : NSObject
```  
<span data-ttu-id="fcbf5-105">Une interface pour permettre des paramètres de plateforme de périphériques connectés à stocker dans un emplacement particulier.</span><span class="sxs-lookup"><span data-stu-id="fcbf5-105">An interface to allow Connected Devices Platform settings to be stored in a particular location.</span></span>  

## <a name="properties"></a><span data-ttu-id="fcbf5-106">Properties</span><span class="sxs-lookup"><span data-stu-id="fcbf5-106">Properties</span></span>

### <a name="storagepath"></a><span data-ttu-id="fcbf5-107">storagePath</span><span class="sxs-lookup"><span data-stu-id="fcbf5-107">storagePath</span></span>
`@property (nonatomic, readwrite, nonnull) NSString* storagePath;`

<span data-ttu-id="fcbf5-108">Le chemin d’accès à l’emplacement de stockage des paramètres de plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="fcbf5-108">The path to the storage location of the Connected Devices Platform settings.</span></span>