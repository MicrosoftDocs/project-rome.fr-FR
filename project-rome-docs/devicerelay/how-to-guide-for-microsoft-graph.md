---
title: Utilisation des API REST de relais d’appareils de Microsoft Graph
ms.openlocfilehash: 887ebff8788ac4300036512761df80c6b8e5e97f
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "75207818"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="67134-102">Utilisation des API REST de relais d’appareils de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="67134-102">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="67134-103">Les fonctionnalités de relais d’appareils peuvent être implémentées au moyen d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="67134-103">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="67134-104">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span><span class="sxs-lookup"><span data-stu-id="67134-104">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="67134-105">Une implémentation avec Microsoft Graph vous permet de découvrir vos appareils, de lancer des applications et d’interagir avec les services d’application à partir de n’importe quel appareil capable d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="67134-105">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="67134-106">Avec Microsoft Graph, ces scénarios sont plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et n’offre pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="67134-106">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>