---
title: MCDAppServiceConnectionStatus
description: Contient des valeurs qui décrivent l’état d’une connexion à un service d’application distant.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: cf272326ce5c88f7c847a2a03eafe5b8bbbaa56e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901637"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>variables `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

Contient des valeurs qui décrivent l’état d’une connexion à un service d’application distant. Consultez [création et utilisation d’un app service](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations sur les services app services sur les appareils Windows.

|Nom   |Valeur   |Description   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| La connexion à App service a été ouverte avec succès.|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| Le package pour l’app service sur lequel une connexion a été tentée n’est pas installé sur l’appareil. Vérifiez que le package est installé avant d’essayer d’ouvrir une connexion à App service.|
|MCDAppServiceConnectionStatusAppUnavailable | 2| Le package pour l’app service sur lequel une connexion a été tentée est temporairement indisponible. Réessayez de vous connecter ultérieurement.|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| L’application avec l’ID de package spécifié est installée et disponible, mais l’application ne déclare pas la prise en charge de l’app service spécifié. Vérifiez que le nom de l’app service et la version de l’application sont corrects.|
|MCDAppServiceConnectionStatusUnknown | 4| La connexion n’a pas pu être établie pour une raison inconnue.|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| L’appareil ou l’application distant cible n’est plus disponible pour la connexion.|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|L’application cliente n’est pas configurée pour prendre en charge la connectivité à distance.|
|MCDAppServiceConnectionStatusNotAuthorized | 7| L’appareil client n’est pas autorisé à prendre en charge la connectivité à distance. Cela peut se produire si un jeton non valide a été passé au MCDAppServiceConnection.|