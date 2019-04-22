---
title: L’intégration des applications IOs avec les Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801311"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>Guide pratique : L’intégration avec les Notifications de graphique (iOS)

Notifications de graphique activer votre application envoyer et gérer les notifications de ciblage d’utilisateur sur plusieurs appareils. 

Avec le SDK côté client de Project Rome sur iOS, votre application iOS peut s’inscrire pour recevoir des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur connecté. Le Kit de développement permet au client de l’application recevoir les nouvelles charges utiles de notification entrant, gérer l’état des notifications existantes et récupérer l’historique de la notification. Pour plus d’informations sur les Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)

Toutes les fonctionnalités dans le SDK de Rome projet includng graphique Notifications et bien plus encore, sont appuient sur une plateforme sous-jacente, appelée la plateforme d’appareils connectés. Ce guide est conçu pour vous guider à travers les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés et d’expliquer comment utiliser des API dans le Kit de développement pour implémenter des Notifications de graphique-fonctionnalités spécifiques.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

Consultez le [référence de l’API](api-reference-for-ios/index.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la plateforme de périphériques connectés et les Notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>À l’aide de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de Notification de graphique
Le Kit de développement logiciel Project Rome permet à votre application pour vous abonner à différents canaux afin de recevoir et gérer les différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore. Il s’agit tout stockée et synchronisé dans **MCDUserDataFeed**. **MCDUserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique.
Pour intégrer avec Notification de graphique et recevoir des MCDUserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **MCDUserNotificationChannel**. Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).

Les méthodes suivantes d’initialiser un **MCDUserNotificationChannel**.
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
À ce stade, vous devez avoir un **MCDUserNotificationChannel** référencer dans `channel`.

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>Créer un MCDUserNotificationReader pour recevoir des MCDUserNotifications entrantes et accéder à l’historique MCDUserNotification
Comme nous vous avons montré précédemment, le certificat APNS initial sans assistance message arrivant sur le client d’application uniquement contient un drainage de l’épaule, et vous devez transmettre cette charge utile tap d’épaule à la plateforme d’appareils connectés afin de déclencher le SDK pour effectuer une synchronisation complète avec le périphérique connecté serveur, qui contient tous les MCDUserNotifications publiées par le serveur de votre application. Cela abaisse la charge utile de notification complète publiée par votre serveur d’application correspondant à cette tap épaule (et dans le cas si les notifications précédentes ont été publiées mais pas reçues sur ce client de l’application en raison de la connectivité des appareils ou d’autres problèmes, elles seront extrait vers le bas également). Avec ces synchronisations en temps réel en permanence effectuées par le Kit de développement, le client de l’application est en mesure d’accéder à un cache local des flux de données MCDUserNotification connecté l’utilisateur. Dans ce cas un MCDUserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection MCDUserNotification complète qui peut être utilisée en tant que modèle de vue de la notification de l’utilisateur historique.  
### <a name="receiving-mcdusernotifications"></a>Réception MCDUserNotifications
Vous devez d’abord instancier un MCDUserNotificationReader et obtenir toutes les MCDUserNotifications existantes déjà dans le lecteur si vous vous intéressez lors de la consommation de ces informations pour l’expérience que vous voulez activer. Il est recommandé de toujours supposer que le serveur d’application a déjà publié des notifications à celui-ci connecté utilisateur, étant donné que ce point de terminaison de périphérique particulier n’est peut-être pas le seul ou le premier point de terminaison que l’utilisateur a installé votre application. Ensuite, ajoutez un écouteur d’événements qui se déclenche quand la plateforme d’appareils connectés se termine une synchronisation et a des modifications apportées à vous en informer. Dans le cas des Notifications de graphique, les nouvelles modifications peut être nouveau MCDUserNotifications entrantes publiées par votre suppressions du serveur ou les mises à jour MCDUserNotifcation, application et points de terminaison inscrits de délais d’expiration qui se sont produits à partir du serveur ou des autres que le même utilisateur connecté.

> [!TIP] 
> Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement la notification en mode silencieux APNS pour construire une notification visuelle dans le centre de notification au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification en mode silencieux pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire. 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>Mettre à jour l’état d’une MCDUserNotification existante
Dans la section précédente, nous avons mentionné que parfois une modification MCDUserNotification reçue via le lecteur peut être une mise à jour de l’état sur une MCDUserNotification existante – si marquée comme dismissed ou marqués comme lus. Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique. Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification MCDUserNotification pour commencer : à partir d’un autre appareil. Vous pouvez choisir le moment pour mettre à jour l’état de votre MCDUserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application vous Activer. Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés. L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante. Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de la Notification utilisateur correspondante afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur. Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action. Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur. 

> [!TIP]
> Classe de MCDUserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le MCDUserNotificationReadState ou le MCDUserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour. Par exemple, vous pouvez marquer les États d’action pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel. Vous pouvez également, ou en même temps, vous pouvez marquer lire l’état de lecture ou non lu et selon qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application. 

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
