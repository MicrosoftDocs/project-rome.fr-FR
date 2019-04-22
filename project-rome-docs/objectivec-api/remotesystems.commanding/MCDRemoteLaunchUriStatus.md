---
title: MCDRemoteLaunchUriStatus
description: Contient des valeurs qui décrivent l’état d’un lancement des applications à distance à l’aide d’un URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 1a0302cd570b8cb25476a8188e3bcb1667707461
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801081"
---
# <a name="enum-mcdremotelaunchuristatus"></a>Enum `MCDRemoteLaunchUriStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteLaunchUriStatus)`

Contient des valeurs qui décrivent l’état d’un lancement des applications à distance à l’aide d’un URI.


| Nom    |Value   |Description   |                  
|------ |------- |--|
|MCDRemoteLaunchUriStatusUnknown | 0| L’état est inconnu.|
|MCDRemoteLaunchUriStatusSuccess | 1| Le lancement à distance a réussi.|
|MCDRemoteLaunchUriStatusAppUnavailable | 2 | L’application cible n’est pas disponible.|
|MCDRemoteLaunchUriStatusProtocolUnavailable | 3 | L’application cible ne prend pas en charge cet URI.|
|MCDRemoteLaunchUriStatusRemoteSystemUnavailable | 4 | L’appareil auquel le message a été envoyé n’est pas disponible.|
|MCDRemoteLaunchUriStatusValueSetTooLarge | 5 | Le groupe de données envoyé à l’application cible était trop grand.|
|MCDRemoteLaunchUriStatusDeniedByLocalSystem | 6 | Le système client a empêché l’utilisation de la plateforme de systèmes à distance.|
|MCDRemoteLaunchUriStatusDeniedByRemoteSystem | 7 | L’appareil cible a empêché l’utilisation de la plateforme de systèmes à distance.|