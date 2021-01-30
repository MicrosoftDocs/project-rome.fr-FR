---
title: Publication et lecture d’activités de l’utilisateur (iOS)
description: Ce guide montre comment créer, publier et lire des activités de l’utilisateur Windows dans votre application iOS.
ms.topic: article
keywords: microsoft, windows, projet rome, activités de l’utilisateur, ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 95345d8fb4d8dd600ec0dc447ea38c29612402d1
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901677"
---
# <a name="implementing-user-activities-for-ios"></a><span data-ttu-id="fa778-104">Implémentation d’activités de l’utilisateur pour iOS</span><span class="sxs-lookup"><span data-stu-id="fa778-104">Implementing User Activities for iOS</span></span>

<span data-ttu-id="fa778-105">Les activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application.</span><span class="sxs-lookup"><span data-stu-id="fa778-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="fa778-106">Elles permettent d’enregistrer une capture instantanée d’une tâche en cours à poursuivre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="fa778-106">They make it possible to save a snapshot of a current task to be continued at a later time.</span></span> <span data-ttu-id="fa778-107">La fonctionnalité [Chronologie Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représentées sous forme de cartes comportant du texte et des graphiques.</span><span class="sxs-lookup"><span data-stu-id="fa778-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="fa778-108">Pour plus d’informations sur les activités de l’utilisateur en général, consultez [Poursuivre l’activité utilisateur, même sur différents appareils](/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="fa778-108">For more information about User Activities in general, see [Continue user activity, even across devices](/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="fa778-109">Pour savoir quand créer ou mettre à jour des activités, consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](/windows/uwp/launch-resume/useractivities-best-practices).</span><span class="sxs-lookup"><span data-stu-id="fa778-109">For recommendations on when to create or update Activities, see the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="fa778-110">Avec le SDK Projet Rome, votre application iOS peut non seulement publier des activités de l’utilisateur pour une utilisation dans des fonctionnalités Windows telles que la Chronologie, mais elle peut également agir comme point de terminaison et relire des activités à l’utilisateur comme le fait la Chronologie.</span><span class="sxs-lookup"><span data-stu-id="fa778-110">With the Project Rome SDK, your iOS app can not only publish User Activities for use in Windows features such as Timeline, but it can also act as an endpoint and read Activities back to the user just as Timeline does.</span></span> <span data-ttu-id="fa778-111">Cela permet aux applications inter-appareils de transcender totalement leurs plateformes et de proposer des expériences qui suivent les utilisateurs plutôt que les appareils.</span><span class="sxs-lookup"><span data-stu-id="fa778-111">This allows cross-device apps to completely transcend their platforms and present experiences that follow users rather than devices.</span></span>

<span data-ttu-id="fa778-112">Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="fa778-112">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="fa778-113">Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées aux activités de l’utilisateur à l’aide de cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="fa778-113">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement user activities related features.</span></span>

<span data-ttu-id="fa778-114">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="fa778-114">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="fa778-115">Consultez la page [Informations de référence sur les API](api-reference-for-ios.md) pour obtenir des liens vers la documentation de référence pertinente pour ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="fa778-115">See the [API reference](api-reference-for-ios.md) page for links to the reference docs relevant to these scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="fa778-116">Configuration de la Plateforme d’appareils connectés et des notifications</span><span class="sxs-lookup"><span data-stu-id="fa778-116">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="fa778-117">Utilisation de la plateforme</span><span class="sxs-lookup"><span data-stu-id="fa778-117">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="fa778-118">Initialiser un canal des activités de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fa778-118">Initialize a User Activity channel</span></span>

<span data-ttu-id="fa778-119">Pour implémenter les fonctionnalités Activité de l’utilisateur dans votre application, vous devez d’abord initialiser le flux des activités de l’utilisateur en créant un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fa778-119">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a MCDUserActivityChannel.</span></span> <span data-ttu-id="fa778-120">Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).</span><span class="sxs-lookup"><span data-stu-id="fa778-120">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="fa778-121">Pour cette étape, vous devez disposer d’un compte d’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="fa778-121">You will need a signed-in user account for this step.</span></span> <span data-ttu-id="fa778-122">Comme ci-dessus, vous pouvez utiliser une classe de l’exemple de fournisseur d’authentification pour acquérir facilement le ou les MCDUserAccounts.</span><span class="sxs-lookup"><span data-stu-id="fa778-122">As above, you may use a class from the authentication provider sample to easily acquire the MCDUserAccount(s).</span></span> <span data-ttu-id="fa778-123">Vous aurez aussi besoin de votre ID d’application multiplateforme, qui a été récupéré par le biais de l’inscription au tableau de bord du développeur Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa778-123">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="fa778-124">La méthode suivante de l’exemple d’application initialise un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fa778-124">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

<span data-ttu-id="fa778-125">La méthode suivante de l’exemple d’application initialise un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fa778-125">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

```ObjectiveC

    // Get a UserActivity channel, getting the default channel        
    NSLog(@"Creating UserActivityChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserActivityChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserActivityChannel userActivityChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must have an active account to publish activities!");
    self.createActivityStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="fa778-126">À ce stade, vous devez avoir une référence à MCDUserActivityChannel dans le canal.</span><span class="sxs-lookup"><span data-stu-id="fa778-126">At this point, you should have an MCDUserActivityChannel reference in channel.</span></span>

### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="fa778-127">Créer et publier une activité de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fa778-127">Create and publish a User Activity</span></span>

<span data-ttu-id="fa778-128">L’exemple de code suivant montre comment une nouvelle instance de **MCDUserActivity** est créée.</span><span class="sxs-lookup"><span data-stu-id="fa778-128">The following sample code shows how a new **MCDUserActivity** instance is created.</span></span>

```ObjectiveC
- (IBAction)createActivityButton:(id)sender
{
    // Step #2: Create a UserActivity
    [self.channel getOrCreateUserActivityAsync:[[NSUUID UUID] UUIDString]
        completion:^(MCDUserActivity* activity, NSError* error) {
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error creating activity!";
            }
            else if (!activity)
            {
                NSLog(@"No activity created!");
            }
            else
            {
                dispatch_async(dispatch_get_main_queue(), ^{
                    self.activity = activity;

                    // Create an activityId so the app knows so you know how to get back
                    self.activityId.text = activity.activityId;
                    self.createActivityStatusField.text = @"Created by iOSSample";
                    // Create a deep link so the app can get right back to where it was
                    self.activationUri.text = @"roman-app:";
                    self.createActivityStatusField.text = @"Activity created";
                });
            }
        }];
}
```

<span data-ttu-id="fa778-129">Dans la méthode suivante, les données visuelles de **MCDUserActivity** sont définies avant la publication de l’activité.</span><span class="sxs-lookup"><span data-stu-id="fa778-129">In the next method, the visual data of the **MCDUserActivity** is set before the Activity is published.</span></span> <span data-ttu-id="fa778-130">L’URI d’activation détermine l’action qui est effectuée quand l’activité est activée (quand elle est sélectionnée dans la Chronologie, par exemple).</span><span class="sxs-lookup"><span data-stu-id="fa778-130">The activation URI will determine what action is taken when the Activity is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="fa778-131">Le texte d’affichage s’affiche sur d’autres appareils quand ils consultent l’activité (dans la Chronologie Windows, par exemple).</span><span class="sxs-lookup"><span data-stu-id="fa778-131">The display text will be shown on other devices when they view the Activity (in Windows Timeline, for example).</span></span> <span data-ttu-id="fa778-132">L’iconUri est un lien web vers une image d’icône.</span><span class="sxs-lookup"><span data-stu-id="fa778-132">The iconUri is a web link to an icon image.</span></span>


```ObjectiveC
- (IBAction)publishActivityButton:(id)sender
{
    self.createActivityStatusField.text = @"Saving";
    self.activity.activationUri = self.activationUri.text;
    // Set the display text for your activity.
    self.activity.visualElements.displayText = @"Visual Element, like an Adaptive Card";
    self.activity.visualElements.attribution.iconUri = @"https://www.microsoft.com/favicon.ico";

    // ...
```

<span data-ttu-id="fa778-133">Une fois le **MCDUserActivity** rempli avec ces données, l’opération de publication a lieu.</span><span class="sxs-lookup"><span data-stu-id="fa778-133">Once the **MCDUserActivity** is populated with this data, the publish operation takes place.</span></span>

```ObjectiveC
    // ...

    // Publish the Activity
    [self.activity saveAsync:^(NSError* error) {
        dispatch_async(dispatch_get_main_queue(), ^{
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error saving activity";
            }
            else
            {
                self.createActivityStatusField.text = @"Saved successfully!";
                [self.sessionButton setTitle:@"Start Session" forState:normal];
            }
        });
    }];
}

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```
> [!TIP] 
> <span data-ttu-id="fa778-134">Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="fa778-134">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="fa778-135">Pour obtenir une étude complète des différentes façons de personnaliser un UserActivity, consultez les classes **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)** et **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)**.</span><span class="sxs-lookup"><span data-stu-id="fa778-135">For a complete look at the different ways that a UserActivity can be customized, see the **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, and **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span></span> <span data-ttu-id="fa778-136">Consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](/windows/uwp/launch-resume/useractivities-best-practices) pour obtenir des recommandations détaillées sur la façon de concevoir des activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fa778-136">See the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

## <a name="update-an-existing-user-activity"></a><span data-ttu-id="fa778-137">Mettre à jour une activité d’utilisateur existante</span><span class="sxs-lookup"><span data-stu-id="fa778-137">Update an existing User Activity</span></span>

<span data-ttu-id="fa778-138">Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas de nouvel engagement, de page modifiée, etc.), vous pouvez le faire en utilisant un **MCDUserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="fa778-138">If you have an existing activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **MCDUserActivitySession**.</span></span> 

<span data-ttu-id="fa778-139">Une fois que vous avez créé une session, votre application peut apporter les changements souhaités aux propriétés de **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="fa778-139">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="fa778-140">Quand vous avez terminé d’apporter les changements, fermez la session.</span><span class="sxs-lookup"><span data-stu-id="fa778-140">When you're done making changes, close the session.</span></span> 

<span data-ttu-id="fa778-141">La méthode suivante de l’exemple d’application active ou désactive une session.</span><span class="sxs-lookup"><span data-stu-id="fa778-141">The following method from the sample app toggles a session on and off.</span></span>

```ObjectiveC
- (IBAction)manageSessionButton:(id)sender
{

    // Start a new a session for the UserActivity
    if (self.session == nil)
    {
       self.session = [self.activity createSession];
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has started %@", self.session);
            self.session = [self.activity createSession];
            dispatch_async(dispatch_get_main_queue(), ^{ [self.sessionButton setTitle:@"Stop Session" forState:normal]; });
        });
    }
    else
    {
        // Stop the UserActivitySession
        [self.session close];
        self.session = nil;
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has stopped %@", self.session);
            [self.sessionButton setTitle:@"Start Session" forState:normal];
        });
    }
}
```


<span data-ttu-id="fa778-142">Un **MCDUserActivitySession** peut être considéré comme un moyen de créer un **MCDUserActivitySessionHistoryItem** (décrit dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="fa778-142">An **MCDUserActivitySession** can be thought of as a way to create a **MCDUserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="fa778-143">Au lieu de créer un **MCDUserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une session pour chaque page.</span><span class="sxs-lookup"><span data-stu-id="fa778-143">Rather than create a new **MCDUserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="fa778-144">Cela constitue une expérience de lecture d’activité plus intuitive et plus organisée.</span><span class="sxs-lookup"><span data-stu-id="fa778-144">This will make for a more intuitive and organized activity reading experience.</span></span>

## <a name="read-user-activities"></a><span data-ttu-id="fa778-145">Lire des activités de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fa778-145">Read User Activities</span></span>

<span data-ttu-id="fa778-146">Votre application peut lire les activités de l’utilisateur et les présenter à l’utilisateur exactement comme le fait la fonctionnalité Chronologie Windows.</span><span class="sxs-lookup"><span data-stu-id="fa778-146">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="fa778-147">Pour configurer la lecture des activités de l’utilisateur, vous utilisez la même instance de **MCDUserActivityChannel** que précédemment.</span><span class="sxs-lookup"><span data-stu-id="fa778-147">To set up User Activity reading, you use the same **MCDUserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="fa778-148">Cette instance peut exposer des instances de **MCDUserActivitySessionHistoryItem**, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.</span><span class="sxs-lookup"><span data-stu-id="fa778-148">This instance can expose **MCDUserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

```ObjectiveC
- (IBAction)readActivityButton:(id)sender
{

    // Read/sync your UserActivities
    [self.channel getRecentUserActivitiesAsync:(NSInteger)5
        completion:^(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull result, NSError* _Nullable error) {
            dispatch_async(dispatch_get_main_queue(), ^{
                if (error)
                {
                    self.readActivityStatusField.text = @"Error reading activity!";
                }
                else if (result.count == 0)
                {
                    self.readActivityStatusField.text = @"Read completed, no activities returned";
                }
                else
                {
                    self.readActivityStatusField.text = @"Read completed!";
                    MCDUserActivitySessionHistoryItem* item = result.firstObject;
                    self.activityList.text = item.userActivity.activityId;
                    self.activityDisplay.text = item.userActivity.visualElements.displayText;
                }
            });
        }];
}
```

<span data-ttu-id="fa778-149">Votre application doit maintenant disposer d’une liste d’éléments **MCDUserActivitySessionHistoryItem**.</span><span class="sxs-lookup"><span data-stu-id="fa778-149">Now your app should have a populated list of **MCDUserActivitySessionHistoryItem** s.</span></span> <span data-ttu-id="fa778-150">Chacun d’entre eux peut fournir le **MCDUserActivity** sous-jacent (consultez **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fa778-150">Each of these can deliver the underlying **MCDUserActivity** (see **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** for details), which you can then display to the user.</span></span>