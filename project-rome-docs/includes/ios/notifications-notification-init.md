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
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="957de-103">TODO Configurer votre application pour la rendre compatible avec les notifications d’APNs</span><span class="sxs-lookup"><span data-stu-id="957de-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="957de-104">Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour lui permettre de recevoir des notifications Push.</span><span class="sxs-lookup"><span data-stu-id="957de-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="957de-105">Tout d’abord, veillez à ajouter la valeur « remote-notifications » à **UIBackgroundMode** dans le fichier _Info.plist_ de votre application pour permettre à celle-ci de recevoir des notifications pendant qu’elle s’exécute en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="957de-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="957de-106">Ensuite, au démarrage de votre application, vous devez demander l’autorisation d’afficher les notifications d’alerte.</span><span class="sxs-lookup"><span data-stu-id="957de-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="957de-107">Pour cela, appelez `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon la version d’iOS que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="957de-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="957de-108">Une fois que votre application a acquis l’autorisation, vous pouvez l’inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="957de-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="957de-109">Associez la Plateforme d’appareils connectés à une notification Push native d’APNs pour iOS.</span><span class="sxs-lookup"><span data-stu-id="957de-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="957de-110">Comme nous l’avons vu précédemment, les clients d’application doivent faire connaître au kit SDK côté client et à la Plateforme d’appareils connectés pendant le processus d’inscription le pipeline de notification Push natif qui est utilisé pour chaque plateforme mobile, ceci pour permettre au service de notification Graph de distribuer les notifications à chaque point de terminaison client d’application quand votre serveur d’applications publie une notification ciblant l’utilisateur via les API MS Graph.</span><span class="sxs-lookup"><span data-stu-id="957de-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="957de-111">Dans les étapes précédentes, vous avez initialisé la plateforme sans définir le paramètre *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="957de-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="957de-112">Ici, vous devez construire et transmettre un objet qui implémente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** .</span><span class="sxs-lookup"><span data-stu-id="957de-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="957de-113">La principale chose à noter est la méthode `getNotificationRegistrationAsync:`, qui doit retourner une instance de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** .</span><span class="sxs-lookup"><span data-stu-id="957de-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="957de-114">**MCDNotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="957de-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="957de-115">Transmettez cette inscription dans votre implémentation de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="957de-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="957de-116">Ensuite, l’appel d’initialisation de la Plateforme doit fournir à la Plateforme locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données de la Plateforme d’appareils connectés côté serveur, qui relaie les demandes de lancement et les messages de service d’application d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="957de-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="957de-117">Voici une implémentation de **MCDNotificationProvider** à partir de l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="957de-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="957de-118">L’exemple de code suivant met à jour ce **MCDNotificationProvider** avec un **MCDNotificationRegistration** complété.</span><span class="sxs-lookup"><span data-stu-id="957de-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
