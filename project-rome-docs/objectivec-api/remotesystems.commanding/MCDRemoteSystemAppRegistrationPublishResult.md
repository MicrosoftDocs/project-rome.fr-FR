---
title: MCDRemoteSystemAppRegistrationPublishResult
description: Une classe communique le résultat asynchrone de publication informations sur l’application système distant pour un compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909921"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a>Classe `MCDRemoteSystemAppRegistrationPublishResult` 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

Cette classe communique le résultat asynchrone de publication informations sur l’application système distant pour un compte. Les États d’erreur communiqués via ce résultat doivent servir par l’application à la nouvelle tentative de publication en cas de certaines conditions transitoires telles que le réseau ne soit pas disponible.

## <a name="properties"></a>Properties

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

Énumération d’état de l’opération de publication.