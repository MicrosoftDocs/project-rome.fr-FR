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
### <a name="create-the-platform"></a><span data-ttu-id="a4b75-103">Créer la plateforme</span><span class="sxs-lookup"><span data-stu-id="a4b75-103">Create the platform</span></span>

<span data-ttu-id="a4b75-104">Pour commencer simplement instancier la plateforme.</span><span class="sxs-lookup"><span data-stu-id="a4b75-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="a4b75-105">S’abonner aux événements ConnectedDevicesAccountManager pour gérer le compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a4b75-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="a4b75-106">La plateforme nécessite un utilisateur authentifié accéder à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="a4b75-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="a4b75-107">Vous devrez vous abonner à **ConnectedDevicesAccountManager** événements afin d’assurer un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a4b75-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="a4b75-108">S’abonner aux événements de ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="a4b75-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="a4b75-109">De même, la plateforme utilise des notifications pour fournir des commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="a4b75-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="a4b75-110">Par conséquent, vous devez vous abonner à la **ConnectedDevicesNotificationRegistrationManager** événements afin d’assurer les États de l’inscription du cloud sont valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="a4b75-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="a4b75-111">Vérifier l’état à l’aide **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="a4b75-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```