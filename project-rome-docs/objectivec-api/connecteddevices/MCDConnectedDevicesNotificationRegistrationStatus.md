---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: En savoir plus sur la classe MCDConnectedDevicesNotificationRegistrationStatus. Ces valeurs sont utilisées pour communiquer l’état de l’inscription du Cloud.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: a7dd06a4593203f60275a540702ccfc164aa6b59
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761103"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a>type `MCDConnectedDevicesNotificationRegistrationStatus` 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
Énumération indiquant l’état de l’opération d’inscription.
Les États d’erreur indiquent des conditions transitoires où le développeur de l’application souhaite réessayer l’inscription.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStatusSuccess | 0 | Opération exécutée avec succès.
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork | 1 | Le réseau n’était pas disponible. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure | 2 | Un service Web a échoué. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber | 3 | Aucun abonné aux demandes de jeton n’a répondu. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed | 4 | Échec de la demande de jeton. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound | 5 | Le compte pour lequel enregistrer des informations est introuvable. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown | 6 | L’opération a rencontré une erreur inconnue. |