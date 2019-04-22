---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801601"
---
### <a name="add-the-sdk"></a><span data-ttu-id="6ed97-103">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="6ed97-103">Add the SDK</span></span>

<span data-ttu-id="6ed97-104">Le plus simple pour ajouter la plateforme d’appareils connectés à votre application iOS consiste à l’aide de la [CocoaPods](https://cocoapods.org/) Gestionnaire de dépendances.</span><span class="sxs-lookup"><span data-stu-id="6ed97-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="6ed97-105">Accédez à votre projet iOS *Podfile* et insérez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="6ed97-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> <span data-ttu-id="6ed97-106">Afin de consommer CocoaPod, vous devez utiliser le _.xcworkspace_ fichier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="6ed97-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="6ed97-107">Initialiser la plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="6ed97-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="6ed97-108">Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="6ed97-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="6ed97-109">Vous devez instancier le **MCDPlatform** classe.</span><span class="sxs-lookup"><span data-stu-id="6ed97-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="6ed97-110">Le **MCDPlatform**de `platformWithAccountProvider:` méthode accepte deux paramètres : un **MCDUserAccountProvider** et un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="6ed97-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="6ed97-111">Le **MCDNotificationProvider** paramètre n’est nécessaire pour l’hébergement d’applications à distance et les activités de l’utilisateur, qui ne sont pas traités dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="6ed97-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="6ed97-112">Il peut être laissée `nil` pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="6ed97-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="6ed97-113">Le **MCDUserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="6ed97-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="6ed97-114">Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée.</span><span class="sxs-lookup"><span data-stu-id="6ed97-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="6ed97-115">Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous avons fourni des implémentations de fournisseur pour Android et iOS de compte.</span><span class="sxs-lookup"><span data-stu-id="6ed97-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="6ed97-116">Ces implémentations, trouvé dans le [exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), peut être utilisé pour obtenir le jeton d’accès OAuth 2.0 et actualiser le jeton pour votre application.</span><span class="sxs-lookup"><span data-stu-id="6ed97-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="6ed97-117">Le code suivant à partir de l’exemple d’application illustre l’initialisation de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6ed97-117">The following code from the sample app shows the initialization of the platform.</span></span>

```ObjectiveC
- (void)initializePlatform
{
    // Only register for APNs if this app is enabled for push notifications
    NotificationProvider* notificationProvider;
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        notificationProvider = [AppDataSource sharedInstance].notificationProvider;
    }
    else
    {
        NSLog(@"Initializing platform without a notification provider!");
        notificationProvider = nil;
    }

    // Initialize platform
    [AppDataSource sharedInstance].platform = [MCDPlatform platformWithAccountProvider:[AppDataSource sharedInstance].accountProvider notificationProvider:notificationProvider];

    // ...
}
```

<span data-ttu-id="6ed97-118">Arrêter la plateforme quand votre application s’arrête au premier plan en appelant le `shutdownAsync:` (méthode).</span><span class="sxs-lookup"><span data-stu-id="6ed97-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
