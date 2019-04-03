---
title: MCDStatelessAppServiceResponseStatus
description: Contient des valeurs qui décrivent l’état d’un message envoyé à partir du service d’une application vers un autre (si les données du message a été remises avec succès).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9d01e892861c8551b7b3e41d1b227f65f07d752a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907871"
---
# <a name="enum-mcdstatelessappserviceresponsestatus"></a>Enum `MCDStatelessAppServiceResponseStatus`

`typedef NS_ENUM(NSInteger, MCDStatelessAppServiceResponseStatus)`

 Contient des valeurs qui décrivent l’état d’un message envoyé à partir du service d’une application vers un autre (si les données du message a été remises avec succès).


| Nom    |Value   |Description   |                  
|------ |------- |--|
|MCDStatelessAppServiceResponseStatusSuccess | 0| Le message a été remis correctement. |
|MCDStatelessAppServiceResponseStatusAppNotInstalled | 1| Le package pour le service d’application à laquelle une connexion a été tentée n’est pas installé sur l’appareil. Vérifiez que le package est installé avant d’essayer d’ouvrir une connexion au service de p theap. |
|MCDStatelessAppServiceResponseStatusAppUnavailable | 2 | Le package pour le service d’application à laquelle une connexion a été tentée est temporairement indisponible. Tentez de vous connecter plus tard. |
|MCDStatelessAppServiceResponseStatusAppServiceUnavailable | 3 | L’application avec l’ID de package spécifié est installé et disponible, mais l’application ne déclare pas de prise en charge pour le service de l’application spécifiée. Vérifiez que le nom du service d’application et la version de l’application sont corrects. |
|MCDStatelessAppServiceResponseStatusRemoteSystemUnavailable | 4 | Le message n’a pas été remis, car une connexion à l’appareil distant n’a pas pu être établie.|
|MCDStatelessAppServiceResponseStatusRemoteSystemNotSupportedByApp | 5 | L’application distante n’est pas configurée pour prendre en charge la connectivité à distance. |
|MCDStatelessAppServiceResponseStatusNotAuthorized | 6 | Le service d’application n’est pas autorisé à communiquer avec le périphérique distant. |
|MCDStatelessAppServiceResponseStatusResourceLimitsExceeded | 7 | Le message n’a pas été remis, car elle a dépassé les limites de mémoire programme du service application distante.|
|MCDStatelessAppServiceResponseStatusMessageSizeTooLarge | 8 | Le message n’a pas été remis, car elle dépasse la taille autorisée. |
|MCDStatelessAppServiceResponseStatusFailure | 9 | Le message n’a pas été remis en raison d’une panne réseau. |
|MCDStatelessAppServiceResponseStatusUnknown | 10 |Le message n'a pas été remis pour une raison inconnue. |