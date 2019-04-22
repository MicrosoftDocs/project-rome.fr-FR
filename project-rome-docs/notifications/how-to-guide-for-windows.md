---
title: L’intégration d’applications UWP avec des Notifications de graphique
description: Comment effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception pour les notifications publiés à partir de votre serveur d’application.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801301"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>Guide pratique : L’intégration à MS Graph Notifications (Windows UWP)

Avec le SDK côté client graphique Notifications sur Windows, votre application UWP de Windows peut effectuer les étapes d’inscription nécessaire pour qu’il devienne un point de terminaison de réception qui reçoit des notifications publiées à partir de votre serveur d’application ciblée sur un utilisateur. Le SDK est ensuite utilisé pour gérer les notifications sur le côté client, y compris la réception des notifications de nouvelles charges utiles est arrivé sur ce client, la gestion de l’état des notifications et récupération de l’historique de notification. Pour plus d’informations sur MS Graph Notifications et comment il permet la remise de notification orientée, consultez [vue d’ensemble des Notifications Microsoft Graph](index.md)

Consultez le [référence de l’API](api-reference-for-windows/index.md) page pour des liens vers la documentation de référence relatives à des scénarios de notification.

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>Programme d’installation préliminaire pour accéder à la plateforme d’appareils connectés pour pouvoir utiliser les Notifications de graphique 
Il existe quelques étapes à suivre pour intégrer des Notifications de graphique
* Compte de service administré ou inscription d’application AAD
* L’intégration du centre de développement pour fournir l’identité de l’application multiplateforme et transmettre les informations d’identification de la Notification
* Ajouter le Kit de développement et l’initialisation de la plateforme d’appareils connectés
* Associer le Service de Notification de plateforme d’appareils connectés

Tout d’abord, vous devez effectuer le MSA et/ou l’inscription de l’application AAD. Si vous avez déjà fait cela, passez à la section suivante.
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
Ensuite, vous devez intégrer avec Microsoft Windows Dev Center pour accéder à la plateforme d’appareils connectés afin de s’intégrer avec des expériences entre les périphériques, y compris l’utilisation de Notifications de graphique. Si vous avez déjà fait cela, passez à la section suivante.
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
Ensuite, vous devez ajouter le Kit de développement logiciel Project Rome à votre projet et initialiser la plateforme d’appareils connectés. Si vous avez déjà fait cela, passez à la section suivante.
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
Enfin, vous devez activer votre application recevoir des notifications push. Si vous avez déjà fait cela, passez à la section suivante.
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de Notification de graphique
À un niveau élevé, le SDK permet à votre application pour vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, y compris les Notifications de graphique, les activités des utilisateurs et bien plus encore. Il s’agit tout stockée et synchronisé dans **UserDataFeed**. **UserNotification** est la classe et type de données correspondant à une notification utilisateur ciblé envoyée par le biais de Notifications de graphique. Pour intégrer avec Notification de graphique et recevoir des UserNotification publiée par le serveur de votre application, vous devez d’abord initialiser les données utilisateur de flux en créant un **UserNotificationChannel**. Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme). 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Créer un UserNotificationReader pour recevoir des UserNotifications entrantes et accéder à l’historique UserNotification
Une fois que vous avez un **UserNotificationChannel** référence, vous devez un **UserNotificationReader** afin de permettre au SDK extraire le contenu de la notification à partir du serveur. Dans ce cas un UserNotificationReader permet à l’application l’accès client à ce flux de données – pour recevoir la dernière charge utile de notification via l’écouteur d’événements ou accéder à la collection UserNotification complète qui peut être utilisée en tant que modèle de vue de l’historique de notification de l’utilisateur.  

Le code suivant montre comment instancier un canal de notification utilisateur, créer un lecteur de la notification utilisateur et ajouter un gestionnaire d’événements sur le lecteur de notification utilisateur qui se déclenche quand la plateforme d’appareils connectés se termine chaque synchronisation et a des modifications apportées à vous en informer. 

```C#

public async Task SetupChannel()
{
    var account = m_accoutProvider.SignedInAccount;

    if (m_feed == null)
    {
        await Task.Run(() =>
        {
            lock (this)
            {
                if (m_feed == null)
                {
                    m_platform = new ConnectedDevicesPlatform(m_accoutProvider, this);

                    Logger.Instance.LogMessage($"Create feed for {account.Id} {account.Type}");
                    m_feed = new UserDataFeed(account, m_platform, "graphnotifications.sample.windows.com");
                    m_feed.SyncStatusChanged += Feed_SyncStatusChanged;
                    m_feed.AddSyncScopes(new List<IUserDataFeedSyncScope>
                    {
                        UserNotificationChannel.SyncScope
                    });

                    m_channel = new UserNotificationChannel(m_feed);
                    m_reader = m_channel.CreateReader();
                    m_reader.DataChanged += Reader_DataChanged;
                }
            }
        });
    }
}

```

### <a name="receiving-usernotifications"></a>Réception UserNotifications

Dans la section ci-dessus, nous voyons qu’un écouteur d’événement du est ajouté au lecteur de notification utilisateur. Vous devez implémenter cet écouteur d’événement pour lire toutes les nouvelles notifications et les mises à jour de la notification à partir du lecteur et implémenter votre propre logique métier pour gérer chacun de ces modifications. 

> [!TIP] 
> Cet écouteur d’événements est où vous traitez la logique commerciale principale et « utiliser » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement notification brute de WNS pour construire une notification toast local dans le centre de maintenance au niveau du système d’exploitation, ou si vous utilisez le contenu dans la notification pour mettre à jour d’une interface utilisateur dans l’application, c’est ici que pour ce faire. 

Le code suivant vous montre comment l’exemple d’application choisit de déclencher une notification toast local pour tous les UserNotification entrante qui sont actifs et supprimer la notification correspondante de l’interface utilisateur dans la vue dans l’application si une notification est supprimée. 

```C#

private void Reader_DataChanged(UserNotificationReader sender, object args)
{
    ReadNotifications(sender, true);
}

private async void ReadNotifications(UserNotificationReader reader, bool showToast)
{
    var notifications = await reader.ReadBatchAsync(UInt32.MaxValue);

    foreach (var notification in notifications)
    {

        if (notification.Status == UserNotificationStatus.Active)
        {
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            if (notification.UserActionState == UserNotificationUserActionState.NoInteraction)
            {
                // new notification, show this to user using the Windows local toast notification APIs
                m_newNotifications.Add(notification);
                if (!string.IsNullOrEmpty(notification.Content) && showToast)
                {
                    ShowToastNotification(BuildToastNotification(notification.Id, notification.Content));
                }
            }

            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.Insert(0, notification);
        }
        else
        {
            // Existing notification is marked as deleted, remove from display
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            RemoveToastNotification(notification.Id);
        }
    }
}

```
## <a name="update-the-state-of-an-existing-usernotification"></a>Mettre à jour l’état d’une UserNotification existante
Dans la section précédente, nous avons mentionné que parfois une modification UserNotification reçue via le lecteur peut être une mise à jour de l’état sur une UserNotification existante – si marquée comme dismissed ou marqués comme lus. Dans ce cas, le client de l’application peut choisir ce qu’il faut faire, telles que l’activation universel ignorer en supprimant la notification visual correspondante sur ce périphérique. Prenons un retour, votre client de l’application est souvent celui qui a lancé cette mise à jour de la modification UserNotification pour commencer : à partir d’un autre appareil. Vous pouvez choisir le moment pour mettre à jour l’état de votre UserNotifications, mais en général ils mis à jour lors de la notification visual correspondante est gérée par l’utilisateur sur l’appareil, ou la notification est plus gérée par l’utilisateur dans une certaine expérience dans l’application que vous activez . Voici à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblée sur l’utilisateur a. utilisateur A reçu cette notification sur son PC et sur son téléphone dans lequel les clients d’application sont installés. L’utilisateur clique sur la notification sur PC et court après dans l’application vers les handles de la tâche correspondante. Le client d’application sur ce PC appellera puis connecté les appareils Platform SDK pour mettre à jour l’état de le correspondante UserNotification afin de disposer de cette mise à jour synchronisée sur les appareils de tous les cet utilisateur. Les autres clients d’application, lors de la réception de cette mise à jour en temps réel d’état, seront puis supprimer l’alerte correspondante visual / message / notification à partir du centre de notification de l’appareil toast / barre d’état système / Centre de l’Action. Voici comment les notifications obtient universellement ignorées sur les appareils d’un utilisateur. 

> [!TIP] 
> Classe de UserNotification fournit actuellement 2 types de mises à jour de l’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState et définissez votre propre logique sur ce qui doit se produire lorsque les notifications sont mis à jour. Par exemple, vous pouvez marquer UserActionState pour être activé ou ignoré, et faire disparaître le tableau croisé dynamique sur cette valeur à mettre en œuvre universel. Vous pouvez également, ou en même temps vous pouvez marquer état ReadState comme lu ou non lu et en fonction de qui déterminent quelles notifications doivent apparaître dans l’affichage de l’historique de notification dans l’application. Code ci-dessous extrait de code montre comment marquer le UserNotificationUserActionState d’une notification en tant qu’ignoré.

```C#
public async void Dismiss(string id)
{
    var notification = m_newNotifications.Find((n) => { return (n.Id == id); });
    if (notification != null)
    {
        notification.UserActionState = UserNotificationUserActionState.Dismissed;
        await notification.SaveAsync();
    }
}

```
