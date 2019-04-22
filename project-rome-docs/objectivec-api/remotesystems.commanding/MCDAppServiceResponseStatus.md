---
title: MCDAppServiceResponseStatus
description: Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800331"
---
# <a name="enum-mcdappserviceresponsestatus"></a>Enum `MCDAppServiceResponseStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

Contient des valeurs qui décrivent l’état d’un message de réponse à partir d’un service d’application à distance.

|Nom         | Value  | Description    |                           
|--------|-------------|-----|
|MCDAppServiceResponseStatusSuccess |0| Le service d’application correctement reçu et traité le message.|
|MCDAppServiceResponseStatusFailure |1| Échec de l’app service recevoir et traiter le message.|
|MCDAppServiceResponseStatusResourceLimitsExceeded |2| Le service d’application s’est arrêté car pas suffisamment de ressources n’est disponible.|
|MCDAppServiceResponseStatusUnknown |3| Une erreur inconnue s’est produite.|
|MCDAppServiceResponseStatusRemoteSystemUnavailable |4| L’appareil auquel le message a été envoyé n’est pas disponible.|
|MCDAppServiceResponseStatusMessageTooLarge |5| Le service de l’application a échoué traiter le message, car il est trop volumineux.|
|MCDAppServiceResponseStatusAppServiceConnectionClosed|6| La connexion de service d’application a été fermée avant une réponse a été envoyée.|