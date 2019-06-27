---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 0ac6a543cc63be9154e40482e587a8f373f56798
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755795"
---
### <a name="create-the-platform"></a>Créer la plateforme


Pour commencer, instanciez simplement la plateforme.

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur 

Pour pouvoir accéder à la plateforme, l’utilisateur doit être authentifié.  Vous devrez vous abonner aux événements **ConnectedDevicesAccountManager** pour être certain qu’un compte valide est utilisé. 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>S’abonner aux événements ConnectedDevicesNotificationRegistrationManager

De la même manière, la plateforme utilise des notifications pour la transmission de commandes entre les appareils.  Par conséquent, vous devez vous abonner aux événements **ConnectedDevicesNotificationRegistrationManager** pour faire en sorte que les états d’inscription cloud soient valides pour le compte utilisé.  Vérifiez l’état à l’aide de **ConnectedDevicesNotificationRegistrationState**

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a>Démarrer la plateforme
Maintenant que la plateforme est initialisée et que les gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte d’appareils système distants.  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a>Récupérer les comptes d’utilisateur connus de l’application

Il est important de vérifier que la liste des comptes d’utilisateur connus de l’application est correctement synchronisée avec **ConnectedDevicesAccountManager**.

Utilisez **ConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

Pour supprimer un compte non valide, vous pouvez utiliser **ConnectedDevicesAccountManager.removeAccountAsync**

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```