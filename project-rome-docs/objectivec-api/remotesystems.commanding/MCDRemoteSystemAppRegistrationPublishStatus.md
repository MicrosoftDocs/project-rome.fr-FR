---
title: MCDRemoteSystemAppRegistrationPublishStatus
description: Contient des valeurs qui décrivent l’état d’un lancement des applications à distance à l’aide d’un URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 32c3e473938925f12838bf6dc5ccc3e98a3394a6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800581"
---
# <a name="enum-mcdremotesystemappregistrationpublishstatus"></a>Enum `MCDRemoteSystemAppRegistrationPublishStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteSystemAppRegistrationPublishStatus)`

Énumération indiquant l’état de l’opération de publication.
Les États d’erreur indiquent où le développeur application peut souhaiter réessayez de publier des conditions transitoires.

| Nom    |Value   |Description   |                  
|------ |------- |--|
|MCDRemoteSystemAppRegistrationPublishStatusSuccess | 0 | Opération achevée avec succès.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoNetwork | 1 | Réseau n’était pas disponible. |
|MCDRemoteSystemAppRegistrationPublishStatusErrorWebFailure | 2 | Échec d’un service web.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoTokenRequestSubscriber | 3 | Aucun abonné demande de jeton a répondu.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorTokenRequestFailed | 4 | Échec de la demande de jeton.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorAccountNotFound | 5 | Impossible de trouver le compte pour publier des informations pour.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorUnknown | 6 | Opération a rencontré une erreur inconnue.|