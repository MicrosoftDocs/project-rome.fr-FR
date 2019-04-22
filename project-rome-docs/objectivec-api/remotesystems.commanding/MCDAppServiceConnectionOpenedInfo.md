---
title: MCDAppServiceConnectionOpenedInfo
description: Cette classe fournit des données pour l’événement MCDAppServiceProvider.connectionDidOpen, qui est déclenché quand un appareil distant ouvre une connexion à un service de l’application locale.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801071"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a>Classe `MCDAppServiceConnectionOpenedInfo` 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

Cette classe fournit des données pour l’événement MCDAppServiceProvider.connectionDidOpen, qui est déclenché quand un appareil distant ouvre une connexion à un service de l’application locale.

## <a name="properties"></a>Properties

### <a name="appserviceconnection"></a>appServiceConnection
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

Une instance de MCDAppServiceConnection qui représente la connexion entre le service d’application local et le périphérique distant.

### <a name="remotesystemapp"></a>remoteSystemApp
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

L’application distante MCDRemoteSystemApp qui a lancé une connexion au service d’application local.