---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907681"
---
### <a name="create-the-platform"></a>Créer la plateforme

Pour commencer simplement instancier la plateforme.

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur 

La plateforme nécessite un utilisateur authentifié accéder à la plateforme.  Vous devrez vous abonner à **ConnectedDevicesAccountManager** événements afin d’assurer un compte valide est utilisé. 

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenRequested().subscribe((accountManager, args) -> {

    // Get access token
                 
}
```

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenInvalidated().subscribe((accountManager, args) -> {

    // Refresh and renew existing access token
    
}
```


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>S’abonner aux événements de ConnectedDevicesNotificationRegistrationManager

De même, la plateforme utilise des notifications pour fournir des commandes entre les appareils.  Par conséquent, vous devez vous abonner à la **ConnectedDevicesNotificationRegistrationManager** événements afin d’assurer les États de l’inscription du cloud sont valides pour le compte utilisé.  Vérifier l’état à l’aide **ConnectedDevicesNotificationRegistrationState**

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```