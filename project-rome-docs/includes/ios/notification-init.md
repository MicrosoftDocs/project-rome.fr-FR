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
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="30302-103">Programme d’installation préliminaire pour les notifications push</span><span class="sxs-lookup"><span data-stu-id="30302-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="30302-104">Inscrire votre application pour les notifications push</span><span class="sxs-lookup"><span data-stu-id="30302-104">Register your app for push notifications</span></span>

<span data-ttu-id="30302-105">Inscrire votre application pour [Apns](https://developer.apple.com/notifications/) prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="30302-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="30302-106">Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez ; vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="30302-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="30302-107">Inscrire votre application formulaire inter-périphériques plate-forme de périphériques connectés d’accéder</span><span class="sxs-lookup"><span data-stu-id="30302-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="30302-108">Ensuite, enregistrez votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="30302-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="30302-109">Il s’agit d’une autre procédure de s’inscrire sur le centre de développement Windows, qui a été abordé dans les étapes préliminaires ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="30302-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="30302-110">Elle autorise la plateforme d’appareils connectés pour envoyer des notifications à l’aide du service de notifications push natif.</span><span class="sxs-lookup"><span data-stu-id="30302-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="30302-111">Le centre de développement nécessitera des processus d’intégration :</span><span class="sxs-lookup"><span data-stu-id="30302-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="30302-112">ID de client. de votre application</span><span class="sxs-lookup"><span data-stu-id="30302-112">Your app's client ID.</span></span>
* <span data-ttu-id="30302-113">La clé de Service de Notification Push Apple.</span><span class="sxs-lookup"><span data-stu-id="30302-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="30302-114">Cela est nécessaire pour fournir des données et des commandes à l’application (sur un appareil qui peut être verrouillé ou en veille) sous la forme de notifications.</span><span class="sxs-lookup"><span data-stu-id="30302-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="30302-115">Configurer votre application pour être compatible avec notification</span><span class="sxs-lookup"><span data-stu-id="30302-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="30302-116">Après avoir terminé le flux de travail sur le tableau de bord du développeur, vous devez modifier le code réel de votre application pour vérifier capable de recevoir des notifications push.</span><span class="sxs-lookup"><span data-stu-id="30302-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="30302-117">Tout d’abord, veillez à ajouter « à distance-notifications » **UIBackgroundMode** à votre application _Info.plist_ pour permettre à l’application recevoir des notifications lors de l’exécution en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="30302-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="30302-118">À déterminer</span><span class="sxs-lookup"><span data-stu-id="30302-118">TBD</span></span>

<span data-ttu-id="30302-119">En second lieu, au démarrage de votre application, vous devez demander l’autorisation pour afficher les notifications d’alerte.</span><span class="sxs-lookup"><span data-stu-id="30302-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="30302-120">Cela est effectué en appelant soit `-[UIApplication registerUsernotificationSettings:categories:]` ou `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, selon quelle version d’e/s que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="30302-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="30302-121">Une fois que votre application a acquis l’autorisation, vous pouvez inscrire pour recevoir des notifications à distance en appelant `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="30302-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="30302-122">Certaines notifications à partir de la plateforme d’appareils connectés présente les alertes, et le texte de ces alertes est localisable et doit être inséré dans les ressources de chaîne de votre application.</span><span class="sxs-lookup"><span data-stu-id="30302-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="30302-123">Vous devez définir les balises de ressources suivantes de votre application _en.lproj\Localizable.strings_ fichier.</span><span class="sxs-lookup"><span data-stu-id="30302-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="30302-124">Vous devrez peut-être créer ce fichier.</span><span class="sxs-lookup"><span data-stu-id="30302-124">You may need to create this file.</span></span> <span data-ttu-id="30302-125">Dans Xcode, sélectionnez **New**, recherchez le type de fichier « Chaînes » et créez un fichier appelé _Localizable.strings_.</span><span class="sxs-lookup"><span data-stu-id="30302-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="30302-126">Associer le service de notification de la plateforme locale</span><span class="sxs-lookup"><span data-stu-id="30302-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="30302-127">Enfin, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="30302-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="30302-128">Dans les étapes ci-dessus, vous avez initialisé la plateforme sans définir le *notificationProvider* paramètre.</span><span class="sxs-lookup"><span data-stu-id="30302-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="30302-129">Ici, vous devez construire et passez un objet qui implémente  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span><span class="sxs-lookup"><span data-stu-id="30302-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="30302-130">La principale chose à noter est la `getNotificationRegistrationAsync:` (méthode), qui doit retourner un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span><span class="sxs-lookup"><span data-stu-id="30302-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="30302-131">Le **MCDNotificationRegistration** est responsable de la fourniture de la plateforme d’appareils connectés avec un jeton d’accès (et des informations connexes) pour le service de notification.</span><span class="sxs-lookup"><span data-stu-id="30302-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="30302-132">Fournir cette inscription dans votre implémentation de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="30302-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="30302-133">Ensuite, l’appel de l’initialisation de plate-forme doit fournir la plateforme locale avec accès au service de notifications push, ce qui permet de votre application à recevoir des données à partir de la plateforme des appareils connectés de côté serveur, qui relaie les demandes de lancement et les messages de service à partir de l’application d’autres périphériques.</span><span class="sxs-lookup"><span data-stu-id="30302-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="30302-134">Voici une implémentation de **MCDNotificationProvider** à partir de l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="30302-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="30302-135">L’exemple de code suivant met à jour cet **MCDNotificationProvider** avec un renseignés **MCDNotificationRegistration**.</span><span class="sxs-lookup"><span data-stu-id="30302-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
