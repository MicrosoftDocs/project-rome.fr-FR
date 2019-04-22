---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801501"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="28abc-103">TODO configurer votre application à être APNs compatible avec notification</span><span class="sxs-lookup"><span data-stu-id="28abc-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="28abc-104">Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour vérifier capable de recevoir des notifications push.</span><span class="sxs-lookup"><span data-stu-id="28abc-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="28abc-105">Tout d’abord, veillez à ajouter « à distance-notifications » **UIBackgroundMode** à votre application _Info.plist_ pour permettre à l’application recevoir des notifications lors de l’exécution en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="28abc-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="28abc-106">En second lieu, au démarrage de votre application, vous devez demander l’autorisation pour afficher les notifications d’alerte.</span><span class="sxs-lookup"><span data-stu-id="28abc-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="28abc-107">Cela est effectué en appelant soit `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon quelle version d’e/s que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="28abc-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="28abc-108">Une fois que votre application a acquis l’autorisation, vous pouvez inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="28abc-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="28abc-109">Associer la plateforme d’appareils connectés à une notification push native APNs pour iOS.</span><span class="sxs-lookup"><span data-stu-id="28abc-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="28abc-110">Comme mentionné précédemment, les clients d’application doivent apportent des informations sur le pipeline de notification push natif utilisé pour chaque plateforme mobile pour le Kit de développement côté client et la plateforme d’appareils connectés pendant le processus d’inscription, pour permettre à Graph service de notification pour les notifications de sortance pour chaque point de terminaison du client d’application lorsque votre serveur d’applications publie une notification utilisateur de multi-ciblage via MS Graph API.</span><span class="sxs-lookup"><span data-stu-id="28abc-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="28abc-111">Dans les étapes ci-dessus, vous avez initialisé la plateforme sans définir le *notificationProvider* paramètre.</span><span class="sxs-lookup"><span data-stu-id="28abc-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="28abc-112">Ici, vous devez construire et passez un objet qui implémente  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span><span class="sxs-lookup"><span data-stu-id="28abc-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="28abc-113">La principale chose à noter est la `getNotificationRegistrationAsync:` (méthode), qui doit retourner un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span><span class="sxs-lookup"><span data-stu-id="28abc-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="28abc-114">Le **MCDNotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="28abc-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="28abc-115">Fournir cette inscription dans votre implémentation de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="28abc-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="28abc-116">Ensuite, l’appel de l’initialisation de plate-forme doit fournir la plateforme locale avec accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir de la plateforme des appareils connectés de côté serveur, qui relaie les demandes de lancement et les messages de service à partir de l’application d’autres périphériques.</span><span class="sxs-lookup"><span data-stu-id="28abc-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="28abc-117">Voici une implémentation de **MCDNotificationProvider** à partir de l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="28abc-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="28abc-118">L’exemple de code suivant met à jour cet **MCDNotificationProvider** avec un renseignés **MCDNotificationRegistration**.</span><span class="sxs-lookup"><span data-stu-id="28abc-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
