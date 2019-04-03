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
# <a name="implementing-user-activities-for-android"></a>Implémentation d’activités de l’utilisateur pour Android

Activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application. Ils permettent d’enregistrer un instantané d’une tâche à poursuivre ultérieurement. Le [Windows chronologie](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) fonctionnalité offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représenté sous forme de cartes avec le texte et les graphiques. Pour plus d’informations sur les activités des utilisateurs en général, consultez [continuer les activités des utilisateurs, même sur les appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Pour obtenir des recommandations concernant créer ou mettre à jour des activités, consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.

Avec le Kit de développement Project Rome, votre application Android peut non seulement publier les activités de l’utilisateur pour une utilisation dans les fonctionnalités de Windows telles que la chronologie, mais peut également agir comme un point de terminaison et lire des activités à l’utilisateur comme chronologie sur les appareils Windows. Cela permet aux applications d’inter-périphériques transcendant leurs plateformes et de fournir des expériences qui suivent les utilisateurs plutôt que des dispositifs.  

Consultez le [référence de l’API](api-reference-for-android.md) page pour des liens vers la documentation de référence relatives à ces scénarios.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>À l’aide de la plateforme

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Initialiser un canal de l’activité des utilisateurs

Pour implémenter les fonctionnalités de l’activité des utilisateurs dans votre application, vous devez d’abord initialiser le flux en créant un UserActivityChannel d’activité utilisateur. Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).

Vous devez également votre ID d’application multiplateforme, qui a été récupérée via l’inscription de tableau de bord de développement Microsoft.
Les méthodes suivantes d’initialiser un UserActivityChannel.

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

À ce stade, vous aurez une référence UserActivityChannel mActivityChannel.


### <a name="create-and-publish-a-user-activity"></a>Créer et publier une activité utilisateur

Ensuite, définissez les données d’ID, DisplayText et ActivationURI de ce que sera considéré comme un nouveau **UserActivity**. L’ID doit être une chaîne unique. Le texte s’affichera sur d’autres appareils lorsqu’ils les consultent l’activité (dans Windows chronologie, par exemple), elle devrait donc être une description concise de l’activité. Le ActivationUri détermine quelle action est effectuée lorsque le **UserActivity** est activé (lorsqu’il est sélectionné dans la chronologie, par exemple). Le code suivant renseigne des exemples de données pour ces champs.


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

Ensuite, fournir une méthode qui crée un nouveau **UserActivity** instance.

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
Une fois que vous avez le **UserActivity** de l’instance, le remplir avec les données définies ci-dessus.

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

Enfin, l’activité de publication vers le cloud. 

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
> Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées. Pour une présentation plus détaillée sur les différentes façons qu’un UserActivity peut être personnalisé, consultez le  **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, et **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes. Consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide pour obtenir des recommandations détaillées quant à la conception d’activités des utilisateurs.

### <a name="update-an-existing-user-activity"></a>Mettre à jour d’une activité utilisateur existant

Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas d’un engagement nouvelle page modifiée et ainsi de suite), vous pouvez le faire en utilisant un **UserActivitySession**.

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

Une fois que vous avez créé une session, votre application peut effectuer les modifications souhaitées aux propriétés de la **UserActivity**. Lorsque vous avez terminé d’apporter des modifications, fermez la session. 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

Un **UserActivitySession** peut être considéré comme un moyen de créer un **UserActivitySessionHistoryItem** (présenté dans la section suivante). Au lieu de créer un nouveau **UserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une nouvelle session pour chaque page. Vous serez ainsi pour une activité plus intuitive et organisée expérience de lecture.

### <a name="read-user-activities"></a>Activités de l’utilisateur en lecture

Votre application peut lire les activités des utilisateurs et les présenter à l’utilisateur comme le fait de la fonctionnalité de montage de Windows. Pour configurer la lecture de l’activité des utilisateurs, utilisez le même **UserActivityChannel** instance indiquée précédemment. Cette instance peut exposer **UserActivitySessionHistoryItem** instances, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.

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

Maintenant votre application doit disposer d’une liste de **UserActivitySessionHistoryItem**s. Chacun d'entre eux peut fournir sous-jacent **UserActivity** (consultez **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.
