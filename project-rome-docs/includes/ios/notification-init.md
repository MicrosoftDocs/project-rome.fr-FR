---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801151"
---
## <a name="preliminary-setup-for-push-notifications"></a>Programme d’installation préliminaire pour les notifications push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application pour les notifications push

Inscrire votre application pour [Apns](https://developer.apple.com/notifications/) prennent en charge. Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard. 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>Inscrire votre application formulaire inter-périphériques plate-forme de périphériques connectés d’accéder

Ensuite, enregistrez votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une autre procédure de s’inscrire sur le centre de développement Windows, qui a été abordé dans les étapes préliminaires ci-dessus. Elle autorise la plateforme d’appareils connectés pour envoyer des notifications à l’aide du service de notifications push natif. Le centre de développement nécessitera des processus d’intégration :
* ID de client. de votre application
* La clé de Service de Notification Push Apple. Cela est nécessaire pour fournir des données et des commandes à l’application (sur un appareil qui peut être verrouillé ou en veille) sous la forme de notifications. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configurer votre application pour être compatible avec notification

Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour vérifier capable de recevoir des notifications push. Tout d’abord, veillez à ajouter « à distance-notifications » **UIBackgroundMode** à votre application _Info.plist_ pour permettre à l’application recevoir des notifications lors de l’exécution en arrière-plan. 

À déterminer

En second lieu, au démarrage de votre application, vous devez demander l’autorisation pour afficher les notifications d’alerte. Cela est effectué en appelant soit `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon quelle version d’e/s que vous ciblez. Une fois que votre application a acquis l’autorisation, vous pouvez inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`. 

Certaines notifications à partir de la plateforme d’appareils connectés présente les alertes, et le texte de ces alertes est localisable et doit être inséré dans les ressources de chaîne de votre application. Vous devez définir les balises de ressources suivantes de votre application _en.lproj\Localizable.strings_ fichier. Vous devrez peut-être créer ce fichier. Dans Xcode, sélectionnez **New**, recherchez le type de fichier « Chaînes » et créez un fichier appelé _Localizable.strings_.

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>Associer le service de notification de la plateforme locale

Enfin, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application. Dans les étapes ci-dessus, vous avez initialisé la plateforme sans définir le *notificationProvider* paramètre. Ici, vous devez construire et passez un objet qui implémente  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**. La principale chose à noter est la `getNotificationRegistrationAsync:` (méthode), qui doit retourner un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance. Le **MCDNotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.

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
