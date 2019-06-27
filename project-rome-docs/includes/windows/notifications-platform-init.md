---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909691"
---
### <a name="add-the-sdk"></a>Ajouter le kit SDK

Pour Windows, le kit SDK de notification Graph est mis à la disposition des développeurs via un package NuGet et non un SDK intégré au système d’exploitation Windows, le but étant d’offrir un support de bas niveau de meilleure qualité et une planification de mise en production plus flexible. Le package NuGet est publié par msgraphsdkteam sur nuget.org et vous pouvez le trouver [ici](https://www.nuget.org/profiles/msgraphsdkteam). 

Pour plus d’informations sur l’inclusion et l’utilisation de packages NuGet à partir de votre application UWP, consultez ces liens. 
* [Utiliser des packages de nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [Démarrage rapide : Installer et utiliser un package dans Visual Studio](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




Selon les scénarios que vous implémentez, vous n’avez peut-être pas besoin de tous les espaces de noms. Pour les notifications Graph en particulier, vous aurez besoin des espaces de noms présentés ci-dessous.


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>Initialiser la Plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application. Les étapes d’initialisation doivent se produire dans la méthode **OnLaunched** ou **onActivated** de votre classe principale, car elles constituent une condition préalable à l’exécution d’autres scénarios Appareils connectés. 

Vous devez instancier la classe **ConnectedDevicesPlatform**. Le constructeur **ConnectedDevicesPlatform** accepte trois paramètres : **Context** pour l’application, **NotificationProvider** et **UserAccountProvider**.

Le paramètre **NotificationProvider** est nécessaire uniquement pour certains scénarios. Il est obligatoire dans le cas d’une utilisation des notifications Microsoft Graph. Laissez-le vide pour l’instant et découvrez dans la section suivante comment permettre au SDK client de gérer les notifications entrantes centrées sur l’utilisateur via des canaux Push natifs.

Le paramètre **UserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés. Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme. 

Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Windows dans du code d’exemple. Pour plus d’informations, consultez **MicrosoftAccountProvider.cs**. 

Vous pouvez ensuite construire une instance de **Platform**. 

```C#

public async Task InstantiatePlatform()
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


                }
            }
        });
    }
}

```

Nous vous recommandons d’arrêter la plateforme quand votre application quitte le premier plan.

```C#

public async void Reset()
{
    if (m_platform != null)
    {
        await m_platform.ShutdownAsync();
        m_platform = null;
        m_feed = null;
        m_newNotifications.Clear();
        m_historicalNotifications.Clear();
    }
}

```
