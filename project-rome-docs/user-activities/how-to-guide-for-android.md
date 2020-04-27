---
title: Publication et lecture d’activités de l’utilisateur (Android)
description: Ce guide montre comment créer, publier et lire des activités de l’utilisateur Windows dans votre application Android.
ms.topic: article
keywords: microsoft, windows, projet rome, activités de l’utilisateur, android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: 67f793341a108853d5b36e062fd04f441efff473
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801531"
---
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="fd888-104">Implémentation d’activités de l’utilisateur pour Android</span><span class="sxs-lookup"><span data-stu-id="fd888-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="fd888-105">Les activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application.</span><span class="sxs-lookup"><span data-stu-id="fd888-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="fd888-106">Elles permettent d’enregistrer une capture instantanée d’une tâche à poursuivre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="fd888-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="fd888-107">La fonctionnalité [Chronologie Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représentées sous forme de cartes comportant du texte et des graphiques.</span><span class="sxs-lookup"><span data-stu-id="fd888-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="fd888-108">Pour plus d’informations sur les activités de l’utilisateur en général, consultez [Poursuivre l’activité utilisateur, même sur différents appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="fd888-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="fd888-109">Pour savoir quand créer ou mettre à jour des activités, consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices).</span><span class="sxs-lookup"><span data-stu-id="fd888-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="fd888-110">Avec le SDK Projet Rome, votre application Android peut non seulement publier des activités de l’utilisateur pour les utiliser dans des fonctionnalités Windows telles que la Chronologie, mais aussi faire office de point de terminaison et relire des activités à l’utilisateur comme le fait la Chronologie sur les appareils Windows.</span><span class="sxs-lookup"><span data-stu-id="fd888-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="fd888-111">Cela permet aux applications inter-appareils de transcender leurs plateformes et de fournir des expériences qui suivent les utilisateurs plutôt que les appareils.</span><span class="sxs-lookup"><span data-stu-id="fd888-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="fd888-112">Consultez la page [Informations de référence sur les API](api-reference-for-android.md) pour obtenir des liens vers la documentation de référence pertinente pour ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="fd888-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="fd888-113">Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="fd888-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="fd888-114">Utilisation de la plateforme</span><span class="sxs-lookup"><span data-stu-id="fd888-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="fd888-115">Initialiser un canal des activités de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fd888-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="fd888-116">Pour implémenter les fonctionnalités Activité de l’utilisateur dans votre application, vous devez d’abord initialiser le flux des activités de l’utilisateur en créant un UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fd888-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="fd888-117">Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).</span><span class="sxs-lookup"><span data-stu-id="fd888-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="fd888-118">Vous aurez aussi besoin de votre ID d’application multiplateforme, qui a été récupéré par le biais de l’inscription au tableau de bord du développeur Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fd888-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="fd888-119">Les méthodes suivantes initialisent un UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fd888-119">The following methods initialize a UserActivityChannel.</span></span>

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

<span data-ttu-id="fd888-120">À ce stade, vous devez avoir une référence à UserActivityChannel dans mActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="fd888-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="fd888-121">Créer et publier une activité de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fd888-121">Create and publish a User Activity</span></span>

<span data-ttu-id="fd888-122">Ensuite, définissez les données d’ID, de DisplayText et d’ActivationURI de ce qui sera un nouveau **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="fd888-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="fd888-123">L’ID doit être une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="fd888-123">The ID should be a unique String.</span></span> <span data-ttu-id="fd888-124">Le DisplayText s’affiche sur d’autres appareils quand ils consultent l’activité (dans la Chronologie Windows, par exemple). Ce doit donc être une description concise de l’activité.</span><span class="sxs-lookup"><span data-stu-id="fd888-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="fd888-125">L’ActivationUri détermine l’action qui est effectuée quand **UserActivity** est activé (quand il est sélectionné dans la Chronologie, par exemple).</span><span class="sxs-lookup"><span data-stu-id="fd888-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="fd888-126">Le code suivant renseigne des exemples de données pour ces champs.</span><span class="sxs-lookup"><span data-stu-id="fd888-126">The following code fills in sample data for these fields.</span></span>


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

<span data-ttu-id="fd888-127">Ensuite, fournissez une méthode qui crée une instance de **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="fd888-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

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
<span data-ttu-id="fd888-128">Une fois que vous avez l’instance de **UserActivity**, remplissez-la avec les données définies ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="fd888-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="fd888-129">Enfin, publiez l’activité dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="fd888-129">Finally, publish the Activity to the cloud.</span></span> 

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
> <span data-ttu-id="fd888-130">Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="fd888-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="fd888-131">Pour obtenir une étude complète des différentes façons de personnaliser un UserActivity, consultez les classes **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)** , **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)** et **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** .</span><span class="sxs-lookup"><span data-stu-id="fd888-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="fd888-132">Consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) pour obtenir des recommandations détaillées sur la façon de concevoir des activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fd888-132">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="fd888-133">Mettre à jour une activité d’utilisateur existante</span><span class="sxs-lookup"><span data-stu-id="fd888-133">Update an existing User Activity</span></span>

<span data-ttu-id="fd888-134">Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas de nouvel engagement, de page modifiée, etc.), vous pouvez le faire en utilisant un **UserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="fd888-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

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

<span data-ttu-id="fd888-135">Une fois que vous avez créé une session, votre application peut apporter les changements souhaités aux propriétés de **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="fd888-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="fd888-136">Quand vous avez terminé d’apporter les changements, fermez la session.</span><span class="sxs-lookup"><span data-stu-id="fd888-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="fd888-137">Un **UserActivitySession** peut être considéré comme un moyen de créer un **UserActivitySessionHistoryItem** (décrit dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="fd888-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="fd888-138">Au lieu de créer un **UserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une session pour chaque page.</span><span class="sxs-lookup"><span data-stu-id="fd888-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="fd888-139">Cela constitue une expérience de lecture d’activité plus intuitive et plus organisée.</span><span class="sxs-lookup"><span data-stu-id="fd888-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="fd888-140">Lire des activités de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="fd888-140">Read User Activities</span></span>

<span data-ttu-id="fd888-141">Votre application peut lire les activités de l’utilisateur et les présenter à l’utilisateur exactement comme le fait la fonctionnalité Chronologie Windows.</span><span class="sxs-lookup"><span data-stu-id="fd888-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="fd888-142">Pour configurer la lecture des activités de l’utilisateur, utilisez la même instance de **UserActivityChannel** que précédemment.</span><span class="sxs-lookup"><span data-stu-id="fd888-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="fd888-143">Cette instance peut exposer des instances de **UserActivitySessionHistoryItem**, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.</span><span class="sxs-lookup"><span data-stu-id="fd888-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="fd888-144">Votre application doit maintenant disposer d’une liste d’éléments **UserActivitySessionHistoryItem**.</span><span class="sxs-lookup"><span data-stu-id="fd888-144">Now your app should have a populated list of **UserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="fd888-145">Chacun d’entre eux peut fournir le **UserActivity** sous-jacent (consultez **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fd888-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>
