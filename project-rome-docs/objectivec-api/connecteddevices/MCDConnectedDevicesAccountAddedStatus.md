---
title: MCDConnectedDevicesAccountAddedStatus
description: Contient les valeurs qui décrivent l’état de l’opération Ajouter compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801561"
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
