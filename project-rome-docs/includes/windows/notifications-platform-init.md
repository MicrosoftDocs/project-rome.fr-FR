---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909691"
---
### <a name="add-the-sdk"></a><span data-ttu-id="ac703-101">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="ac703-101">Add the SDK</span></span>

<span data-ttu-id="ac703-102">Pour Windows, le kit SDK de notification Graph est mis à la disposition des développeurs via un package NuGet et non un SDK intégré au système d’exploitation Windows, le but étant d’offrir un support de bas niveau de meilleure qualité et une planification de mise en production plus flexible.</span><span class="sxs-lookup"><span data-stu-id="ac703-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="ac703-103">Le package NuGet est publié par msgraphsdkteam sur nuget.org et vous pouvez le trouver [ici](https://www.nuget.org/profiles/msgraphsdkteam).</span><span class="sxs-lookup"><span data-stu-id="ac703-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="ac703-104">Pour plus d’informations sur l’inclusion et l’utilisation de packages NuGet à partir de votre application UWP, consultez ces liens.</span><span class="sxs-lookup"><span data-stu-id="ac703-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* [<span data-ttu-id="ac703-105">Utiliser des packages de nuget.org</span><span class="sxs-lookup"><span data-stu-id="ac703-105">Use packages from nuget.org</span></span>](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [<span data-ttu-id="ac703-106">Démarrage rapide : Installer et utiliser un package dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ac703-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="ac703-107">Selon les scénarios que vous implémentez, vous n’avez peut-être pas besoin de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="ac703-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="ac703-108">Pour les notifications Graph en particulier, vous aurez besoin des espaces de noms présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ac703-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="ac703-109">Initialiser la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="ac703-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="ac703-110">Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="ac703-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="ac703-111">Les étapes d’initialisation doivent se produire dans la méthode **OnLaunched** ou **onActivated** de votre classe principale, car elles constituent une condition préalable à l’exécution d’autres scénarios Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="ac703-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="ac703-112">Vous devez instancier la classe **ConnectedDevicesPlatform**.</span><span class="sxs-lookup"><span data-stu-id="ac703-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="ac703-113">Le constructeur **ConnectedDevicesPlatform** accepte trois paramètres : **Context** pour l’application, **NotificationProvider** et **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="ac703-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="ac703-114">Le paramètre **NotificationProvider** est nécessaire uniquement pour certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="ac703-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="ac703-115">Il est obligatoire dans le cas d’une utilisation des notifications Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="ac703-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="ac703-116">Laissez-le vide pour l’instant et découvrez dans la section suivante comment permettre au SDK client de gérer les notifications entrantes centrées sur l’utilisateur via des canaux Push natifs.</span><span class="sxs-lookup"><span data-stu-id="ac703-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="ac703-117">Le paramètre **UserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="ac703-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="ac703-118">Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ac703-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="ac703-119">Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Windows dans du code d’exemple. Pour plus d’informations, consultez **MicrosoftAccountProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="ac703-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="ac703-120">Vous pouvez ensuite construire une instance de **Platform**.</span><span class="sxs-lookup"><span data-stu-id="ac703-120">Then you can construct a **Platform** instance.</span></span> 

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

<span data-ttu-id="ac703-121">Nous vous recommandons d’arrêter la plateforme quand votre application quitte le premier plan.</span><span class="sxs-lookup"><span data-stu-id="ac703-121">You should shut down the platform when your app exits the foreground.</span></span>

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
