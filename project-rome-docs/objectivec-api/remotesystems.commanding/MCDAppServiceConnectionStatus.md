---
title: MCDAppServiceConnectionStatus
description: Contient des valeurs qui décrivent l’état d’une connexion à un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5beba7ae30d8ffd9149c5e8a599eacc38213b6d2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801451"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>Enum `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

Contient des valeurs qui décrivent l’état d’une connexion à un service d’application à distance. Consultez [créer et consommer un service d’application](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) pour plus d’informations sur les services d’application sur les appareils Windows.

|Nom   |Value   |Description   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| La connexion au service d’application a été ouverte avec succès.|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| Le package pour le service d’application à laquelle une connexion a été tentée n’est pas installé sur l’appareil. Vérifiez que le package est installé avant d’essayer d’ouvrir une connexion au service d’application.|
|MCDAppServiceConnectionStatusAppUnavailable | 2| Le package pour le service d’application à laquelle une connexion a été tentée est temporairement indisponible. Tentez de vous connecter plus tard.|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| L’application avec l’ID de package spécifié est installé et disponible, mais l’application ne déclare pas de prise en charge pour le service de l’application spécifiée. Vérifiez que le nom du service d’application et la version de l’application sont corrects.|
|MCDAppServiceConnectionStatusUnknown | 4| La connexion n’a pas pu être établie pour une raison inconnue.|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| Le périphérique distant cible ou l’application n’est plus disponible pour la connexion.|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|L’application cliente n’est pas configurée pour prendre en charge la connectivité à distance.|
|MCDAppServiceConnectionStatusNotAuthorized | 7| L’appareil client n’est pas autorisé à prendre en charge la connectivité à distance. Cela peut se produire, car la MCDAppServiceConnection a été passée à un jeton non valide.|