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
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a>Utilisation des API REST Activités de l’utilisateur de Microsoft Graph

La fonctionnalité Activités de l’utilisateur peut être implémentée par le biais d’appels d’API REST avec Microsoft Graph. Des informations supplémentaires et une documentation de référence sur les API sont disponibles dans la [section Projet Rome de la documentation Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).

Cela vous permet de créer, de publier, de mettre à jour et de lire des activités de l’utilisateur de style Windows à partir de tout appareil en mesure d’effectuer des requêtes HTTP. Microsoft Graph rend ces scénarios plus simples à implémenter que sur les SDK des plateformes natives, mais il ne prend pas en charge toutes les fonctionnalités du projet Rome et ne fournit pas non plus de modèle objet natif.