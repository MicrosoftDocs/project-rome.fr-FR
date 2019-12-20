---
title: Utilisation des API REST Activités de l’utilisateur de Microsoft Graph
ms.openlocfilehash: efb5b591ca4c1f3024e1fb19dceee783dc75dc8c
ms.sourcegitcommit: 5670ff536ea9bfcd678cfde54f262a1ec5c8add4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207898"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="1f925-102">Utilisation des API REST Activités de l’utilisateur de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="1f925-102">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="1f925-103">La fonctionnalité Activités de l’utilisateur peut être implémentée par le biais d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="1f925-103">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="1f925-104">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span><span class="sxs-lookup"><span data-stu-id="1f925-104">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="1f925-105">Cela vous permet de créer, de publier, de mettre à jour et de lire des activités de l’utilisateur de style Windows à partir de tout appareil en mesure d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f925-105">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="1f925-106">Microsoft Graph rend ces scénarios plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et ne fournit pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="1f925-106">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>