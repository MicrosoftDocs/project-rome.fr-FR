---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d498d192b6ac909e8b3978b54e6996eef98d2814
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803972"
---
### <a name="create-the-platform"></a><span data-ttu-id="5f17e-103">Créer la plateforme</span><span class="sxs-lookup"><span data-stu-id="5f17e-103">Create the platform</span></span>


<span data-ttu-id="5f17e-104">Pour commencer simplement instancier la plateforme.</span><span class="sxs-lookup"><span data-stu-id="5f17e-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="5f17e-105">S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5f17e-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="5f17e-106">La plateforme nécessite un utilisateur authentifié accéder à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="5f17e-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="5f17e-107">Vous devrez vous abonner à **ConnectedDevicesAccountManager** événements afin d’assurer un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5f17e-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="5f17e-108">S’abonner aux événements de ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="5f17e-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="5f17e-109">De même, la plateforme utilise des notifications pour fournir des commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="5f17e-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="5f17e-110">Par conséquent, vous devez vous abonner à la **ConnectedDevicesNotificationRegistrationManager** événements afin d’assurer les États de l’inscription du cloud sont valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="5f17e-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="5f17e-111">Vérifier l’état à l’aide **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="5f17e-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="5f17e-112">Démarrer la plateforme</span><span class="sxs-lookup"><span data-stu-id="5f17e-112">Start the platform</span></span>
<span data-ttu-id="5f17e-113">Maintenant que la plateforme est initialisée et gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte des périphériques système à distance.</span><span class="sxs-lookup"><span data-stu-id="5f17e-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="5f17e-114">Récupérer les comptes d’utilisateur connus pour l’application</span><span class="sxs-lookup"><span data-stu-id="5f17e-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="5f17e-115">Il est important de s’assurer que la liste des comptes d’utilisateur connu à l’application sont correctement synchronisées avec le **ConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="5f17e-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="5f17e-116">Utilisez **ConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f17e-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="5f17e-117">Pour supprimer un compte non valide, vous pouvez utiliser **ConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="5f17e-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```