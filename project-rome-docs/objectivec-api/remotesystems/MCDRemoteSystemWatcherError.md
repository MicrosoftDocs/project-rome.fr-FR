---
title: MCDRemoteSystemWatcherError
description: Contient des valeurs describe une erreur rencontrée par un objet de l’Observateur système distant pendant le processus de découverte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801721"
---
# <a name="enum-mcdremotesystemwatchererror"></a>Enum `MCDRemoteSystemWatcherError` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 Contient des valeurs describe une erreur rencontrée par un objet de l’Observateur système distant pendant le processus de découverte.

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemWatcherErrorUnknown | 0 | L’Observateur a rencontré une erreur inconnue. |
| MCDRemoteSystemWatcherErrorInternetNotAvailable | 1 | L’erreur s’est produite, car la connexion Internet a été perdue. |
| MCDRemoteSystemWatcherErrorAuthenticationError | 2 | L’erreur s’est produite, car un ConnectedDevicesAccount utilisé pour exécuter la découverte n’a pas pu être authentifié. | 
