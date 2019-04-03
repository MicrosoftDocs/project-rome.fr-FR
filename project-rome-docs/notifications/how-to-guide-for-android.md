---
title: L’intégration d’applications Android avec les Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907911"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>Guide pratique : L’intégration avec les Notifications de graphique (Android)

Notifications de graphique activer votre application envoyer et gérer les notifications de ciblage d’utilisateur sur plusieurs appareils. 

Avec le SDK côté client de Project Rome sur Android, votre application Android peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur connecté. Le Kit de développement permet au client de l’application recevoir les nouvelles charges utiles de notification entrant, gérer l’état des notifications existantes et récupérer l’historique de la notification. Pour plus d’informations sur les Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)

Toutes les fonctionnalités dans le SDK de Rome projet includng graphique Notifications et bien plus encore, sont appuient sur une plateforme sous-jacente, appelée la plateforme d’appareils connectés. Ce guide est conçu pour vous guider à travers les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés et d’expliquer comment utiliser des API dans le Kit de développement pour implémenter des Notifications de graphique-fonctionnalités spécifiques.

Consultez le [référence de l’API](api-reference-for-android.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application Android de Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de Notification de graphique
Le Kit de développement logiciel Project Rome permet à votre application pour vous abonner à différents canaux afin de recevoir et gérer les différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore. Il s’agit tout stockée et synchronisé dans **UserDataFeed**. **UserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique. Pour intégrer avec Notification de graphique et recevoir des UserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **UserNotificationChannel**. Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme). 

Les méthodes suivantes d’initialiser un **UserNotificationChannel**.

```Java
private UserNotificationChannel mNotificationChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserNotificationFeed.
 */
public void initializeUserNotificationFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserNotificationChannel.getSyncScope() };

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
    mNotificationChannel = getUserNotificationChannel();
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
private UserNotificationChannel getUserNotificationChannel() {
    UserNotificationChannel channel = null;
    try {
        // create a UserNotificationChannel for the signed in account
        channel = new UserNotificationChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```
À ce stade, vous devez avoir un **UserNotificationChannel** référencer dans `mNotificationChannel`.

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Créer un UserNotificationReader pour recevoir des UserNotifications entrantes et accéder à l’historique UserNotification
Comme nous vous avons montré précédemment, la notification initiale Google Cloud Messaging arrivant sur l’application client contient uniquement un drainage de l’épaule, et vous devez transmettre cette charge utile tap d’épaule à la plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le Appareil serveur relié, qui contient tous les UserNotifications publiées par le serveur de votre application. Cela abaisse la charge utile de notification complète publiée par votre serveur d’application correspondant à cette tap épaule (et dans le cas si les notifications précédentes ont été publiées mais pas reçues sur ce client de l’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront extrait vers le bas également). Avec ces synchronisations en temps réel en permanence effectuées par le Kit de développement, le client de l’application est en mesure d’accéder à un cache local des flux de données UserNotification connecté l’utilisateur. Dans ce cas un UserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection UserNotification complète qui peut être utilisée en tant que modèle de vue de l’historique de notification de l’utilisateur.  
### <a name="receiving-usernotifications"></a>Réception UserNotifications
Vous devez d’abord instancier un UserNotificationReader et obtenir toutes les UserNotifications existantes déjà dans le lecteur si vous vous intéressez lors de la consommation de ces informations pour l’expérience que vous voulez activer. Il est recommandé de toujours supposer que le serveur d’application a déjà publié des notifications à celui-ci connecté utilisateur, étant donné que ce point de terminaison de périphérique particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé votre application. 
```Java
private static UserNotificationReader mReader;
private static final ArrayList<UserNotification> mHistoricalNotifications = new ArrayList<>();
// Instantiate UserNotificationReader
UserNotificationReaderOptions options = new UserNotificationReaderOptions();
mReader = mNotificationChannel.createReaderWithOptions(options);
// Read any previously published UserNotifications that have not expired yet
mReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
    @Override
    public void accept(UserNotification[] userNotifications) throws Throwable {
        synchronized (mHistoricalNotifications) {
            for (UserNotification notification : userNotifications) {
                if (notification.getReadState() == UserNotificationReadState.UNREAD) {
                    mHistoricalNotifications.add(notification);
                }
            }
        }
 
        if (RunnableManager.getHistoryUpdated() != null) {
            activity.runOnUiThread(RunnableManager.getHistoryUpdated());
        }
    }
});

```
Maintenant, ajoutez un écouteur d’événements qui se déclenche quand la plateforme d’appareils connectés se termine une synchronisation et a des modifications apportées à vous en informer. Dans le cas des Notifications de graphique, les nouvelles modifications peut être nouveau UserNotifications entrantes publiées par votre suppressions du serveur ou les mises à jour UserNotifcation, application et délais d’expiration qui se sont produits à partir du serveur ou des autres inscrit les points de terminaison qui a le même utilisateur connecté dans. 
> [!TIP] 
> Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement un message de données de Google Cloud Messaging pour construire une notification visual dans la barre d’état de la notification au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire. 
```Java
mReader.addDataChangedListener(new EventListener<UserNotificationReader, Void>() {
    @Override
    public void onEvent(UserNotificationReader userNotificationReader, Void aVoid) {
        userNotificationReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
        @Override
        public void accept(UserNotification[] userNotifications) throws Throwable {
            boolean updatedNew = false;
            boolean updatedHistorical = false;
            synchronized (sHistoricalNotifications) {
                for (final UserNotification notification : userNotifications) {
                    if (notification.getStatus() == UserNotificationStatus.ACTIVE && notification.getReadState() == UserNotificationReadState.UNREAD) {
                        switch (notification.getUserActionState()) {
                            case NO_INTERACTION:
                                // Brand new notification
                                // Insert business logic to construct a new visual notification in Android notification tray for the user to see
                                // ...
                            case DISMISSED:
                                // Existing notification that is marked as dismissed
                                // An app client receive this type of changes because another app client logged in by the same user has marked the notification as dismissed and the change is fanned-out to everywhere
                                // This state sync across app clients on different devices enable universal dismiss of notifications and other scenarios across multiple devices owned by the same user
                                // Insert business logic to dismiss the corresponding visual notification inside Android system notification tray, to make sure users don’t have to deal with redundant information across devices, and potentially insert this notification in your app’s notification history view
                                // ...
                            default:
                                // Unexpected
                        }
                    } else {
                        // ...
                    }
                }
            }
        }
    });
}
});

```
## <a name="update-the-state-of-an-existing-usernotification"></a>Mettre à jour l’état d’une UserNotification existante
Dans la section précédente, nous avons mentionné que parfois une modification UserNotification reçue via le lecteur peut être une mise à jour de l’état sur une UserNotification existante – si marquée comme dismissed ou marqués comme lus. Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique. Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification UserNotification pour commencer : à partir d’un autre appareil. Vous pouvez choisir le moment pour mettre à jour l’état de votre UserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application que vous activez . Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés. L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante. Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de le correspondante UserNotification afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur. Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action. Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur. 

> [!TIP] 
> Classe de UserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour. Par exemple, vous pouvez marquer UserActionState pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel. Vous pouvez également, ou en même temps vous pouvez marquer état ReadState comme lu ou non lu et en fonction de qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application. Code ci-dessous extrait de code montre comment marquer le UserNotificationUserActionState d’une notification en tant qu’ignoré.

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
