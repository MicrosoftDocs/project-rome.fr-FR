---
title: MCDRemoteSystemAuthorizationKind
description: Contient des valeurs qui décrivent les types d’autorisation potentiel (étendues d’autorisation basée sur le compte d’utilisateur) pour la découverte du système distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801321"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a>Enum `MCDRemoteSystemAuthorizationKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

Contient des valeurs qui décrivent les types d’autorisation potentiel (étendues d’autorisation basée sur le compte d’utilisateur) pour la découverte du système distant. 

## <a name="fields"></a>Champs

| Nom                              | Value | Description                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemAuthorizationKindSameUser   | 0     | Le système peut uniquement découvrir et connexion d’appareils par le même compte d’utilisateur est connectés à.   |
| MCDRemoteSystemAuthorizationKindAnonymous | 1     | Le système peut détecter et se connecter avec les appareils des autres utilisateurs autant qu’elles sont trouve à proximité et autoriser la détection anonyme.  |

