---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801601"
---
### <a name="add-the-sdk"></a><span data-ttu-id="3708f-103">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="3708f-103">Add the SDK</span></span>

<span data-ttu-id="3708f-104">Le moyen le plus simple d’ajouter la Plateforme d’appareils connectés à votre application iOS est d’utiliser le gestionnaire de dépendances [CocoaPods](https://cocoapods.org/).</span><span class="sxs-lookup"><span data-stu-id="3708f-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="3708f-105">Accédez au fichier *Podfile* de votre projet iOS et insérez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="3708f-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="3708f-106">Pour utiliser CocoaPod, vous devez utiliser le fichier _.xcworkspace_ dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="3708f-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="3708f-107">Initialiser la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="3708f-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="3708f-108">Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="3708f-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="3708f-109">Vous devez instancier la classe **MCDPlatform**.</span><span class="sxs-lookup"><span data-stu-id="3708f-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="3708f-110">La méthode `platformWithAccountProvider:` de **MCDPlatform** accepte deux paramètres : **MCDUserAccountProvider** et **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="3708f-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="3708f-111">Le paramètre **MCDNotificationProvider** est nécessaire uniquement pour l’hébergement d’applications distantes et les activités utilisateur, sujets non abordés dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="3708f-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="3708f-112">Pour l’instant, il peut rester `nil`.</span><span class="sxs-lookup"><span data-stu-id="3708f-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="3708f-113">Le paramètre **MCDUserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="3708f-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="3708f-114">Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="3708f-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="3708f-115">Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Android et iOS.</span><span class="sxs-lookup"><span data-stu-id="3708f-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="3708f-116">Ces implémentations, qui se trouvent dans l’[exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), permettent d’obtenir le jeton d’accès OAuth 2.0 et le jeton d’actualisation pour votre application.</span><span class="sxs-lookup"><span data-stu-id="3708f-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="3708f-117">Le code suivant tiré de l’exemple d’application illustre l’initialisation de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="3708f-117">The following code from the sample app shows the initialization of the platform.</span></span>

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

<span data-ttu-id="3708f-118">Arrêtez la plateforme au moment où votre application quitte le premier plan en appelant la méthode `shutdownAsync:`.</span><span class="sxs-lookup"><span data-stu-id="3708f-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
