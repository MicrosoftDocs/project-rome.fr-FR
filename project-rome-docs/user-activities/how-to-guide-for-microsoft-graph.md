---
ms.openlocfilehash: 8fd5cb9176bbde99598a95b51c1f2bba513ae187
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801111"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="f4d75-101">Utilisation des API REST Activités de l’utilisateur de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f4d75-101">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="f4d75-102">La fonctionnalité Activités de l’utilisateur peut être implémentée par le biais d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="f4d75-102">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="f4d75-103">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span><span class="sxs-lookup"><span data-stu-id="f4d75-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="f4d75-104">Cela vous permet de créer, de publier, de mettre à jour et de lire des activités de l’utilisateur de style Windows à partir de tout appareil en mesure d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4d75-104">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="f4d75-105">Microsoft Graph rend ces scénarios plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et ne fournit pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="f4d75-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>