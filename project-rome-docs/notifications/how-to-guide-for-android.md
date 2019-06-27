---
title: Intégration d’applications Android à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801201"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>Guides pratique : Intégration à la fonctionnalité Notifications Graph (Android)

Les notifications Graph permettent à votre application d’envoyer et de gérer des notifications ciblant l’utilisateur sur plusieurs appareils. 

Avec le SDK côté client Projet Rome sur Android, votre application Android peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’applications ciblant un utilisateur connecté. Le SDK permet au client d’application de recevoir les nouvelles charges utiles de notification entrante, gérer l’état des notifications existantes et récupérer l’historique des notifications. Pour plus d’informations sur la fonctionnalité Notifications et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).

Toutes les fonctionnalités du SDK Projet Rome, notamment Notifications Graph, reposent sur une plateforme sous-jacente appelée « Plateforme d’appareils connectés ». Ce guide est conçu de façon à vous guider tout au long des étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés et à expliquer comment utiliser les API du SDK afin d’implémenter des fonctionnalités spécifiques aux notifications Graph.

Consultez la page [Informations de référence sur les API](api-reference-for-android.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application Android du projet Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de notification Graph
Le SDK Projet Rome permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore. Ils sont tous stockés et synchronisés dans **UserDataFeed**. **UserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph. Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un UserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **UserNotificationChannel**. Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme). 

Les méthodes suivantes initialisent un **UserNotificationChannel**.

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
À ce stade, vous devez avoir une référence à **UserNotificationChannel** dans `mNotificationChannel`.

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Créer un UserNotificationReader pour recevoir des UserNotification entrants et accéder à l’historique des UserNotification
Comme nous l’avons montré précédemment, la notification Google Cloud Messaging initiale arrivant sur le client d’application contient uniquement un passage de relais, et vous devez transmettre cette charge utile en passage de relais à la Plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le serveur d’appareils connectés, lequel contient tous les UserNotifications publiés par votre serveur d’applications. Cette opération extrait la charge utile de notification complète publiée par votre serveur d’applications correspondant à ce passage de relais (et dans le cas où des notifications précédentes ont été publiées mais pas reçues sur ce client d’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront également extraites). Avec ces synchronisations en temps réel effectuées en permanence par le SDK, le client d’application est en mesure d’accéder à un cache local de ce flux de données UserNotification de l’utilisateur connecté. Dans ce cas, un UserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments UserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).  
### <a name="receiving-usernotifications"></a>Réception de UserNotifications
Vous devez d’abord instancier un UserNotificationReader et obtenir tous les UserNotifications existants dans le lecteur si la consommation de ces informations pour l’expérience que vous essayez d’activer vous intéresse. Étant donné que ce point de terminaison d’appareil particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé sur votre application, nous pouvons toujours présumer sans risque que le serveur d’applications a déjà publié des notifications à cet utilisateur connecté. 
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
Maintenant, ajoutez un détecteur d’événements qui se déclenche quand la Plateforme d’appareils connectés effectue une synchronisation et qu’elle doit vous informer de nouveaux changements. Dans le cas de la fonctionnalité Notifications Graph, les nouveaux changements peuvent être de nouveaux UserNotifications entrants publiés par votre serveur d’applications, ou des mises à jour, suppressions et expirations d’éléments UserNotifcation qui se sont produits à partir du serveur ou à partir d’autres points de terminaison inscrits auxquels le même utilisateur s’est connecté. 
> [!TIP] 
> Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement un message de données de Google Cloud Messaging pour construire une notification visuelle dans la barre de notification au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela. 
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
## <a name="update-the-state-of-an-existing-usernotification"></a>Mettre à jour l’état d’un UserNotification existant
Dans la section précédente, nous avons mentionné qu’un changement de UserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un UserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu). Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier. Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de UserNotification pour commencer. Vous pouvez choisir le moment où mettre à jour l’état de vos UserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez. Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés. L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante. Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état du UserNotification correspondant afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur. Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil. Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur. 

> [!TIP] 
> La classe UserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour. Par exemple, vous pouvez marquer UserActionState comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel. Alternativement ou simultanément, vous pouvez marquer ReadState comme Read (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application. L’extrait de code ci-dessous montre comment marquer le UserNotificationUserActionState d’une notification comme Dismissed (Masqué).

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
