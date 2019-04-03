---
title: MCDRemoteSystemConnectionInfo
description: Une classe qui fournit des informations sur une instance donnée de MCDAppServiceConnection complémentaires.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907051"
---
# <a name="class-mcdremotesystemconnectioninfo"></a>Classe `MCDRemoteSystemConnectionInfo` 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

Une classe qui fournit des informations complémentaires sur une donnée **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instance.

## <a name="properties"></a>Properties

### <a name="proximal"></a>proximal
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

Indique si la connexion associée est une connexion PROXIMALE (**Oui**) ou non (**non**).

## <a name="constructors"></a>Constructeurs

### <a name="trycreatefromappserviceconnection"></a>tryCreateFromAppServiceConnection
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

Crée une instance de cette classe à partir de la connexion de service d’application donnée.

#### <a name="parameters"></a>Paramètres
* `appServiceConnection` 

Un **MCDAppServiceConnection** instance.

#### <a name="returns"></a>Returns
Retourne une instance de cette classe correspondant à la connexion de service d’application.