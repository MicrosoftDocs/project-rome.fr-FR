---
title: Créer des applications multiappareils
description: Découvrez les fonctionnalités multiappareils et multiplateformes activées pour les applications Windows 10 avec le projet Rome.
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: 28e76debcb8d3d74333827062e2345e078374b46
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755731"
---
# <a name="project-rome"></a><span data-ttu-id="8f3d2-103">Projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-103">Project Rome</span></span>

<span data-ttu-id="8f3d2-104">Le [projet Rome](https://developer.microsoft.com/en-us/windows/project-rome) est la plateforme des expériences multiappareils de Microsoft pour les applications.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-104">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) is Microsoft's cross-device experiences platform for apps.</span></span> 

<span data-ttu-id="8f3d2-105">Sur ce site, vous trouverez une documentation développeur pour le projet Rome et des liens vers d’autres ressources utiles.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-105">On this site you will find developer documentation for Project Rome and links to other useful resources.</span></span>

<span data-ttu-id="8f3d2-106">Pour des actualités, des billets de blog et des vidéos sur le projet Rome, visitez la [page d’accueil du projet Rome](https://developer.microsoft.com/windows/project-rome).</span><span class="sxs-lookup"><span data-stu-id="8f3d2-106">For news, blog posts, and videos about Project Rome, visit the [Project Rome landing page](https://developer.microsoft.com/windows/project-rome).</span></span>

<span data-ttu-id="8f3d2-107">Pour des exemples d’applications avec le projet Rome, consultez le tableau du SDK ci-dessous, ou visitez le [dépôt d’exemples du projet Rome](https://github.com/Microsoft/project-rome).</span><span class="sxs-lookup"><span data-stu-id="8f3d2-107">For sample applications using Project Rome, check out the SDK table below, or visit the [Project Rome samples repo](https://github.com/Microsoft/project-rome).</span></span>

## <a name="about-project-rome"></a><span data-ttu-id="8f3d2-108">À propos du projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-108">About Project Rome</span></span>

<span data-ttu-id="8f3d2-109">Le projet Rome permet aux développeurs d’écrire des applications qui peuvent s’exécuter sur plusieurs appareils et qui accompagnent l’utilisateur quand il passe à un autre appareil.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-109">Project Rome allows developers to write apps that can run on multiple devices and travel with the user as they switch between devices.</span></span>

<span data-ttu-id="8f3d2-110">Le projet Rome inclut des fonctionnalités exposées via Microsoft Graph et des SDK natifs spécifiques aux plateformes.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-110">Project Rome includes features exposed via Microsoft Graph and platform-specific native SDKs.</span></span> <span data-ttu-id="8f3d2-111">Ce sont des fonctionnalités liées à des possibilités multiappareils et d’appareils connectés, permettant à vos applications d’être centrées autour de l’identité d’un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-111">These features enable multiple cross-device and connected-device capabilities, allowing your apps to be centralized around a logged-in user identity.</span></span> <span data-ttu-id="8f3d2-112">Les fonctionnalités associées au projet Rome incluent, sans y être limitées, les activités des utilisateurs, les notifications, les relais d’appareils et le partage à proximité.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-112">Features associated with Project Rome include but are not limited to user activities, notifications, device relay, and nearby share.</span></span>

## <a name="choosing-between-native-apis-and-graph-apis"></a><span data-ttu-id="8f3d2-113">Choix entre les API natives et les API Graph</span><span class="sxs-lookup"><span data-stu-id="8f3d2-113">Choosing between native APIs and Graph APIs</span></span>

<span data-ttu-id="8f3d2-114">Certains scénarios sont disponibles via *à la fois* les SDK des plateformes natifs et les API REST via Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-114">Some scenarios are available through *both* the native platform SDKs and REST APIs via Microsoft Graph.</span></span> <span data-ttu-id="8f3d2-115">En règle générale, les API REST permettent une implémentation simple et rapide des fonctionnalités du projet Rome.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-115">In general, the REST APIs enable quick and simple implementation of the Project Rome features.</span></span> <span data-ttu-id="8f3d2-116">Il y a cependant des avantages à utiliser des implémentations spécifiques aux plateformes :</span><span class="sxs-lookup"><span data-stu-id="8f3d2-116">However, there are some advantages to using platform-specific implementations:</span></span>

* <span data-ttu-id="8f3d2-117">Les kits SDK des plateformes fournissent un modèle objet dans le langage natif, un stockage local et un modèle publication-abonnement pour mettre à jour l’application quand les informations côté serveur changent.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-117">The platform SDKs provide an object model in the native language, local storage, and a publish-subscribe pattern to update the app when server-side information changes.</span></span>
* <span data-ttu-id="8f3d2-118">Si votre application s’exécute sur Windows (applications UWP ou Win32), le SDK de la plateforme fournit plusieurs fonctionnalités supplémentaires, comme l’utilisation du compte par défaut des utilisateurs et le suivi automatique de l’engagement utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-118">If your app runs on Windows (UWP or Win32 apps), the platform SDK provides a number of additional features, such as using the users' default account and automatically tracking user engagement.</span></span>
* <span data-ttu-id="8f3d2-119">Si vous prévoyez d’utiliser d’autres fonctionnalités du projet Rome qui sont disponibles seulement via les kits SDK des plateformes, vous pouvez implémenter chacune des fonctionnalités de la même façon.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-119">If you plan to use other Project Rome features that are only available through the platform SDKs, you may wish to implement each of the features in the same way.</span></span>

<span data-ttu-id="8f3d2-120">D’autres scénarios sont possibles en utilisant une combinaison des API Microsoft Graph et des kits SDK des clients.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-120">Some other scenarios are enabled by using a combination of Microsoft Graph APIs and client SDKs.</span></span> <span data-ttu-id="8f3d2-121">Les notifications en sont un exemple.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-121">An example of this is Notifications.</span></span> <span data-ttu-id="8f3d2-122">Dans ce cas, l’API MS Graph est utilisée pour publier des notifications depuis le côté serveur d’application, et les kits SDK des clients de plateforme natifs sont utilisés pour recevoir et gérer les notifications dans chacune des applications natives côté client.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-122">In this case, MS Graph API is used to publish notifications from app server side, and the native-platform client SDKs are utilized to receive and manage notifications in each client-side native apps.</span></span>

## <a name="sdk"></a><span data-ttu-id="8f3d2-123">Kit de développement logiciel</span><span class="sxs-lookup"><span data-stu-id="8f3d2-123">SDK</span></span>

<span data-ttu-id="8f3d2-124">Le projet Rome est actuellement implémenté pour les plateformes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-124">Project Rome is currently implemented for the below platforms.</span></span> <span data-ttu-id="8f3d2-125">Suivez les liens pour obtenir des exemples et pour le téléchargement des kits SDK.</span><span class="sxs-lookup"><span data-stu-id="8f3d2-125">Follow the links for samples and SDK downloads.</span></span>

[windows-sdk]:             https://developer.microsoft.com/en-us/windows/downloads
[windows-sdk-badge]:       https://img.shields.io/badge/sdk-April%202018%20Update-brightgreen.svg
[windows-drsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems
[windows-afsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserActivity 

[winredist-sdk]:           https://www.nuget.org/packages/Microsoft.ConnectedDevices.UserNotifications
[winredist-sdk-badge]:     https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.UserNotifications.svg
[winredist-sample]:        https://github.com/microsoft/project-rome/tree/master/Windows/samples

[xamarin-sdk]:             https://www.nuget.org/packages/Microsoft.ConnectedDevices.Xamarin.Droid
[xamarin-sdk-badge]:       https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.Xamarin.Droid.svg
[xamarin-sample]:          https://github.com/Microsoft/project-rome/tree/0.8.1/Xamarin/samples

[ios-sdk]:                 https://cocoapods.org/pods/ProjectRomeSdk
[ios-sdk-badge]:           https://img.shields.io/cocoapods/v/ProjectRomeSdk.svg
[ios-sample]:              https://github.com/microsoft/project-rome/tree/master/iOS/samples

[android-sdk]:             https://bintray.com/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/_latestVersion
[android-sdk-badge]:       https://api.bintray.com/packages/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/images/download.svg
[android-sample]:          https://github.com/microsoft/project-rome/tree/master/Android/samples

[graph-relay]:             https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities]:        https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification]:      https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview

[graph-relay-badge]:       https://img.shields.io/badge/Device_Relay-Beta-orange.svg
[graph-activities-badge]:  https://img.shields.io/badge/Activities-1.0-brightgreen.svg
[graph-notification-badge]:https://img.shields.io/badge/Graph_Notifications-Beta-orange.svg

[graph-relay-sample]:        https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities-sample]:   https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification-sample]: https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview



|   <span data-ttu-id="8f3d2-126">Plateforme</span><span class="sxs-lookup"><span data-stu-id="8f3d2-126">Platform</span></span>                        | <span data-ttu-id="8f3d2-127">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="8f3d2-127">Features</span></span>                                                         |           <span data-ttu-id="8f3d2-128">Package SDK</span><span class="sxs-lookup"><span data-stu-id="8f3d2-128">SDK Package</span></span>                          |   <span data-ttu-id="8f3d2-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="8f3d2-129">Samples</span></span>                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| <span data-ttu-id="8f3d2-130">**SDK Windows**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-130">**Windows SDK**</span></span>                   | <span data-ttu-id="8f3d2-131">Relais d’appareils, activités/chronologie</span><span class="sxs-lookup"><span data-stu-id="8f3d2-131">Device Relay, Activities/Timeline</span></span>                                | <span data-ttu-id="8f3d2-132">[![SDK][windows-sdk-badge]][windows-sdk]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-132">[![SDK][windows-sdk-badge]][windows-sdk]</span></span>       | <span data-ttu-id="8f3d2-133">[Exemple Windows du projet Rome pour les relais d’appareils][windows-drsample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-133">[Project Rome for Device Relay Windows sample][windows-drsample]</span></span> <br> <span data-ttu-id="8f3d2-134">[Exemple Windows du projet Rome pour les activités][windows-afsample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-134">[Project Rome for Activities Windows sample][windows-afsample]</span></span>
| <span data-ttu-id="8f3d2-135">**Windows (préversion)**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-135">**Windows (Preview)**</span></span>             |                                    <span data-ttu-id="8f3d2-136">Notifications Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="8f3d2-136">Microsoft Graph Notifications</span></span> | <span data-ttu-id="8f3d2-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span></span> | <span data-ttu-id="8f3d2-138">[Exemple de notifications Graph pour Windows][winredist-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-138">[Graph Notifications for Windows sample][winredist-sample]</span></span> 
| <span data-ttu-id="8f3d2-139">**Android**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-139">**Android**</span></span>             | <span data-ttu-id="8f3d2-140">Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph (préversion)</span><span class="sxs-lookup"><span data-stu-id="8f3d2-140">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="8f3d2-141">[![Maven][android-sdk-badge]][android-sdk]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-141">[![Maven][android-sdk-badge]][android-sdk]</span></span>     | <span data-ttu-id="8f3d2-142">[Exemples du projet Rome pour Android][android-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-142">[Project Rome for Android sample][android-sample]</span></span>
| <span data-ttu-id="8f3d2-143">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-143">**iOS**</span></span>                 | <span data-ttu-id="8f3d2-144">Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph (préversion)</span><span class="sxs-lookup"><span data-stu-id="8f3d2-144">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="8f3d2-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span></span>          | <span data-ttu-id="8f3d2-146">[Exemples du projet Rome pour iOS][ios-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-146">[Project Rome for iOS sample][ios-sample]</span></span>
| <span data-ttu-id="8f3d2-147">**Xamarin pour Android (préversion)**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-147">**Xamarin for Android (Preview)**</span></span> | <span data-ttu-id="8f3d2-148">Relais d’appareils</span><span class="sxs-lookup"><span data-stu-id="8f3d2-148">Device Relay</span></span>                                                     | <span data-ttu-id="8f3d2-149">[![Nuget][xamarin-sdk-badge]][xamarin-sdk]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-149">[![Nuget][xamarin-sdk-badge]][xamarin-sdk]</span></span>     | <span data-ttu-id="8f3d2-150">[Exemple Xamarin pour Android][xamarin-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-150">[Xamarin for Android sample][xamarin-sample]</span></span>
| <span data-ttu-id="8f3d2-151">**MSGraph**</span><span class="sxs-lookup"><span data-stu-id="8f3d2-151">**MSGraph**</span></span>                       | <span data-ttu-id="8f3d2-152">Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="8f3d2-152">Device Relay, Activities/Timeline, Microsoft Graph Notifications</span></span> | <span data-ttu-id="8f3d2-153">[![REST][graph-relay-badge]][graph-relay]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-153">[![REST][graph-relay-badge]][graph-relay]</span></span><br> <span data-ttu-id="8f3d2-154">[![REST][graph-activities-badge]][graph-activities]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-154">[![REST][graph-activities-badge]][graph-activities]</span></span><br><span data-ttu-id="8f3d2-155">[![REST][graph-notification-badge]][graph-notification]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-155">[![REST][graph-notification-badge]][graph-notification]</span></span>          | <span data-ttu-id="8f3d2-156">[Relais d’appareils][graph-relay-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-156">[Device Relay][graph-relay-sample]</span></span><br><span data-ttu-id="8f3d2-157">[Activités/chronologie][graph-activities-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-157">[Activities/Timeline][graph-activities-sample]</span></span><br><span data-ttu-id="8f3d2-158">[Notifications Graph][graph-notification-sample]</span><span class="sxs-lookup"><span data-stu-id="8f3d2-158">[Graph Notifications][graph-notification-sample]</span></span>

## <a name="project-rome-blog-posts"></a><span data-ttu-id="8f3d2-159">Billets de blog du projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-159">Project Rome blog posts</span></span>
* [<span data-ttu-id="8f3d2-160">Expériences multiplateformes avec le projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-160">Cross-device experiences with Project Rome</span></span>](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [<span data-ttu-id="8f3d2-161">Going social: Project Rome, Maps, & Social Network Integration</span><span class="sxs-lookup"><span data-stu-id="8f3d2-161">Going social: Project Rome, Maps, & Social Network Integration</span></span>](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [<span data-ttu-id="8f3d2-162">Présentation du kit de développement logiciel (SDK) Android du projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-162">Announcing Project Rome Android SDK</span></span>](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [<span data-ttu-id="8f3d2-163">Project Rome for Android Update: Now with App Services Support</span><span class="sxs-lookup"><span data-stu-id="8f3d2-163">Project Rome for Android Update: Now with App Services Support</span></span>](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [<span data-ttu-id="8f3d2-164">Création d’une application Compagnon de contrôle à distance pour Android avec le projet Rome</span><span class="sxs-lookup"><span data-stu-id="8f3d2-164">Building a Remote Control Companion App for Android with Project Rome</span></span>](https://blog.xamarin.com/building-remote-control-companion-app-android-project-rome/)

* [<span data-ttu-id="8f3d2-165">New Share Experience in Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="8f3d2-165">New Share Experience in Windows 10 Creators Update</span></span>](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [<span data-ttu-id="8f3d2-166">Liaison application-site web avec les AppUriHandlers</span><span class="sxs-lookup"><span data-stu-id="8f3d2-166">Web-to-App Linking with AppUriHandlers</span></span>](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

## <a name="other-resources"></a><span data-ttu-id="8f3d2-167">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="8f3d2-167">Other resources</span></span>

* [<span data-ttu-id="8f3d2-168">Liaison web-application</span><span class="sxs-lookup"><span data-stu-id="8f3d2-168">Web-to-app linking</span></span>](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/web-to-app-linking)

* [<span data-ttu-id="8f3d2-169">//Build 2016 talk</span><span class="sxs-lookup"><span data-stu-id="8f3d2-169">//Build 2016 talk</span></span>](https://channel9.msdn.com/Events/Build/2016/B831)

* [<span data-ttu-id="8f3d2-170">MS Dev Show podcast</span><span class="sxs-lookup"><span data-stu-id="8f3d2-170">MS Dev Show podcast</span></span>](http://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

## <a name="give-feedback"></a><span data-ttu-id="8f3d2-171">Envoyer vos commentaires</span><span class="sxs-lookup"><span data-stu-id="8f3d2-171">Give feedback</span></span>

|[<span data-ttu-id="8f3d2-172">UserVoice</span><span class="sxs-lookup"><span data-stu-id="8f3d2-172">UserVoice</span></span>](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/183208-connected-apps-and-devices-project-rome)|[<span data-ttu-id="8f3d2-173">Hub de commentaires</span><span class="sxs-lookup"><span data-stu-id="8f3d2-173">Feedback Hub</span></span>](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[<span data-ttu-id="8f3d2-174">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="8f3d2-174">Contact Us</span></span>](mailto:projectrometeam@microsoft.com)|
|-----|-----|-----|
