---
title: UserNotification
description: Cette classe représente une notification utilisateur publiées par le serveur d’applications par le biais de Notifications de graphique et reçu par le client de l’application.
keywords: Microsoft, windows, des notifications de graphique, des conseils pour windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907961"
---
# <a name="class-usernotification"></a>Classe `UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

Cette classe représente une instance de la notification utilisateur unique. Une notification de l’utilisateur est créée et publiée par votre serveur d’application ciblée sur un utilisateur, distribué à tous les points de terminaison de périphérique du même utilisateur connecté.
Une notification de l’utilisateur, une fois reçue par le client de l’application, peut entraîner des expériences telles que la génération et affichage d’une bannière de notification visuelle à l’aide des API de notification locale de la plateforme correspondante.

## <a name="properties"></a>Properties

|Nom | Description |
|:-- |:-- |
|Id |Obtient le développeur spécifié unique id pour cette notification à l’utilisateur.|
|   GroupId |Obtient le développeur spécifié id de groupe pour cette notification à l’utilisateur.| 
|   ExpirationTime |Obtient le délai d’expiration pour cette notification à l’utilisateur.| 
|   Priority|Obtient le développeur spécifié priorité pour cette notification à l’utilisateur.| 
|   Contenu|Obtient la charge utile de contenu pour cette notification, qui est défini de développeur des données arbitraires.| 
|   ReadState|Obtient la valeur de l’état de lecture pour cette notification utilisateur qui indique la notification est lu ou non lu.| 
|   UserActionState|Obtient la valeur de l’état d’action utilisateur pour une notification de l’utilisateur déterminer si la notification n'est pas interagie, fermée, activée ou répétée.| 


## <a name="methods"></a>Méthodes

### <a name="saveasync"></a>SaveAsync() 
Cela doit être appelée lors de la publication des modifications de notification utilisateur. Cette méthode doit être appelée chaque fois que l’application modifie une propriété d’être mise à jour de la UserNotification.
```C#
public IAsyncOperation SaveAsync()
```

