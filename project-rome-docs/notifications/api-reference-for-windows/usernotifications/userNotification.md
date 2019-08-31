---
title: UserNotification
description: Cette classe représente une notification utilisateur publiée par le serveur d’applications par le biais de notifications de graphique et reçue par le client d’application.
keywords: Microsoft, Windows, notifications Graph, fenêtres de procédures
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801591"
---
# <a name="class-usernotification"></a>type`UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

Cette classe représente une instance de notification d’utilisateur unique. Une notification utilisateur est créée et publiée par votre serveur d’applications ciblé sur un utilisateur et distribuée à tous les points de terminaison d’appareil du même utilisateur connecté.
Une notification utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et l’utilisation d’une bannière de notification visuelle à l’aide des API de notification locales de la plateforme correspondante.

## <a name="properties"></a>Properties

|Name | Description |
|:-- |:-- |
|Id |Obtient l’ID unique spécifié par le développeur pour cette notification utilisateur.|
|   GroupId |Obtient l’ID de groupe spécifié par le développeur pour cette notification utilisateur.| 
|   ExpirationTime |Obtient l’heure d’expiration de cette notification utilisateur.| 
|   Priority|Obtient la priorité spécifiée par le développeur pour cette notification utilisateur.| 
|   Contenu|Obtient la charge utile de contenu pour cette notification, qui est une donnée arbitraire définie par le développeur.| 
|   ReadState|Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique que la notification est lue ou non.| 
|   UserActionState|Obtient la valeur de l’état de l’action utilisateur pour une notification utilisateur afin de déterminer si la notification n’est pas interactive, fermée, activée ou répétée.| 


## <a name="methods"></a>Méthodes

### <a name="saveasync"></a>SaveAsync () 
Cela doit être appelé lors de la publication des modifications de notification utilisateur. Cette méthode doit être appelée chaque fois que l’application modifie une propriété pouvant être mise à jour de UserNotification.
```C#
public IAsyncOperation SaveAsync()
```

