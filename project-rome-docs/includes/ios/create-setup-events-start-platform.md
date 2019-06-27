---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59803975"
---
### <a name="create-an-instance-of-the-platform"></a>Créer une instance de la plateforme

Pour commencer, instanciez simplement la plateforme.

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a>S’abonner à MCDConnectedDevicesAccountManager

Pour pouvoir accéder à la plateforme, l’utilisateur doit être authentifié.  Vous devrez vous abonner aux événements **MCDConnectedDevicesAccountManager** pour être certain qu’un compte valide est utilisé.

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager.accessTokenRequested
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenRequestedEventArgs* _Nonnull request __unused) {

                    // Get access token

                 }
```

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.platform.accountManager.accessTokenInvalidated
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenInvalidatedEventArgs* _Nonnull request) {

                      // Refresh and renew existing access token

                 }
```

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a>S’abonner à MCDConnectedDevicesNotificationRegistrationManager

De la même manière, la plateforme utilise des notifications pour la transmission de commandes entre les appareils.  Par conséquent, vous devez vous abonner aux événements **MCDConnectedDevicesNotificationRegistrationManager** pour faire en sorte que les états d’inscription cloud sont valides pour le compte utilisé.  Vérifiez l’état à l’aide de **MCDConnectedDevicesNotificationRegistrationState**

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a>Démarrer la plateforme
Maintenant que la plateforme est initialisée et que les gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte de périphériques système distants.  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a>Récupérer les comptes d’utilisateurs connus de l’application

Il est important de vérifier que la liste des comptes d’utilisateurs connus de l’application est correctement synchronisée avec **MCDConnectedDevicesAccountManager**.

Utilisez **MCDConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

Pour supprimer un compte non valide, vous pouvez utiliser **MCDConnectedDevicesAccountManager.removeAccountAsync**

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```