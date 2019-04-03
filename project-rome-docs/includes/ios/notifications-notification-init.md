---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907431"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>TODO configurer votre application à être APNs compatible avec notification

Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour vérifier capable de recevoir des notifications push. Tout d’abord, veillez à ajouter « à distance-notifications » **UIBackgroundMode** à votre application _Info.plist_ pour permettre à l’application recevoir des notifications lors de l’exécution en arrière-plan. 

En second lieu, au démarrage de votre application, vous devez demander l’autorisation pour afficher les notifications d’alerte. Cela est effectué en appelant soit `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon quelle version d’e/s que vous ciblez. Une fois que votre application a acquis l’autorisation, vous pouvez inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`. 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>Associer la plateforme d’appareils connectés à une notification push native APNs pour iOS. 
Comme mentionné précédemment, les clients d’application doivent apportent des informations sur le pipeline de notification push natif utilisé pour chaque plateforme mobile pour le Kit de développement côté client et la plateforme d’appareils connectés pendant le processus d’inscription, pour permettre à Graph service de notification pour les notifications de sortance pour chaque point de terminaison du client d’application lorsque votre serveur d’applications publie une notification utilisateur de multi-ciblage via MS Graph API.

Dans les étapes ci-dessus, vous avez initialisé la plateforme sans définir le *notificationProvider* paramètre. Ici, vous devez construire et passez un objet qui implémente  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**. La principale chose à noter est la `getNotificationRegistrationAsync:` (méthode), qui doit retourner un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance. Le **MCDNotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.

Fournir cette inscription dans votre implémentation de **MCDNotificationProvider**. Ensuite, l’appel de l’initialisation de plate-forme doit fournir la plateforme locale avec accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir de la plateforme des appareils connectés de côté serveur, qui relaie les demandes de lancement et les messages de service à partir de l’application d’autres périphériques. 

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

L’exemple de code suivant met à jour cet **MCDNotificationProvider** avec un renseignés **MCDNotificationRegistration**.

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
