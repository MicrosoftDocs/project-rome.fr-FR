---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909691"
---
### <a name="add-the-sdk"></a><span data-ttu-id="93e88-101">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="93e88-101">Add the SDK</span></span>

<span data-ttu-id="93e88-102">Pour Windows, SDK de Notification de graphique est mis à disposition pour les développeurs via un package NuGet au lieu du SDK de Windows du système d’exploitation intégrés afin d’avoir mieux bas niveau prise en charge et planification de mise en production plus flexible.</span><span class="sxs-lookup"><span data-stu-id="93e88-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="93e88-103">Le package NuGet est publié par msgraphsdkteam sur nuget.org et vous pouvez trouver [ici](https://www.nuget.org/profiles/msgraphsdkteam).</span><span class="sxs-lookup"><span data-stu-id="93e88-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="93e88-104">Pour plus d’informations, y compris et consommer des packages NuGet à partir de votre application UWP, consultez ces liens.</span><span class="sxs-lookup"><span data-stu-id="93e88-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* [<span data-ttu-id="93e88-105">Utiliser les packages de nuget.org</span><span class="sxs-lookup"><span data-stu-id="93e88-105">Use packages from nuget.org</span></span>](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [<span data-ttu-id="93e88-106">Démarrage rapide : Installer et utiliser un package dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93e88-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="93e88-107">Selon les scénarios que vous implémentez, vous nombreuses pas besoin de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="93e88-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="93e88-108">Pour les Notifications de graphique plus précisément, vous devez les espaces de noms comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="93e88-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="93e88-109">Initialiser la plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="93e88-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="93e88-110">Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="93e88-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="93e88-111">Les étapes d’initialisation doivent se produire dans votre classe principale **OnLaunched** ou **onActivated** (méthode), car ils sont requis avant d’autres scénarios d’appareils connectés peuvent avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="93e88-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="93e88-112">Vous devez instancier le **ConnectedDevicesPlatform** classe.</span><span class="sxs-lookup"><span data-stu-id="93e88-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="93e88-113">Le **ConnectedDevicesPlatform** constructeur accepte trois paramètres : le **contexte** pour l’application, un **NotificationProvider**et un  **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="93e88-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="93e88-114">Le **NotificationProvider** paramètre est uniquement nécessaire pour certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="93e88-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="93e88-115">En cas d’utilisation de notification Microsoft Graph, il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="93e88-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="93e88-116">Laissez ce champ vide pour l’instant et découvrir dans la section suivante pour activer le logiciel (SDK) pour gérer les notifications entrantes centrés sur l’utilisateur via des canaux de push natif.</span><span class="sxs-lookup"><span data-stu-id="93e88-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="93e88-117">Le **UserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="93e88-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="93e88-118">Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée.</span><span class="sxs-lookup"><span data-stu-id="93e88-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="93e88-119">Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous vous proposons compte implémentations du fournisseur pour Windows dans l’exemple de code, veillez à vérifier **MicrosoftAccountProvider.cs** pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="93e88-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="93e88-120">Puis vous pouvez construire un **plateforme** instance.</span><span class="sxs-lookup"><span data-stu-id="93e88-120">Then you can construct a **Platform** instance.</span></span> 

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

<span data-ttu-id="93e88-121">Vous devez arrêter la plateforme quand votre application s’arrête au premier plan.</span><span class="sxs-lookup"><span data-stu-id="93e88-121">You should shut down the platform when your app exits the foreground.</span></span>

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
