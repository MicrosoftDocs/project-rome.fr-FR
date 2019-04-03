---
title: Publication et la lecture des activités des utilisateurs (Android)
description: Ce guide montre comment créer, publier et lire des activités des utilisateurs dans votre application Android basée sur Windows.
ms.topic: article
keywords: Microsoft, windows, project rome, d’activités des utilisateurs, d’android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: 67f793341a108853d5b36e062fd04f441efff473
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909611"
---
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="c3f6e-104">Implémentation d’activités de l’utilisateur pour Android</span><span class="sxs-lookup"><span data-stu-id="c3f6e-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="c3f6e-105">Activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="c3f6e-106">Ils permettent d’enregistrer un instantané d’une tâche à poursuivre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="c3f6e-107">Le [Windows chronologie](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) fonctionnalité offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représenté sous forme de cartes avec le texte et les graphiques.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="c3f6e-108">Pour plus d’informations sur les activités des utilisateurs en général, consultez [continuer les activités des utilisateurs, même sur les appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="c3f6e-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="c3f6e-109">Pour obtenir des recommandations concernant créer ou mettre à jour des activités, consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="c3f6e-110">Avec le Kit de développement Project Rome, votre application Android peut non seulement publier les activités de l’utilisateur pour une utilisation dans les fonctionnalités de Windows telles que la chronologie, mais peut également agir comme un point de terminaison et lire des activités à l’utilisateur comme chronologie sur les appareils Windows.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="c3f6e-111">Cela permet aux applications d’inter-périphériques transcendant leurs plateformes et de fournir des expériences qui suivent les utilisateurs plutôt que des dispositifs.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="c3f6e-112">Consultez le [référence de l’API](api-reference-for-android.md) page pour des liens vers la documentation de référence relatives à ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="c3f6e-113">Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="c3f6e-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="c3f6e-114">À l’aide de la plateforme</span><span class="sxs-lookup"><span data-stu-id="c3f6e-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="c3f6e-115">Initialiser un canal de l’activité des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c3f6e-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="c3f6e-116">Pour implémenter les fonctionnalités de l’activité des utilisateurs dans votre application, vous devez d’abord initialiser le flux en créant un UserActivityChannel d’activité utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="c3f6e-117">Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).</span><span class="sxs-lookup"><span data-stu-id="c3f6e-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="c3f6e-118">Vous devez également votre ID d’application multiplateforme, qui a été récupérée via l’inscription de tableau de bord de développement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="c3f6e-119">Les méthodes suivantes d’initialiser un UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-119">The following methods initialize a UserActivityChannel.</span></span>

```Java
private UserActivityChannel mActivityChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserActivityFeed.
 */
public void initializeUserActivityFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserActivityChannel.getSyncScope(), UserNotificationChannel.getSyncScope() };

    // Get a reference to the UserDataFeed. This method is defined below
    mUserDataFeed = getUserDataFeed(scopes, new EventListener<UserDataFeed, Void>() {
        @Override
        public void onEvent(UserDataFeed userDataFeed, Void aVoid) {
            if (userDataFeed.getSyncStatus() == UserDataSyncStatus.SYNCHRONIZED) {
                // log synchronized.
            } else {
                // log synchronization not completed.
            }
        }
    });

    // this method is defined below
    mActivityChannel = getUserActivityChannel();
}

// instantiate the UserDataFeed
private UserDataFeed getUserDataFeed(SyncScope[] scopes, EventListener<UserDataFeed, Void> listener) {
    UserAccount[] accounts = AccountProviderBroker.getSignInHelper().getUserAccounts();
    if (accounts.length <= 0) {
        // notify the user that sign-in is required
        return null;
    }

    // use the initialized Platform instance, along with the cross-device app ID.
    UserDataFeed feed = UserDataFeed.getForAccount(accounts[0], PlatformBroker.getPlatform(), Secrets.APP_HOST_NAME);
    feed.addSyncStatusChangedListener(listener);
    feed.addSyncScopes(scopes);
    // sync data with the server
    feed.startSync();
    return feed;
}

// use the UserDataFeed reference to create a UserActivityChannel
@Nullable
private UserActivityChannel getUserActivityChannel() {
    UserActivityChannel channel = null;
    try {
        // create a UserActivityChannel for the signed in account
        channel = new UserActivityChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```

<span data-ttu-id="c3f6e-120">À ce stade, vous aurez une référence UserActivityChannel mActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="c3f6e-121">Créer et publier une activité utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3f6e-121">Create and publish a User Activity</span></span>

<span data-ttu-id="c3f6e-122">Ensuite, définissez les données d’ID, DisplayText et ActivationURI de ce que sera considéré comme un nouveau **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="c3f6e-123">L’ID doit être une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-123">The ID should be a unique String.</span></span> <span data-ttu-id="c3f6e-124">Le texte s’affichera sur d’autres appareils lorsqu’ils les consultent l’activité (dans Windows chronologie, par exemple), elle devrait donc être une description concise de l’activité.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="c3f6e-125">Le ActivationUri détermine quelle action est effectuée lorsque le **UserActivity** est activé (lorsqu’il est sélectionné dans la chronologie, par exemple).</span><span class="sxs-lookup"><span data-stu-id="c3f6e-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="c3f6e-126">Le code suivant renseigne des exemples de données pour ces champs.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-126">The following code fills in sample data for these fields.</span></span>


```Java
private UserActivity mActivity;
private String mActivityId;
private String mDisplayText;
private String mActivationUri;

// ...

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```

<span data-ttu-id="c3f6e-127">Ensuite, fournir une méthode qui crée un nouveau **UserActivity** instance.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

```Java
// Create the UserActivity (with unique ID) using a custom method. 
mActivity = createUserActivity(mActivityChannel, mActivityId);

// ...

// Custom method for creating a new UserActivity
@Nullable
private UserActivity createUserActivity(UserActivityChannel channel, String activityId)
{
    UserActivity activity = null;
    AsyncOperation<UserActivity> activityOperation = channel.getOrCreateUserActivityAsync(activityId);
    try {
        activity = activityOperation.get();
        Log.d("UserActivityFragment","Created user activity successfully");
    } catch (Exception e) {
        e.printStackTrace();
        Log.d("UserActivityFragment","Created user activity successfully");
    }
    return activity;
}
```
<span data-ttu-id="c3f6e-128">Une fois que vous avez le **UserActivity** de l’instance, le remplir avec les données définies ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="c3f6e-129">Enfin, l’activité de publication vers le cloud.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-129">Finally, publish the Activity to the cloud.</span></span> 

```Java
// This code saves and publishes the activity
AsyncOperation<Void> operation = mActivity.saveAsync();
operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<Void, Throwable>() {
    @Override
    public void accept(Void aVoid, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to save");
        } else {
            Log.d("UserActivityFragment", "User activity saved");
        }
    }
});
```

> [!TIP] 
> <span data-ttu-id="c3f6e-130">Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="c3f6e-131">Pour une présentation plus détaillée sur les différentes façons qu’un UserActivity peut être personnalisé, consultez le  **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, et **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="c3f6e-132">Consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide pour obtenir des recommandations détaillées quant à la conception d’activités des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-132">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="c3f6e-133">Mettre à jour d’une activité utilisateur existant</span><span class="sxs-lookup"><span data-stu-id="c3f6e-133">Update an existing User Activity</span></span>

<span data-ttu-id="c3f6e-134">Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas d’un engagement nouvelle page modifiée et ainsi de suite), vous pouvez le faire en utilisant un **UserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

```Java
private UserActivitySession mActivitySession;

// ...

if (mActivity != null)
{
    // create a session from a previous UserActivity instance.
    mActivitySession = mActivity.createSession();
    Log.d("UserActivityFragment", "Starting");
}
```

<span data-ttu-id="c3f6e-135">Une fois que vous avez créé une session, votre application peut effectuer les modifications souhaitées aux propriétés de la **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="c3f6e-136">Lorsque vous avez terminé d’apporter des modifications, fermez la session.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="c3f6e-137">Un **UserActivitySession** peut être considéré comme un moyen de créer un **UserActivitySessionHistoryItem** (présenté dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="c3f6e-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="c3f6e-138">Au lieu de créer un nouveau **UserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une nouvelle session pour chaque page.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="c3f6e-139">Vous serez ainsi pour une activité plus intuitive et organisée expérience de lecture.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="c3f6e-140">Activités de l’utilisateur en lecture</span><span class="sxs-lookup"><span data-stu-id="c3f6e-140">Read User Activities</span></span>

<span data-ttu-id="c3f6e-141">Votre application peut lire les activités des utilisateurs et les présenter à l’utilisateur comme le fait de la fonctionnalité de montage de Windows.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="c3f6e-142">Pour configurer la lecture de l’activité des utilisateurs, utilisez le même **UserActivityChannel** instance indiquée précédemment.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="c3f6e-143">Cette instance peut exposer **UserActivitySessionHistoryItem** instances, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

```Java
private ArrayList<UserActivitySessionHistoryItem> mHistoryItems; 

// ...

mHistoryItems.clear();

Log.d("UserActivityFragment", "Read");
//Async method to read activities. Last (most recent) 5 activities will be returned
AsyncOperation<UserActivitySessionHistoryItem[]> operation = mActivityChannel.getRecentUserActivitiesAsync(5);

operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<UserActivitySessionHistoryItem[], Throwable>() {
    @Override
    public void accept(UserActivitySessionHistoryItem[] result, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to read user activity!" + throwable.getMessage() + " " + throwable.getStackTrace());
        } else {
            // get the returned UserActivitySessionHistoryItems
            for (UserActivitySessionHistoryItem item : result)
            {
                mHistoryItems.add(item);
            }
        }
    }
});
```

<span data-ttu-id="c3f6e-144">Maintenant votre application doit disposer d’une liste de **UserActivitySessionHistoryItem**s.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-144">Now your app should have a populated list of **UserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="c3f6e-145">Chacun d'entre eux peut fournir sous-jacent **UserActivity** (consultez **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3f6e-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>
