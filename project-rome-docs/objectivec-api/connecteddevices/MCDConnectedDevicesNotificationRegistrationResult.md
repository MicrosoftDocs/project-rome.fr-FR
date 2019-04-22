---
title: MCDConnectedDevicesNotificationRegistrationResult
description: Communique le résultat asynchrone de l’inscription des informations de notification pour un compte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801351"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a>Classe `MCDConnectedDevicesNotificationRegistrationResult` 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
MCDConnectedDevicesNotificationRegistrationResult communique le résultat asynchrone de l’inscription des informations de notification pour un compte. Les États d’erreur communiqués via ce résultat doivent servir par l’application à l’inscription de nouvelle tentative en cas de certaines conditions transitoires telles que le réseau ne soit pas disponible.

## <a name="properties"></a>Properties

### <a name="status"></a>status

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

Énumération d’état de l’opération d’inscription.