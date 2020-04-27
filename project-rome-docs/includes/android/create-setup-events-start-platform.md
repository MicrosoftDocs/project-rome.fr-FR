---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 0ac6a543cc63be9154e40482e587a8f373f56798
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755795"
---
### <a name="create-the-platform"></a><span data-ttu-id="a2dc3-103">Créer la plateforme</span><span class="sxs-lookup"><span data-stu-id="a2dc3-103">Create the platform</span></span>


<span data-ttu-id="a2dc3-104">Pour commencer, instanciez simplement la plateforme.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="a2dc3-105">S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a2dc3-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="a2dc3-106">Pour pouvoir accéder à la plateforme, l’utilisateur doit être authentifié.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="a2dc3-107">Vous devrez vous abonner aux événements **ConnectedDevicesAccountManager** pour être certain qu’un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="a2dc3-108">S’abonner aux événements ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="a2dc3-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="a2dc3-109">De la même manière, la plateforme utilise des notifications pour la transmission de commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="a2dc3-110">Par conséquent, vous devez vous abonner aux événements **ConnectedDevicesNotificationRegistrationManager** pour faire en sorte que les états d’inscription cloud soient valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="a2dc3-111">Vérifiez l’état à l’aide de **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="a2dc3-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="a2dc3-112">Démarrer la plateforme</span><span class="sxs-lookup"><span data-stu-id="a2dc3-112">Start the platform</span></span>
<span data-ttu-id="a2dc3-113">Maintenant que la plateforme est initialisée et que les gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte d’appareils système distants.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="a2dc3-114">Récupérer les comptes d’utilisateurs connus de l’application</span><span class="sxs-lookup"><span data-stu-id="a2dc3-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="a2dc3-115">Il est important de vérifier que la liste des comptes d’utilisateur connus de l’application est correctement synchronisée avec **ConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="a2dc3-116">Utilisez **ConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="a2dc3-117">Pour supprimer un compte non valide, vous pouvez utiliser **ConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="a2dc3-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```