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
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="625a9-103">Créer une instance de la plateforme</span><span class="sxs-lookup"><span data-stu-id="625a9-103">Create an instance of the platform</span></span>

<span data-ttu-id="625a9-104">Pour commencer, instanciez simplement la plateforme.</span><span class="sxs-lookup"><span data-stu-id="625a9-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="625a9-105">S’abonner à MCDConnectedDevicesAccountManager</span><span class="sxs-lookup"><span data-stu-id="625a9-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="625a9-106">Pour pouvoir accéder à la plateforme, l’utilisateur doit être authentifié.</span><span class="sxs-lookup"><span data-stu-id="625a9-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="625a9-107">Vous devrez vous abonner aux événements **MCDConnectedDevicesAccountManager** pour être certain qu’un compte valide est utilisé.</span><span class="sxs-lookup"><span data-stu-id="625a9-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="625a9-108">S’abonner à MCDConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="625a9-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="625a9-109">De la même manière, la plateforme utilise des notifications pour la transmission de commandes entre les appareils.</span><span class="sxs-lookup"><span data-stu-id="625a9-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="625a9-110">Par conséquent, vous devez vous abonner aux événements **MCDConnectedDevicesNotificationRegistrationManager** pour faire en sorte que les états d’inscription cloud sont valides pour le compte utilisé.</span><span class="sxs-lookup"><span data-stu-id="625a9-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="625a9-111">Vérifiez l’état à l’aide de **MCDConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="625a9-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="625a9-112">Démarrer la plateforme</span><span class="sxs-lookup"><span data-stu-id="625a9-112">Start the platform</span></span>
<span data-ttu-id="625a9-113">Maintenant que la plateforme est initialisée et que les gestionnaires d’événements sont en place, vous êtes prêt à démarrer la découverte de périphériques système distants.</span><span class="sxs-lookup"><span data-stu-id="625a9-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="625a9-114">Récupérer les comptes d’utilisateurs connus de l’application</span><span class="sxs-lookup"><span data-stu-id="625a9-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="625a9-115">Il est important de vérifier que la liste des comptes d’utilisateurs connus de l’application est correctement synchronisée avec **MCDConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="625a9-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="625a9-116">Utilisez **MCDConnectedDevicesAccountManager.addAccountAsync** pour ajouter un nouveau compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="625a9-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="625a9-117">Pour supprimer un compte non valide, vous pouvez utiliser **MCDConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="625a9-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```