---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800291"
---
### <a name="create-the-platform"></a><span data-ttu-id="ad418-103">Créer la plateforme</span><span class="sxs-lookup"><span data-stu-id="ad418-103">Create the platform</span></span>

<span data-ttu-id="ad418-104">Pour commencer, instanciez simplement la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ad418-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="ad418-105">S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="ad418-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="ad418-106">Pour pouvoir accéder à la plateforme, l’utilisateur doit être authentifié.</span><span class="sxs-lookup"><span data-stu-id="ad418-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="ad418-107">Vous devrez vous abonner aux événements **ConnectedDevicesAccountManager** pour être certain qu’un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ad418-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="ad418-108">S’abonner aux événements ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="ad418-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="ad418-109">De la même manière, la plateforme utilise des notifications pour la transmission de commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="ad418-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="ad418-110">Par conséquent, vous devez vous abonner aux événements **ConnectedDevicesNotificationRegistrationManager** pour faire en sorte que les états d’inscription cloud soient valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="ad418-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="ad418-111">Vérifiez l’état à l’aide de **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="ad418-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```