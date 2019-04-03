---
title: MCDConnectedDevicesAccountAddedStatus
description: Contient les valeurs qui décrivent l’état de l’opération Ajouter compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907201"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>Enum `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
Contient les valeurs qui décrivent l’état de l’opération Ajouter compte.

## <a name="fields"></a>Champs

| Nom                              |   Value     | Description |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | Le compte a été correctement ajouté à la plateforme. |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | L’opération de compte a échoué, car Rome ne détecté aucun accès réseau. |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | L’opération de compte a échoué, car Rome n’a pas pu contacter les services web. |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | L’opération de compte a échoué, car l’application n’a pas s’abonner à l’événement AccessTokenRequested. |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | L’opération de compte a échoué, car l’application n’a pas retourné un jeton demandé. |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | L’opération de compte a échoué pour une raison inconnue. |
