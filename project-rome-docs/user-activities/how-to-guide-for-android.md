---
title: Publication et lecture d’activités de l’utilisateur (Android)
description: Ce guide montre comment créer, publier et lire des activités de l’utilisateur Windows dans votre application Android.
ms.topic: article
keywords: microsoft, windows, projet rome, activités de l’utilisateur, android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: ab9cd29451ca9af511b2bd5f94e423f1ba01b46e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901667"
---
# <a name="implementing-user-activities-for-android"></a>Implémentation d’activités de l’utilisateur pour Android

Les activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application. Elles permettent d’enregistrer une capture instantanée d’une tâche à poursuivre ultérieurement. La fonctionnalité [Chronologie Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représentées sous forme de cartes comportant du texte et des graphiques. Pour plus d’informations sur les activités de l’utilisateur en général, consultez [Poursuivre l’activité utilisateur, même sur différents appareils](/windows/uwp/launch-resume/useractivities). Pour savoir quand créer ou mettre à jour des activités, consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](/windows/uwp/launch-resume/useractivities-best-practices).

Avec le SDK Projet Rome, votre application Android peut non seulement publier des activités de l’utilisateur pour les utiliser dans des fonctionnalités Windows telles que la Chronologie, mais aussi faire office de point de terminaison et relire des activités à l’utilisateur comme le fait la Chronologie sur les appareils Windows. Cela permet aux applications inter-appareils de transcender leurs plateformes et de fournir des expériences qui suivent les utilisateurs plutôt que les appareils.  

Consultez la page [Informations de référence sur les API](api-reference-for-android.md) pour obtenir des liens vers la documentation de référence pertinente pour ces scénarios.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Utilisation de la plateforme

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Initialiser un canal des activités de l’utilisateur

Pour implémenter les fonctionnalités Activité de l’utilisateur dans votre application, vous devez d’abord initialiser le flux des activités de l’utilisateur en créant un UserActivityChannel. Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).

Vous aurez aussi besoin de votre ID d’application multiplateforme, qui a été récupéré par le biais de l’inscription au tableau de bord du développeur Microsoft.
Les méthodes suivantes initialisent un UserActivityChannel.

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

À ce stade, vous devez avoir une référence à UserActivityChannel dans mActivityChannel.


### <a name="create-and-publish-a-user-activity"></a>Créer et publier une activité de l’utilisateur

Ensuite, définissez les données d’ID, de DisplayText et d’ActivationURI de ce qui sera un nouveau **UserActivity**. L’ID doit être une chaîne unique. Le DisplayText s’affiche sur d’autres appareils quand ils consultent l’activité (dans la Chronologie Windows, par exemple). Ce doit donc être une description concise de l’activité. L’ActivationUri détermine l’action qui est effectuée quand **UserActivity** est activé (quand il est sélectionné dans la Chronologie, par exemple). Le code suivant renseigne des exemples de données pour ces champs.


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

Ensuite, fournissez une méthode qui crée une instance de **UserActivity**.

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
Une fois que vous avez l’instance de **UserActivity**, remplissez-la avec les données définies ci-dessus.

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

Enfin, publiez l’activité dans le cloud. 

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
> Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées. Pour obtenir une étude complète des différentes façons de personnaliser un UserActivity, consultez les classes **[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)** et **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)**. Consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](/windows/uwp/launch-resume/useractivities-best-practices) pour obtenir des recommandations détaillées sur la façon de concevoir des activités de l’utilisateur.

### <a name="update-an-existing-user-activity"></a>Mettre à jour une activité d’utilisateur existante

Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas de nouvel engagement, de page modifiée, etc.), vous pouvez le faire en utilisant un **UserActivitySession**.

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

Une fois que vous avez créé une session, votre application peut apporter les changements souhaités aux propriétés de **UserActivity**. Quand vous avez terminé d’apporter les changements, fermez la session. 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

Un **UserActivitySession** peut être considéré comme un moyen de créer un **UserActivitySessionHistoryItem** (décrit dans la section suivante). Au lieu de créer un **UserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une session pour chaque page. Cela constitue une expérience de lecture d’activité plus intuitive et plus organisée.

### <a name="read-user-activities"></a>Lire des activités de l’utilisateur

Votre application peut lire les activités de l’utilisateur et les présenter à l’utilisateur exactement comme le fait la fonctionnalité Chronologie Windows. Pour configurer la lecture des activités de l’utilisateur, utilisez la même instance de **UserActivityChannel** que précédemment. Cette instance peut exposer des instances de **UserActivitySessionHistoryItem**, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.

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

Votre application doit maintenant disposer d’une liste d’éléments **UserActivitySessionHistoryItem**. Chacun d’entre eux peut fournir le **UserActivity** sous-jacent (consultez **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.