---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801151"
---
## <a name="preliminary-setup-for-push-notifications"></a>Configuration préliminaire pour les notifications Push

### <a name="register-your-app-for-push-notifications"></a>Inscrire votre application aux notifications Push

Pour assurer une prise en charge d’[Apple Push Notification](https://developer.apple.com/notifications/), inscrivez votre application. Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite. 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>Inscrire votre application pour l’accès à la Plateforme d’appareils connectés inter-appareils

Inscrivez ensuite votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Il s’agit d’une procédure différente de la procédure d’inscription sur le Centre de développement Windows, qui a été abordée précédemment dans les étapes préliminaires. Elle autorise la Plateforme d’appareils connectés à envoyer des notifications à l’aide du service de notification Push natif. Le processus d’intégration du Centre de développement nécessite les éléments suivants :
* L’ID client de votre application.
* La clé du service Apple Push Notification. Ces informations sont nécessaires pour remettre les données et les commandes à l’application (sur un appareil qui est peut-être verrouillé ou en veille) sous forme de notifications. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configurer votre application pour la rendre compatible avec les notifications

Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour lui permettre de recevoir des notifications Push. Tout d’abord, veillez à ajouter la valeur « remote-notifications » à **UIBackgroundMode** dans le fichier _Info.plist_ de votre application pour permettre à celle-ci de recevoir des notifications pendant qu’elle s’exécute en arrière-plan. 

À déterminer

Ensuite, au démarrage de votre application, vous devez demander l’autorisation d’afficher les notifications d’alerte. Pour cela, appelez `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon la version d’iOS que vous ciblez. Une fois que votre application a acquis l’autorisation, vous pouvez l’inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`. 

Certaines notifications en provenance de la Plateforme d’appareils connectés présentent des alertes, dont le texte peut être traduit et ensuite inséré dans les ressources de chaîne de votre application. Vous devez définir les balises de ressource suivantes dans le fichier _en.lproj\Localizable.strings_ de votre application. Vous devrez peut-être créer ce fichier. Dans Xcode, sélectionnez **New**, recherchez le type de fichier « Strings », puis créez un fichier sous le nom _Localizable.strings_.

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>Associer le service de notification à la Plateforme locale

Enfin, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application. Dans les étapes précédentes, vous avez initialisé la plateforme sans définir le paramètre *notificationProvider*. Ici, vous devez construire et transmettre un objet qui implémente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** . La principale chose à noter est la méthode `getNotificationRegistrationAsync:`, qui doit retourner une instance de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** . **MCDNotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.

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
