---
title: Intégration d’applications iOS à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801311"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>Guides pratique : Intégration à la fonctionnalité Notifications Graph (iOS)

Les notifications Graph permettent à votre application d’envoyer et de gérer des notifications ciblant l’utilisateur sur plusieurs appareils. 

Avec le SDK côté client Projet Rome sur iOS, votre application iOS peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’applications ciblant un utilisateur connecté. Le SDK permet au client d’application de recevoir les nouvelles charges utiles de notification entrante, gérer l’état des notifications existantes et récupérer l’historique des notifications. Pour plus d’informations sur la fonctionnalité Notifications et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).

Toutes les fonctionnalités du SDK Projet Rome, notamment Notifications Graph, reposent sur une plateforme sous-jacente appelée « Plateforme d’appareils connectés ». Ce guide est conçu de façon à vous guider tout au long des étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés et à expliquer comment utiliser les API du SDK afin d’implémenter des fonctionnalités spécifiques aux notifications Graph.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

Consultez la page [Informations de référence sur les API](api-reference-for-ios/index.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la Plateforme d’appareils connectés et des notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Utilisation de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de notification Graph
Le SDK Projet Rome permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore. Ils sont tous stockés et synchronisés dans **MCDUserDataFeed**. **MCDUserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph.
Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un MCDUserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **MCDUserNotificationChannel**. Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).

Les méthodes suivantes initialisent un **MCDUserNotificationChannel**.
```ObjectiveC
// You must be logged in to use UserNotifications
NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
if (accounts.count > 0)
{
    // Get a UserNotification channel, getting the default channel
    NSLog(@"Creating UserNotificationChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserNotificationChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must log in to receive notifications for the logged in user!");
    self.createNotificationStatusField.text = @"Need to be logged in!";
}
```
À ce stade, vous devez avoir une référence à **MCDUserNotificationChannel** dans `channel`.

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>Créer un MCDUserNotificationReader pour recevoir des MCDUserNotification entrants et accéder à l’historique des MCDUserNotification
Comme nous l’avons montré précédemment, le message silencieux APNS initial arrivant sur le client d’application contient uniquement un passage de relais, et vous devez transmettre cette charge utile en passage de relais à la Plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le serveur d’appareils connectés, lequel contient tous les MCDUserNotifications publiés par votre serveur d’applications. Cette opération extrait la charge utile de notification complète publiée par votre serveur d’applications correspondant à ce passage de relais (et dans le cas où des notifications précédentes ont été publiées mais pas reçues sur ce client d’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront également extraites). Avec ces synchronisations en temps réel effectuées en permanence par le SDK, le client d’application est en mesure d’accéder à un cache local de ce flux de données MCDUserNotification de l’utilisateur connecté. Dans ce cas, un MCDUserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments MCDUserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).  
### <a name="receiving-mcdusernotifications"></a>Réception de MCDUserNotifications
Vous devez d’abord instancier un MCDUserNotificationReader et obtenir tous les MCDUserNotifications existants dans le lecteur si la consommation de ces informations pour l’expérience que vous essayez d’activer vous intéresse. Étant donné que ce point de terminaison d’appareil particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé sur votre application, nous pouvons toujours présumer sans risque que le serveur d’applications a déjà publié des notifications à cet utilisateur connecté. Ajoutez alors un détecteur d’événements qui se déclenche quand la Plateforme d’appareils connectés effectue une synchronisation et qu’elle doit vous informer de nouveaux changements. Dans le cas de la fonctionnalité Notifications Graph, les nouveaux changements peuvent être de nouveaux MCDUserNotifications entrants publiés par votre serveur d’applications, ou des mises à jour, suppressions et expirations d’éléments MCDUserNotifcation qui se sont produits à partir du serveur ou à partir d’autres points de terminaison inscrits auxquels le même utilisateur s’est connecté.

> [!TIP] 
> Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement une notification silencieuse APNS pour construire une notification visuelle dans le centre de notifications au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification silencieuse pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela. 

```ObjectiveC
// Instantiate the reader from a MCDUserNotificationChannel
// Add a data change listener to subscribe to new changes when new notifications or notification updates are received
- (void)setupWithAccount:(MCDUserAccount*)account {
    dispatch_async(dispatch_get_global_queue(QOS_CLASS_DEFAULT, 0), ^{
        @synchronized (self) {
            MCDUserDataFeed* dataFeed = [MCDUserDataFeed userDataFeedForAccount:account platform:_platform activitySourceHost:@"graphnotifications.sample.windows.com"];
            [dataFeed addSyncScopes:@[[MCDUserNotificationChannel syncScope]]];
            self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:dataFeed];
            self.reader = [self.channel createReader];
            
            __weak typeof(self) weakSelf = self;
            _readerRegistrationToken = [self.reader addDataChangedListener:^(__unused MCDUserNotificationReader* source) {
                NSLog(@"ME123 Got a change!");
                if (weakSelf) {
                    [weakSelf forceRead];
                } else {
                    NSLog(@"ME123 WEAKSELF FOR CHANGES IS NULL!!!");
                }
            }];
            
            [self forceRead];
        }
    });
}

// this is your own business logic when the event listener is fired
// In this case, the app reads the existing batch of notifications in the store and handle any new incoming notifications or notification updates after that
- (void)forceRead {
    NSLog(@"ME123 Forced to read!");
    [self.reader readBatchAsyncWithMaxSize:NSUIntegerMax completion:^(NSArray<MCDUserNotification *> * _Nullable notifications, NSError * _Nullable error) {
        if (error) {
            NSLog(@"ME123 Failed to read batch with error %@", error);
        } else {
            [self _handleNotifications:notifications];
            NSLog(@"ME123 Have %ld listeners", self.listenerMap.count);
            for (void (^listener)(void) in self.listenerMap.allValues) {
                NSLog(@"ME123 Calling a listener about an update!");
                listener();
            }
        }
    }];
}

```

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>Mettre à jour l’état d’un MCDUserNotification existant
Dans la section précédente, nous avons mentionné qu’un changement de MCDUserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un MCDUserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu). Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier. Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de MCDUserNotification pour commencer. Vous pouvez choisir le moment où mettre à jour l’état de vos MCDUserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez. Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés. L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante. Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état de la notification utilisateur correspondante afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur. Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil. Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur. 

> [!TIP]
> La classe MCDUserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le MCDUserNotificationReadState ou le MCDUserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour. Par exemple, vous pouvez marquer l’état d’action comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel. Alternativement ou simultanément, vous pouvez marquer l’état de lecture comme Unread (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application. 

```ObjectiveC
- (void)dismissNotification:(MCDUserNotification*)notification {
    @synchronized (self) {
        notification.userActionState = MCDUserNotificationUserActionStateDismissed;
        [notification saveAsync:^(__unused MCDUserNotificationUpdateResult * _Nullable result, __unused NSError * _Nullable err) {
            NSLog(@"ME123 Dismiss notification with result %d error %@", result.succeeded, err);
        }];
    }
}

```
