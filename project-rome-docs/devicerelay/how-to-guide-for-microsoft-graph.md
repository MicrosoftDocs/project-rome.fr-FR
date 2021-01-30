---
title: Utilisation des API REST de relais d’appareils de Microsoft Graph
description: Découvrez comment utiliser les API REST Relais d’appareils de Microsoft Graph pour découvrir vos appareils, lancer des applications et interagir avec des services d’application.
ms.openlocfilehash: e72bf1c4bc52bddfe84fd09a7588c664aca2d709
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901437"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="79b3d-103">Utilisation des API REST de relais d’appareils de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="79b3d-103">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="79b3d-104">Les fonctionnalités de relais d’appareils peuvent être implémentées au moyen d’appels d’API REST avec Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="79b3d-104">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="79b3d-105">Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](/graph/api/resources/project-rome-overview#devices).</span><span class="sxs-lookup"><span data-stu-id="79b3d-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](/graph/api/resources/project-rome-overview#devices).</span></span>

<span data-ttu-id="79b3d-106">Une implémentation avec Microsoft Graph vous permet de découvrir vos appareils, de lancer des applications et d’interagir avec les services d’application à partir de n’importe quel appareil capable d’effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b3d-106">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="79b3d-107">Avec Microsoft Graph, ces scénarios sont plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et n’offre pas non plus de modèle objet natif.</span><span class="sxs-lookup"><span data-stu-id="79b3d-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>