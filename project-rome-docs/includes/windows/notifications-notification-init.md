---
ms.openlocfilehash: f81fbbffb2ec54f8d9a252a00fc3822f1f3f9582
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800851"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-platform"></a>Associez la Plateforme d’appareils connectés à la notification Push native de chaque plateforme. 

Comme nous l’avons vu précédemment, les clients d’application doivent faire connaître au kit SDK côté client et à la Plateforme d’appareils connectés au moment de l’inscription le pipeline de notification Push natif qui est utilisé pour chaque plateforme, ceci afin de permettre au service de notification Graph de distribuer les notifications à chaque point de terminaison client d’application quand votre serveur d’applications publie une notification ciblant l’utilisateur via les API MS Graph.
Dans les étapes précédentes, vous avez initialisé la Plateforme sans paramètre **NotificationProvider**. Ici, vous devez construire et transmettre un objet qui implémente **NotificationProvider**. Pour en savoir plus, consultez **GraphNotificationProvider.cs** dans l’exemple. 



Transmettez cette inscription dans votre implémentation de **NotificationProvider**. Ensuite, l’appel d’initialisation de la **Plateforme** doit fournir à la **Plateforme** locale un accès au service de notification Push, permettant ainsi à votre application de recevoir des données des notifications MS Graph côté serveur. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Transmettre les notifications Push entrantes au SDK client
Maintenant, vous pouvez gérer la charge utile UserNotification entrante à l’intérieur de la tâche en arrière-plan native Windows inscrite auprès de PushNotificationTrigger ou dans votre écouteur de l’[événement PushNotificationReceived](https://docs.microsoft.com/en-us/uwp/api/windows.networking.pushnotifications.pushnotificationchannel.pushnotificationreceived). 

Pour des raisons notamment de conformité, de sécurité et d’optimisations potentielles, la notification brute WNS entrante en provenance des notifications Graph côté serveur peut souvent être une simple indication, qui ne contient aucune des données initialement publiées par le serveur d’applications. La récupération du contenu de notification effectif publié par le serveur d’applications est occultée par les API du SDK côté client. Dans ce cas, le SDK demande toujours au client d’application de transmettre la charge utile de notification brute WNS entrante au SDK. Cela permet au SDK de déterminer s’il s’agit d’une notification pour des scénarios de notifications Graph ou pas (dans le cas où des notifications Push brutes WNS peuvent aussi être utilisées par le client d’application à d’autres fins). 
