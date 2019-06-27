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
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="30ba5-103">Configuration préliminaire pour les notifications Push</span><span class="sxs-lookup"><span data-stu-id="30ba5-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="30ba5-104">Inscrire votre application aux notifications Push</span><span class="sxs-lookup"><span data-stu-id="30ba5-104">Register your app for push notifications</span></span>

<span data-ttu-id="30ba5-105">Pour assurer une prise en charge d’[Apple Push Notification](https://developer.apple.com/notifications/), inscrivez votre application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="30ba5-106">Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez ; vous en aurez besoin par la suite.</span><span class="sxs-lookup"><span data-stu-id="30ba5-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="30ba5-107">Inscrire votre application pour l’accès à la Plateforme d’appareils connectés inter-appareils</span><span class="sxs-lookup"><span data-stu-id="30ba5-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="30ba5-108">Inscrivez ensuite votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="30ba5-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="30ba5-109">Il s’agit d’une procédure différente de la procédure d’inscription sur le Centre de développement Windows, qui a été abordée précédemment dans les étapes préliminaires.</span><span class="sxs-lookup"><span data-stu-id="30ba5-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="30ba5-110">Elle autorise la Plateforme d’appareils connectés à envoyer des notifications à l’aide du service de notification Push natif.</span><span class="sxs-lookup"><span data-stu-id="30ba5-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="30ba5-111">Le processus d’intégration du Centre de développement nécessite les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="30ba5-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="30ba5-112">L’ID client de votre application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-112">Your app's client ID.</span></span>
* <span data-ttu-id="30ba5-113">La clé du service Apple Push Notification.</span><span class="sxs-lookup"><span data-stu-id="30ba5-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="30ba5-114">Ces informations sont nécessaires pour remettre les données et les commandes à l’application (sur un appareil qui est peut-être verrouillé ou en veille) sous forme de notifications.</span><span class="sxs-lookup"><span data-stu-id="30ba5-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="30ba5-115">Configurer votre application pour la rendre compatible avec les notifications</span><span class="sxs-lookup"><span data-stu-id="30ba5-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="30ba5-116">Après avoir terminé le workflow dans le tableau de bord Développeur, vous devez modifier le code réel de votre application pour lui permettre de recevoir des notifications Push.</span><span class="sxs-lookup"><span data-stu-id="30ba5-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="30ba5-117">Tout d’abord, veillez à ajouter la valeur « remote-notifications » à **UIBackgroundMode** dans le fichier _Info.plist_ de votre application pour permettre à celle-ci de recevoir des notifications pendant qu’elle s’exécute en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="30ba5-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="30ba5-118">À déterminer</span><span class="sxs-lookup"><span data-stu-id="30ba5-118">TBD</span></span>

<span data-ttu-id="30ba5-119">Ensuite, au démarrage de votre application, vous devez demander l’autorisation d’afficher les notifications d’alerte.</span><span class="sxs-lookup"><span data-stu-id="30ba5-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="30ba5-120">Pour cela, appelez `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon la version d’iOS que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="30ba5-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="30ba5-121">Une fois que votre application a acquis l’autorisation, vous pouvez l’inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="30ba5-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="30ba5-122">Certaines notifications en provenance de la Plateforme d’appareils connectés présentent des alertes, dont le texte peut être traduit et ensuite inséré dans les ressources de chaîne de votre application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="30ba5-123">Vous devez définir les balises de ressource suivantes dans le fichier _en.lproj\Localizable.strings_ de votre application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="30ba5-124">Vous devrez peut-être créer ce fichier.</span><span class="sxs-lookup"><span data-stu-id="30ba5-124">You may need to create this file.</span></span> <span data-ttu-id="30ba5-125">Dans Xcode, sélectionnez **New**, recherchez le type de fichier « Strings », puis créez un fichier sous le nom _Localizable.strings_.</span><span class="sxs-lookup"><span data-stu-id="30ba5-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="30ba5-126">Associer le service de notification à la Plateforme locale</span><span class="sxs-lookup"><span data-stu-id="30ba5-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="30ba5-127">Enfin, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="30ba5-128">Dans les étapes précédentes, vous avez initialisé la plateforme sans définir le paramètre *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="30ba5-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="30ba5-129">Ici, vous devez construire et transmettre un objet qui implémente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** .</span><span class="sxs-lookup"><span data-stu-id="30ba5-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="30ba5-130">La principale chose à noter est la méthode `getNotificationRegistrationAsync:`, qui doit retourner une instance de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** .</span><span class="sxs-lookup"><span data-stu-id="30ba5-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="30ba5-131">**MCDNotificationRegistration** est chargé de fournir à la Plateforme d’appareils connectés un jeton d’accès (et les informations associées) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="30ba5-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="30ba5-132">Transmettez cette inscription dans votre implémentation de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="30ba5-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="30ba5-133">Ensuite, l’appel d’initialisation de la Plateforme doit fournir à la Plateforme locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données de la Plateforme d’appareils connectés côté serveur, qui relaie les demandes de lancement et les messages de service d’application d’autres appareils.</span><span class="sxs-lookup"><span data-stu-id="30ba5-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="30ba5-134">Voici une implémentation de **MCDNotificationProvider** à partir de l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="30ba5-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="30ba5-135">L’exemple de code suivant met à jour ce **MCDNotificationProvider** avec un **MCDNotificationRegistration** complété.</span><span class="sxs-lookup"><span data-stu-id="30ba5-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
