---
title: Intégration d’applications UWP à la fonctionnalité Notifications Graph
description: Guide pratique pour effectuer les étapes d’inscription nécessaires permettant de devenir un point de terminaison de réception pour les notifications publiées à partir de votre serveur d’applications.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801301"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>Guides pratique : Intégration à la fonctionnalité Notifications MS Graph (Windows UWP)

Avec le SDK côté client Notifications Graph sur Windows, votre application UWP Windows peut effectuer les étapes d’inscription nécessaires pour devenir un point de terminaison de réception qui reçoit des notifications publiées à partir de votre serveur d’application ciblant un utilisateur. Le SDK est ensuite utilisé pour gérer les notifications côté client, notamment la réception des nouvelles charges utiles de notification arrivées sur ce client, la gestion de l’état des notifications et la récupération de l’historique des notifications. Pour plus d’informations sur la fonctionnalité Notifications MS Graph et la façon dont elle permet la remise de notifications centrées sur la personne, consultez [Vue d’ensemble des notifications Microsoft Graph](index.md).

Consultez la page [Informations de référence sur les API](api-reference-for-windows/index.md) pour obtenir des liens vers la documentation de référence pertinente pour les scénarios de notification.

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>Configuration préliminaire de l’accès à la Plateforme d’appareils connectés pour pouvoir utiliser les notifications Graph 
La procédure d’intégration de la fonctionnalité Notifications Graph comprend quelques étapes.
* Inscription d’application MSA ou AAD
* Intégration au Centre de développement pour fournir une identité d’application multiplateforme et envoie (par push) les informations d’identification de notification
* Ajout du SDK et initialisation de la Plateforme d’appareils connectés
* Associer le service de notification à la Plateforme d’appareils connectés

Tout d’abord, vous devez effectuer l’inscription d’application MSA et/ou AAD. Si vous l’avez déjà fait, passez à la section suivante.
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
Ensuite, vous devez effectuer une intégration au Centre de développement Microsoft Windows pour pouvoir accéder à la Plateforme d’appareils connectés pour une intégration à des expériences inter-appareils, notamment l’utilisation de la fonctionnalité Notifications Graph. Si vous l’avez déjà fait, passez à la section suivante.
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
Ensuite, vous devez ajouter le SDK Projet Rome à votre projet et initialiser la Plateforme d’appareils connectés. Si vous l’avez déjà fait, passez à la section suivante.
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
Enfin, vous devez permettre à votre application de recevoir les notifications Push. Si vous l’avez déjà fait, passez à la section suivante.
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>Initialiser un canal de notification Graph
De manière générale, le SDK permet à votre application de vous abonner à différents canaux afin de recevoir et de gérer différents types de données utilisateur, notamment les notifications Graph, les activités de l’utilisateur, et bien plus encore. Ils sont tous stockés et synchronisés dans **UserDataFeed**. **UserNotification** est la classe et le type de données correspondant à une notification ciblée sur l’utilisateur qui est envoyée par le biais de la fonctionnalité Notifications Graph. Pour effectuer une intégration à la fonctionnalité Notification Graph et recevoir un UserNotification publié par votre serveur d’applications, vous devez d’abord initialiser le flux de données utilisateur en créant un **UserNotificationChannel**. Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme). 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Créer un UserNotificationReader pour recevoir des UserNotification entrants et accéder à l’historique des UserNotification
Une fois que vous avez une référence à **UserNotificationChannel**, vous avez besoin d’un **UserNotificationReader** afin de permettre au SDK d’extraire le contenu de notification réel à partir du serveur. Dans ce cas, un UserNotificationReader permet au client d’application d’accéder à ce flux de données (pour recevoir la dernière charge utile de notification par le biais du détecteur d’événements ou accéder à la collection d’éléments UserNotification complète qui peut être utilisée comme modèle d’affichage de l’historique des notifications de l’utilisateur).  

Le code ci-dessous montre les étapes à suivre pour instancier un canal de notification utilisateur, créer un lecteur de notification utilisateur et ajouter un gestionnaire d’événements sur le lecteur de notification utilisateur qui se déclenche quand la Plateforme d’appareils connectés effectue chaque synchronisation et qu’elle doit vous informer de nouveaux changements. 

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

### <a name="receiving-usernotifications"></a>Réception de UserNotifications

Dans la section ci-dessus, nous voyons qu’un détecteur d’événements est ajouté au lecteur de notification utilisateur. Vous devez implémenter ce détecteur d’événements pour lire toutes les nouvelles notifications et les mises à jour de notification à partir du lecteur, et implémenter votre propre logique métier pour gérer chacun de ces nouveaux changements. 

> [!TIP] 
> Ce détecteur d’événements est l’endroit où vous traitez la principale logique métier et où vous « consommez » le contenu de votre charge utile de notification en fonction de vos scénarios. Si vous utilisez actuellement une notification brute de WNS pour construire une notification toast locale dans le centre de notifications au niveau du système d’exploitation, ou si vous utilisez le contenu de la notification pour mettre à jour une interface utilisateur dans l’application, c’est l’endroit approprié pour cela. 

Le code ci-dessous vous montre comment l’exemple d’application choisit de déclencher une notification toast locale pour tous les éléments UserNotification entrants qui sont actifs et de supprimer l’interface utilisateur de notification correspondante dans la vue dans l’application si une notification est supprimée. 

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
## <a name="update-the-state-of-an-existing-usernotification"></a>Mettre à jour l’état d’un UserNotification existant
Dans la section précédente, nous avons mentionné qu’un changement de UserNotification reçu par le biais du lecteur peut parfois être une mise à jour d’état sur un UserNotification existant (qu’il soit marqué comme masqué ou marqué comme lu). Dans ce cas, le client d’application peut choisir les actions à entreprendre, comme l’activation du masquage universel en supprimant la notification visuelle correspondante sur cet appareil particulier. Si nous revenons un peu en arrière, votre client d’application est souvent celui qui a lancé, à partir d’un autre appareil, cette mise à jour de changement de UserNotification pour commencer. Vous pouvez choisir le moment où mettre à jour l’état de vos UserNotifications, mais en général, ils sont mis à jour quand la notification visuelle correspondante est traitée par l’utilisateur sur cet appareil, ou quand l’utilisateur poursuit le traitement de la notification dans une expérience interne à l’application que vous activez. Voici un exemple de ce à quoi ressemblerait le flux : Votre serveur d’applications publie une notification ciblant l’utilisateur A. L’utilisateur A reçoit cette notification à la fois sur son PC et sur son téléphone où les clients d’application sont installés. L’utilisateur clique sur la notification sur le PC et parcourt l’application pour traiter la tâche correspondante. Le client d’application sur ce PC appelle alors le SDK de la Plateforme d’appareils connectés pour mettre à jour l’état du UserNotification correspondant afin que cette mise à jour synchronisée soit disponible sur tous les appareils de cet utilisateur. Quand les autres clients d’application reçoivent cette mise à jour d’état en temps réel, ils suppriment l’alerte visuelle/le message/la notification toast correspondant du centre de notifications/de la barre de notifications de l’appareil. Voici comment les notifications sont universellement masquées sur les appareils d’un utilisateur. 

> [!TIP] 
> La classe UserNotification fournit actuellement 2 types de mises à jour d’état : vous pouvez modifier le UserNotificationReadState ou le UserNotificationUserActionState, et définir votre propre logique sur ce qui doit se produire quand des notifications sont mises à jour. Par exemple, vous pouvez marquer UserActionState comme Activated (Activé) ou Dismissed (Masqué), et vous appuyer sur cette valeur pour implémenter le masquage universel. Alternativement ou simultanément, vous pouvez marquer ReadState comme Read (Lu) ou Unread (Non lu) et, en vous appuyant sur cette valeur, déterminez quelles notifications doivent apparaître dans l’affichage de l’historique des notifications internes à l’application. L’extrait de code ci-dessous montre comment marquer le UserNotificationUserActionState d’une notification comme Dismissed (Masqué).

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
