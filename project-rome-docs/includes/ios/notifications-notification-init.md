---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801501"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>TODO Configurer votre application pour la rendre compatible avec les notifications d’APNs

Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour lui permettre de recevoir des notifications Push. Tout d’abord, veillez à ajouter la valeur « remote-notifications » à **UIBackgroundMode** dans le fichier _Info.plist_ de votre application pour permettre à celle-ci de recevoir des notifications pendant qu’elle s’exécute en arrière-plan. 

Ensuite, au démarrage de votre application, vous devez demander l’autorisation d’afficher les notifications d’alerte. Pour cela, appelez `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon la version d’iOS que vous ciblez. Une fois que votre application a acquis l’autorisation, vous pouvez l’inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`. 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>Associez la Plateforme d’appareils connectés à une notification Push native d’APNs pour iOS. 
Comme nous l’avons vu précédemment, les clients d’application doivent faire connaître au kit SDK côté client et à la Plateforme d’appareils connectés pendant le processus d’inscription le pipeline de notification Push natif qui est utilisé pour chaque plateforme mobile, ceci pour permettre au service de notification Graph de distribuer les notifications à chaque point de terminaison client d’application quand votre serveur d’applications publie une notification ciblant l’utilisateur via les API MS Graph.

Dans les étapes précédentes, vous avez initialisé la plateforme sans définir le paramètre *notificationProvider*. Ici, vous devez construire et transmettre un objet qui implémente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** . La principale chose à noter est la méthode `getNotificationRegistrationAsync:`, qui doit retourner une instance de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** . **MCDNotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.

Transmettez cette inscription dans votre implémentation de **MCDNotificationProvider**. Ensuite, l’appel d’initialisation de la Plateforme doit fournir à la Plateforme locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données de la Plateforme d’appareils connectés côté serveur, qui relaie les demandes de lancement et les messages de service d’application d’autres appareils. 

Voici une implémentation de **MCDNotificationProvider** à partir de l’exemple d’application.

```ObjectiveC
@implementation NotificationProvider
{
    MCDRegistrationUpdatedEvent* _registrationUpdated;
    MCDNotificationRegistration* _notificationRegistration;
}

+ (instancetype)sharedInstance
{
    static NotificationProvider* sharedInstance = nil;

    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{ sharedInstance = [[NotificationProvider alloc] init]; });

    return sharedInstance;
}

+ (void)updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
        ^{ [[NotificationProvider sharedInstance] _updateNotificationRegistration:notificationRegistration]; });
}

// MCDNotificationProvider
@synthesize registrationUpdated = _registrationUpdated;

- (void)getNotificationRegistrationAsync:(nonnull void (^)(MCDNotificationRegistration* _Nullable, NSError* _Nullable))completionBlock
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{ completionBlock(_notificationRegistration, nil); });
}

- (instancetype)init
{
    if (self = [super init])
    {
        _registrationUpdated = [MCDRegistrationUpdatedEvent new];
    }

    return self;
}

- (void)_updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    _notificationRegistration = notificationRegistration;

    [_registrationUpdated raiseWithNotificationRegistration:notificationRegistration];
}
@end
```

L’exemple de code suivant met à jour ce **MCDNotificationProvider** avec un **MCDNotificationRegistration** complété.

```ObjectiveC
/*
* NotificationRegistration is constructed with four parameters:
* Type: This is GCM or FCM or APN (the notification platform type).
* Token: This is the NSData that APNs sends to your app delegate's didRegisterForRemoteNotificationsWithDeviceToken: method. You must convert the NSData into a string by hex-encoding it.
* SenderId: This is your app’s bundle identifier. 
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
[NotificationProvider
    updateNotificationRegistration:[[MCDNotificationRegistration alloc]
        initWithNotificationType:MCDNotificationTypeAPN
        token:deviceTokenStr
        appId:[[NSBundle mainBundle] bundleIdentifier]
        appDisplayName:(NSString*)[[NSBundle mainBundle]
            objectForInfoDictionaryKey:@"CFBundleDisplayName"]]];
```
