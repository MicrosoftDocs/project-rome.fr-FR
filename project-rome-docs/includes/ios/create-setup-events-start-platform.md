---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907211"
---
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="95bd5-103">Créez une instance de la plateforme</span><span class="sxs-lookup"><span data-stu-id="95bd5-103">Create an instance of the platform</span></span>

<span data-ttu-id="95bd5-104">Pour commencer simplement instancier la plateforme.</span><span class="sxs-lookup"><span data-stu-id="95bd5-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="95bd5-105">S’abonner à MCDConnectedDevicesAccountManager</span><span class="sxs-lookup"><span data-stu-id="95bd5-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="95bd5-106">La plateforme nécessite un utilisateur authentifié accéder à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="95bd5-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="95bd5-107">Vous devrez vous abonner à **MCDConnectedDevicesAccountManager** événements afin d’assurer un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="95bd5-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="95bd5-108">S’abonner à MCDConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="95bd5-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="95bd5-109">De même, la plateforme utilise des notifications pour fournir des commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="95bd5-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="95bd5-110">Par conséquent, vous devez vous abonner à la **MCDConnectedDevicesNotificationRegistrationManager** événements afin d’assurer les États de l’inscription du cloud sont valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="95bd5-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="95bd5-111">Vérifier l’état à l’aide **MCDConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="95bd5-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="95bd5-112">Démarrer la plateforme</span><span class="sxs-lookup"><span data-stu-id="95bd5-112">Start the platform</span></span>
<span data-ttu-id="95bd5-113">Maintenant que la plateforme est initialisée et gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte des périphériques système à distance.</span><span class="sxs-lookup"><span data-stu-id="95bd5-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="95bd5-114">Récupérer les comptes d’utilisateur connus pour l’application</span><span class="sxs-lookup"><span data-stu-id="95bd5-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="95bd5-115">Il est important de s’assurer que la liste des comptes d’utilisateur connu à l’application sont correctement synchronisées avec le **MCDConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="95bd5-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="95bd5-116">Utilisez **MCDConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95bd5-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="95bd5-117">Pour supprimer un compte non valide, vous pouvez utiliser **MCDConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="95bd5-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```