---
title: Utilisation des API REST Activités de l’utilisateur de Microsoft Graph
description: Utilisez les API REST Activités utilisateur de Microsoft Graph pour créer, publier, mettre à jour et lire des activités utilisateur de type Windows.
ms.openlocfilehash: 7ec7a2f285ed0b1875bf8d945534b8b89de566f3
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760073"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="bfeb5-103">Utilisation des API REST Activités de l’utilisateur de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="bfeb5-103">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="bfeb5-104">La fonctionnalité Activités de l’utilisateur peut être implémentée par le biais d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="bfeb5-104">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="bfeb5-105">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span><span class="sxs-lookup"><span data-stu-id="bfeb5-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="bfeb5-106">Cela vous permet de créer, de publier, de mettre à jour et de lire des activités de l’utilisateur de style Windows à partir de tout appareil en mesure d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="bfeb5-106">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="bfeb5-107">Microsoft Graph rend ces scénarios plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et ne fournit pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="bfeb5-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>