---
title: MCDConnectedDevicesProcessNotificationOperation
description: Le résultat de donner une notification à la plateforme Rome pour traitement.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: cb482e7b00cd5fe090de1708388d140cfd45777b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909891"
---
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a>Classe `MCDConnectedDevicesProcessNotificationOperation` 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
Le résultat de donner une notification APNS à la plateforme d’appareils connectés pour le traitement.

> [!NOTE] 
> Cette classe est déconseillée, utilisez MCDConnectedDevicesNotification à la place. 

## <a name="properties"></a>Properties

### <a name="connecteddevicesnotification"></a>connectedDevicesNotification
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

Il s’agit d’un indicateur qui spécifie si la notification a été conçue pour la plateforme d’appareils connectés.

## <a name="methods"></a>Méthodes

### <a name="waitforcompletionasync"></a>waitForCompletionAsync
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 Attendez que la notification se termine en cours de traitement.

#### <a name="parameters"></a>Paramètres 
* `callback` 

Le résultat de rappel d’achèvement de la notification.
