---
title: Notifications Microsoft Graph
description: Incluez des notifications Microsoft Graph dans votre application pour réengager les utilisateurs d’une façon centrée sur la personne.
ms.localizationpriority: medium
ms.topic: overview
ms.custom: seodec2018
ms.openlocfilehash: 23aefb0e9f75721977e3ab9f1002bebf264a5b09
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "58906761"
---
# <a name="microsoft-graph-notifications"></a>Notifications Microsoft Graph
Les notifications sont le moyen le plus efficace de réengager vos utilisateurs. Elles peuvent attirer l’attention de vos utilisateurs et ramener l’utilisateur à votre application. Dans un monde multiappareil, vos utilisateurs peuvent accéder à vos applications et services depuis n’importe où, à travers différentes plateformes et différents appareils où vos applications sont présentes.
Vos scénarios de notification doivent être conçus d’une façon « centrée sur la personne », où l’objectif principal est de notifier l’utilisateur, où qu’il soit. Les solutions de notification existantes fournies par les principales plateformes sont excellentes pour cibler des appareils. Les notifications Microsoft Graph améliorent ceci en vous permettant de cibler des utilisateurs. Les notifications Microsoft Graph prennent en charge le gros du travail, notamment le mappage entre les utilisateurs et les points de terminaison, la synchronisation de l’état des notifications entre les différents points de terminaison des utilisateurs, etc.

## <a name="why-integrate-with-microsoft-graph-notifications"></a>Pourquoi s’intégrer aux notifications Microsoft Graph ?

### <a name="deliver-notifications-to-a-user-across-different-endpoints"></a>Délivrer des notifications à un utilisateur sur différents points de terminaison
L’API Notifications, qui fait partie de Microsoft Graph, vous permet de cibler un compte Microsoft, ou un compte professionnel ou scolaire (Azure Active Directory), pour délivrer une notification. La plateforme distribue cette notification à tous les points de terminaison des utilisateurs, notamment Windows UWP, Android et iOS.

### <a name="manage-notifications-across-endpoints"></a>Gérer les notifications sur des points de terminaison
L’API Notifications Microsoft Graph vous permet de mettre à jour l’état d’une notification et de synchroniser cet état sur tous les points de terminaison. Par exemple, quand un utilisateur réagit à une notification sur un appareil, vous pouvez mettre à jour l’état de cette notification (par exemple la marquer comme étant lue ou ignorée) : le même changement d’état est alors distribué à tous les autres points de terminaison. L’API Notifications Microsoft Graph suit l’état des notifications de vos utilisateurs de façon centralisée, ce qui vous permet de garantir que vos notifications ne sont traitées qu’une seule fois, et mises à jour ou ignorées partout.

### <a name="retrieve-notification-history"></a>Récupérer l’historique des notifications
Vous pouvez utiliser l’API Notifications pour récupérer l’historique des notifications selon un délai d’expiration que vous définissez (jusqu’à 30 jours). Les notifications qui sont marquées comme lues ou ignorées sont toujours récupérables à partir de l’historique, ce qui permet des vues dans l’application de l’historique des notifications et d’autres scénarios.

## <a name="integrating-with-microsoft-graph-notifications"></a>Intégration aux notifications Microsoft Graph

### <a name="onboarding"></a>Intégration
Examinez le guide de procédure sous chaque nœud de plateforme (Windows, Android et iOS) pour obtenir des instructions sur l’utilisation des notifications Graph comme solution de notification Push mobile pour vos applications et services. Notez que ces guides de procédure mettent l’accent sur la réception des notifications. Vous trouverez des informations sur l’envoi des notifications dans la page [Envoi de notifications avec les API MS Graph](sending-notifications.md).

Le guide comprend les étapes spécifiques pour l’utilisation des notifications Graph, notamment l’inscription des identités d’application multiplateforme et des informations d’identification d’envoi (push) mobile. Si vous découvrez l’utilisation de Microsoft Graph, des étapes sont incluses pour l’inscription de votre application à un compte Microsoft (MSA) pour les applications destinées aux consommateurs, ou à Azure Active Directory (AAD) pour les comptes professionnels et scolaires. MSA et AAD sont des identités utilisateur qui vous permettent de tirer parti des charges de travail sur Microsoft Graph au-delà des seules notifications, ce qui permet des scénarios métier plus riches. 

### <a name="microsoft-graph-apis"></a>API Microsoft Graph
Lors de l’utilisation des notifications Graph, le serveur d’application doit utiliser l’API Microsoft Graph (version bêta) pour envoyer des notifications. Pour plus d’informations sur l’intégration côté serveur d’application, consultez les [documents de référence de l’API](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview) concernant son utilisation. 

### <a name="client-side-sdk"></a>SDK côté client
Pour démarrer avec l’intégration des notifications Graph côté client et commencer à recevoir et à gérer des notifications avec les kits SDK natifs, sélectionnez votre plateforme de développement préférée dans le volet de navigation gauche. 

* [Envoi de notifications avec les API MS Graph](sending-notifications.md)
* [Réception de notifications avec le SDK Projet Rome](receiving-notifications.md)
