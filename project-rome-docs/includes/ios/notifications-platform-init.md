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
### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Le plus simple pour ajouter la plateforme d’appareils connectés à votre application iOS consiste à l’aide de la [CocoaPods](https://cocoapods.org/) Gestionnaire de dépendances. Accédez à votre projet iOS *Podfile* et insérez l’entrée suivante :

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
> Afin de consommer CocoaPod, vous devez utiliser le _.xcworkspace_ fichier dans votre projet.

## <a name="initialize-the-connected-devices-platform"></a>Initialiser la plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application. 

Vous devez instancier le **MCDPlatform** classe. Le **MCDPlatform**de `platformWithAccountProvider:` méthode accepte deux paramètres : un **MCDUserAccountProvider** et un **MCDNotificationProvider**. Le **MCDNotificationProvider** paramètre n’est nécessaire pour l’hébergement d’applications à distance et les activités de l’utilisateur, qui ne sont pas traités dans ce guide. Il peut être laissée `nil` pour l’instant.

Le **MCDUserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés. Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée. 

Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous avons fourni des implémentations de fournisseur pour Android et iOS de compte. Ces implémentations, trouvé dans le [exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), peut être utilisé pour obtenir le jeton d’accès OAuth 2.0 et actualiser le jeton pour votre application.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

Le code suivant à partir de l’exemple d’application illustre l’initialisation de la plateforme.

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

Arrêter la plateforme quand votre application s’arrête au premier plan en appelant le `shutdownAsync:` (méthode).
