---
title: Publication et la lecture des activités de l’utilisateur (iOS)
description: Ce guide montre comment créer, publier et lire des activités des utilisateurs dans votre application iOS basée sur Windows.
ms.topic: article
keywords: Microsoft, windows, project rome, d’activités des utilisateurs, d’ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909431"
---
# <a name="implementing-user-activities-for-ios"></a><span data-ttu-id="10bcc-104">Implémentation d’activités des utilisateurs pour iOS</span><span class="sxs-lookup"><span data-stu-id="10bcc-104">Implementing User Activities for iOS</span></span>

<span data-ttu-id="10bcc-105">Activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application.</span><span class="sxs-lookup"><span data-stu-id="10bcc-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="10bcc-106">Ils permettent d’enregistrer un instantané d’une tâche en cours de se poursuivre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="10bcc-106">They make it possible to save a snapshot of a current task to be continued at a later time.</span></span> <span data-ttu-id="10bcc-107">Le [Windows chronologie](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) fonctionnalité offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représenté sous forme de cartes avec le texte et les graphiques.</span><span class="sxs-lookup"><span data-stu-id="10bcc-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="10bcc-108">Pour plus d’informations sur les activités des utilisateurs en général, consultez [continuer les activités des utilisateurs, même sur les appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="10bcc-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="10bcc-109">Pour obtenir des recommandations concernant créer ou mettre à jour des activités, consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span><span class="sxs-lookup"><span data-stu-id="10bcc-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="10bcc-110">Avec le Kit de développement Project Rome, votre application iOS peut publier pas uniquement les activités de l’utilisateur pour une utilisation dans les fonctionnalités de Windows telles que la chronologie, mais il peut également agir comme un point de terminaison et lire des activités à l’utilisateur comme le fait de chronologie.</span><span class="sxs-lookup"><span data-stu-id="10bcc-110">With the Project Rome SDK, your iOS app can not only publish User Activities for use in Windows features such as Timeline, but it can also act as an endpoint and read Activities back to the user just as Timeline does.</span></span> <span data-ttu-id="10bcc-111">Cela permet aux applications d’inter-périphériques transcender complètement les leurs plateformes et des expériences présentes qui suivent les utilisateurs plutôt que des appareils.</span><span class="sxs-lookup"><span data-stu-id="10bcc-111">This allows cross-device apps to completely transcend their platforms and present experiences that follow users rather than devices.</span></span>

<span data-ttu-id="10bcc-112">Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="10bcc-112">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="10bcc-113">Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter des fonctionnalités connexes d’activités utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10bcc-113">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement user activities related features.</span></span>

<span data-ttu-id="10bcc-114">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="10bcc-114">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="10bcc-115">Consultez le [référence de l’API](api-reference-for-ios.md) page pour des liens vers la documentation de référence relatives à ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="10bcc-115">See the [API reference](api-reference-for-ios.md) page for links to the reference docs relevant to these scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="10bcc-116">Configuration de la plateforme de périphériques connectés et les Notifications</span><span class="sxs-lookup"><span data-stu-id="10bcc-116">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="10bcc-117">À l’aide de la plateforme</span><span class="sxs-lookup"><span data-stu-id="10bcc-117">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="10bcc-118">Initialiser un canal de l’activité des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="10bcc-118">Initialize a User Activity channel</span></span>

<span data-ttu-id="10bcc-119">Pour implémenter les fonctionnalités de l’activité des utilisateurs dans votre application, vous devez d’abord initialiser le flux en créant un MCDUserActivityChannel d’activité utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10bcc-119">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a MCDUserActivityChannel.</span></span> <span data-ttu-id="10bcc-120">Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).</span><span class="sxs-lookup"><span data-stu-id="10bcc-120">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="10bcc-121">Vous devez un compte d’utilisateur connecté pour cette étape.</span><span class="sxs-lookup"><span data-stu-id="10bcc-121">You will need a signed-in user account for this step.</span></span> <span data-ttu-id="10bcc-122">Comme ci-dessus, vous pouvez utiliser une classe à partir de l’exemple de fournisseur d’authentification pour acquérir facilement le MCDUserAccount(s).</span><span class="sxs-lookup"><span data-stu-id="10bcc-122">As above, you may use a class from the authentication provider sample to easily acquire the MCDUserAccount(s).</span></span> <span data-ttu-id="10bcc-123">Vous devez également votre ID d’application multiplateforme, qui a été récupérée via l’inscription de tableau de bord de développement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10bcc-123">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="10bcc-124">La méthode suivante à partir de l’exemple d’application initialise un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="10bcc-124">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

<span data-ttu-id="10bcc-125">La méthode suivante à partir de l’exemple d’application initialise un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="10bcc-125">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

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
<span data-ttu-id="10bcc-126">À ce stade, vous devez avoir une référence MCDUserActivityChannel dans le canal.</span><span class="sxs-lookup"><span data-stu-id="10bcc-126">At this point, you should have an MCDUserActivityChannel reference in channel.</span></span>

### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="10bcc-127">Créer et publier une activité utilisateur</span><span class="sxs-lookup"><span data-stu-id="10bcc-127">Create and publish a User Activity</span></span>

<span data-ttu-id="10bcc-128">L’exemple suivant de code montre comment un nouveau **MCDUserActivity** instance est créée.</span><span class="sxs-lookup"><span data-stu-id="10bcc-128">The following sample code shows how a new **MCDUserActivity** instance is created.</span></span>

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

<span data-ttu-id="10bcc-129">Dans la méthode suivante, les données visuelles de la **MCDUserActivity** est définie avant la publication de l’activité.</span><span class="sxs-lookup"><span data-stu-id="10bcc-129">In the next method, the visual data of the **MCDUserActivity** is set before the Activity is published.</span></span> <span data-ttu-id="10bcc-130">L’URI de l’activation déterminent quelle action est effectuée lorsque l’activité est activée (lorsqu’il est sélectionné dans la chronologie, par exemple).</span><span class="sxs-lookup"><span data-stu-id="10bcc-130">The activation URI will determine what action is taken when the Activity is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="10bcc-131">Le texte d’affichage s’affichera sur d’autres appareils lorsqu’ils les consultent l’activité (dans la chronologie de Windows, par exemple).</span><span class="sxs-lookup"><span data-stu-id="10bcc-131">The display text will be shown on other devices when they view the Activity (in Windows Timeline, for example).</span></span> <span data-ttu-id="10bcc-132">L’iconUri est un lien web vers une image d’icône.</span><span class="sxs-lookup"><span data-stu-id="10bcc-132">The iconUri is a web link to an icon image.</span></span>


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

<span data-ttu-id="10bcc-133">Une fois le **MCDUserActivity** est rempli avec ces données, l’opération de publication a lieu.</span><span class="sxs-lookup"><span data-stu-id="10bcc-133">Once the **MCDUserActivity** is populated with this data, the publish operation takes place.</span></span>

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
> <span data-ttu-id="10bcc-134">Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="10bcc-134">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="10bcc-135">Pour une présentation plus détaillée sur les différentes façons qu’un UserActivity peut être personnalisé, consultez le  **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, et **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span><span class="sxs-lookup"><span data-stu-id="10bcc-135">For a complete look at the different ways that a UserActivity can be customized, see the **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, and **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span></span> <span data-ttu-id="10bcc-136">Consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide pour obtenir des recommandations détaillées quant à la conception d’activités des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="10bcc-136">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

## <a name="update-an-existing-user-activity"></a><span data-ttu-id="10bcc-137">Mettre à jour d’une activité utilisateur existant</span><span class="sxs-lookup"><span data-stu-id="10bcc-137">Update an existing User Activity</span></span>

<span data-ttu-id="10bcc-138">Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas d’un engagement nouvelle page modifiée et ainsi de suite), vous pouvez le faire en utilisant un **MCDUserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="10bcc-138">If you have an existing activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **MCDUserActivitySession**.</span></span> 

<span data-ttu-id="10bcc-139">Une fois que vous avez créé une session, votre application peut effectuer les modifications souhaitées aux propriétés de la **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="10bcc-139">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="10bcc-140">Lorsque vous avez terminé d’apporter des modifications, fermez la session.</span><span class="sxs-lookup"><span data-stu-id="10bcc-140">When you're done making changes, close the session.</span></span> 

<span data-ttu-id="10bcc-141">La méthode suivante à partir de l’exemple d’application active ou désactive une session sur Active et inactive.</span><span class="sxs-lookup"><span data-stu-id="10bcc-141">The following method from the sample app toggles a session on and off.</span></span>

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


<span data-ttu-id="10bcc-142">Un **MCDUserActivitySession** peut être considéré comme un moyen de créer un **MCDUserActivitySessionHistoryItem** (présenté dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="10bcc-142">An **MCDUserActivitySession** can be thought of as a way to create a **MCDUserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="10bcc-143">Au lieu de créer un nouveau **MCDUserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une nouvelle session pour chaque page.</span><span class="sxs-lookup"><span data-stu-id="10bcc-143">Rather than create a new **MCDUserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="10bcc-144">Vous serez ainsi pour une activité plus intuitive et organisée expérience de lecture.</span><span class="sxs-lookup"><span data-stu-id="10bcc-144">This will make for a more intuitive and organized activity reading experience.</span></span>

## <a name="read-user-activities"></a><span data-ttu-id="10bcc-145">Activités de l’utilisateur en lecture</span><span class="sxs-lookup"><span data-stu-id="10bcc-145">Read User Activities</span></span>

<span data-ttu-id="10bcc-146">Votre application peut lire les activités des utilisateurs et les présenter à l’utilisateur comme le fait de la fonctionnalité de montage de Windows.</span><span class="sxs-lookup"><span data-stu-id="10bcc-146">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="10bcc-147">Pour configurer la lecture de l’activité des utilisateurs, vous utilisez le même **MCDUserActivityChannel** instance indiquée précédemment.</span><span class="sxs-lookup"><span data-stu-id="10bcc-147">To set up User Activity reading, you use the same **MCDUserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="10bcc-148">Cette instance peut exposer **MCDUserActivitySessionHistoryItem** instances, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.</span><span class="sxs-lookup"><span data-stu-id="10bcc-148">This instance can expose **MCDUserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="10bcc-149">Maintenant votre application doit disposer d’une liste de **MCDUserActivitySessionHistoryItem**s.</span><span class="sxs-lookup"><span data-stu-id="10bcc-149">Now your app should have a populated list of **MCDUserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="10bcc-150">Chacun d'entre eux peut fournir sous-jacent **MCDUserActivity** (consultez **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10bcc-150">Each of these can deliver the underlying **MCDUserActivity** (see **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** for details), which you can then display to the user.</span></span>
