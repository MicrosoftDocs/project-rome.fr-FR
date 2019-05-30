---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909691"
---
### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Pour Windows, SDK de Notification de graphique est mis à disposition pour les développeurs via un package NuGet au lieu du SDK de Windows du système d’exploitation intégrés afin d’avoir mieux bas niveau prise en charge et planification de mise en production plus flexible. Le package NuGet est publié par msgraphsdkteam sur nuget.org et vous pouvez trouver [ici](https://www.nuget.org/profiles/msgraphsdkteam). 

Pour plus d’informations, y compris et consommer des packages NuGet à partir de votre application UWP, consultez ces liens. 
* [Utiliser les packages de nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [Démarrage rapide : Installer et utiliser un package dans Visual Studio](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




Selon les scénarios que vous implémentez, vous nombreuses pas besoin de tous les espaces de noms. Pour les Notifications de graphique plus précisément, vous devez les espaces de noms comme indiqué ci-dessous.


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>Initialiser la plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application. Les étapes d’initialisation doivent se produire dans votre classe principale **OnLaunched** ou **onActivated** (méthode), car ils sont requis avant d’autres scénarios d’appareils connectés peuvent avoir lieu. 

Vous devez instancier le **ConnectedDevicesPlatform** classe. Le **ConnectedDevicesPlatform** constructeur accepte trois paramètres : le **contexte** pour l’application, un **NotificationProvider**et un  **UserAccountProvider**.

Le **NotificationProvider** paramètre est uniquement nécessaire pour certains scénarios. En cas d’utilisation de notification Microsoft Graph, il est nécessaire. Laissez ce champ vide pour l’instant et découvrir dans la section suivante pour activer le logiciel (SDK) pour gérer les notifications entrantes centrés sur l’utilisateur via des canaux de push natif.

Le **UserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés. Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée. 

Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous vous proposons compte implémentations du fournisseur pour Windows dans l’exemple de code, veillez à vérifier **MicrosoftAccountProvider.cs** pour plus d’informations. 

Puis vous pouvez construire un **plateforme** instance. 

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

Vous devez arrêter la plateforme quand votre application s’arrête au premier plan.

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
