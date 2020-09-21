---
title: Utilisation des API REST de relais d’appareils de Microsoft Graph
description: Découvrez comment utiliser les API REST Relais d’appareils de Microsoft Graph pour découvrir vos appareils, lancer des applications et interagir avec des services d’application.
ms.openlocfilehash: a2433e5a16f36edb9e8283d885f9ebf3d05b64d1
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760803"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="b14ed-103">Utilisation des API REST de relais d’appareils de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="b14ed-103">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="b14ed-104">Les fonctionnalités de relais d’appareils peuvent être implémentées au moyen d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="b14ed-104">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="b14ed-105">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span><span class="sxs-lookup"><span data-stu-id="b14ed-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="b14ed-106">Une implémentation avec Microsoft Graph vous permet de découvrir vos appareils, de lancer des applications et d’interagir avec les services d’application à partir de n’importe quel appareil capable d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="b14ed-106">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="b14ed-107">Avec Microsoft Graph, ces scénarios sont plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et n’offre pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="b14ed-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>