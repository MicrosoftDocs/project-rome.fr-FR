---
title: MCDConnectedDevicesAccountAddedStatus
description: En savoir plus sur l’énumération MCDConnectedDevicesAccountAddedStatus. Cette énumération contient des valeurs qui décrivent l’état de l’opération d’ajout de compte.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761033"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>variables `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
Contient les valeurs qui décrivent l’état de l’opération d’ajout d’un compte.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | Le compte a été correctement ajouté à la plateforme. |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | Échec de l’opération de compte, car Rome n’a détecté aucun accès réseau. |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | Échec de l’opération de compte, car Rome n’a pas pu contacter les services Web. |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | L’opération de compte a échoué, car l’application n’est pas abonnée à l’événement AccessTokenRequested. |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | L’opération de compte a échoué, car l’application n’a pas réussi à retourner un jeton lors de la demande. |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | L’opération de compte a échoué pour des raisons inconnues. |
