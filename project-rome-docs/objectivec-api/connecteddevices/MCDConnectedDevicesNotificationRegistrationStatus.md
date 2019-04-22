---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: Valeurs utilisées pour communiquer l’état de l’inscription du cloud.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801361"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a>Classe `MCDConnectedDevicesNotificationRegistrationStatus` 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
Énumération indiquant l’état de l’opération d’inscription.
Les États d’erreur indiquent des conditions transitoires où le développeur d’applications peut souhaitez réessayer l’inscription.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStatusSuccess | 0 | Opération achevée avec succès.
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork | 1 | Réseau n’était pas disponible. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure | 2 | Échec d’un service web. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber | 3 | Aucun abonné demande de jeton a répondu. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed | 4 | Échec de la demande de jeton. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound | 5 | Impossible de trouver le compte pour inscrire les informations pour. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown | 6 | Opération a rencontré une erreur inconnue. |