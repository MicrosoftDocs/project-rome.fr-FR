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
### <a name="add-the-sdk"></a>Ajouter le kit SDK

Le moyen le plus simple d’ajouter la Plateforme d’appareils connectés à votre application iOS est d’utiliser le gestionnaire de dépendances [CocoaPods](https://cocoapods.org/). Accédez au fichier *Podfile* de votre projet iOS et insérez l’entrée suivante :

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
> Pour utiliser CocoaPod, vous devez utiliser le fichier _.xcworkspace_ dans votre projet.

## <a name="initialize-the-connected-devices-platform"></a>Initialiser la Plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application. 

Vous devez instancier la classe **MCDPlatform**. La méthode `platformWithAccountProvider:` de **MCDPlatform** accepte deux paramètres : **MCDUserAccountProvider** et **MCDNotificationProvider**. Le paramètre **MCDNotificationProvider** est nécessaire uniquement pour l’hébergement d’applications distantes et les activités utilisateur, sujets non abordés dans ce guide. Pour l’instant, il peut rester `nil`.

Le paramètre **MCDUserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés. Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme. 

Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Android et iOS. Ces implémentations, qui se trouvent dans l’[exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), permettent d’obtenir le jeton d’accès OAuth 2.0 et le jeton d’actualisation pour votre application.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

Le code suivant tiré de l’exemple d’application illustre l’initialisation de la plateforme.

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

Arrêtez la plateforme au moment où votre application quitte le premier plan en appelant la méthode `shutdownAsync:`.
