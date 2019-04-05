---
title: Créer des applications multiappareils
description: Découvrez les fonctionnalités multiappareils et multiplateformes activées pour les applications Windows 10 avec le projet Rome.
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: 57f6ce29730bd296ee623251d8ef619b114f944b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58906741"
---
# <a name="project-rome"></a>Projet Rome

Le [projet Rome](https://developer.microsoft.com/en-us/windows/project-rome) est la plateforme des expériences multiappareils de Microsoft pour les applications. 

Sur ce site, vous trouverez une documentation développeur pour le projet Rome et des liens vers d’autres ressources utiles.

Pour des actualités, des billets de blog et des vidéos sur le projet Rome, visitez la [page d’accueil du projet Rome](https://developer.microsoft.com/windows/project-rome).

Pour des exemples d’applications avec le projet Rome, consultez le tableau du SDK ci-dessous, ou visitez le [dépôt d’exemples du projet Rome](https://github.com/Microsoft/project-rome).

## <a name="about-project-rome"></a>À propos du projet Rome

Le projet Rome permet aux développeurs d’écrire des applications qui peuvent s’exécuter sur plusieurs appareils et qui accompagnent l’utilisateur quand il passe à un autre appareil.

Le projet Rome inclut des fonctionnalités exposées via Microsoft Graph et des SDK natifs spécifiques aux plateformes. Ce sont des fonctionnalités liées à des possibilités multiappareils et d’appareils connectés, permettant à vos applications d’être centrées autour de l’identité d’un utilisateur connecté. Les fonctionnalités associées au projet Rome incluent, sans y être limitées, les activités des utilisateurs, les notifications, les relais d’appareils et le partage à proximité.

## <a name="choosing-between-native-apis-and-graph-apis"></a>Choix entre les API natives et les API Graph

Certains scénarios sont disponibles via *à la fois* les SDK des plateformes natifs et les API REST via Microsoft Graph. En règle générale, les API REST permettent une implémentation simple et rapide des fonctionnalités du projet Rome. Il y a cependant des avantages à utiliser des implémentations spécifiques aux plateformes :

* Les kits SDK des plateformes fournissent un modèle objet dans le langage natif, un stockage local et un modèle publication-abonnement pour mettre à jour l’application quand les informations côté serveur changent.
* Si votre application s’exécute sur Windows (applications UWP ou Win32), le SDK de la plateforme fournit plusieurs fonctionnalités supplémentaires, comme l’utilisation du compte par défaut des utilisateurs et le suivi automatique de l’engagement utilisateur.
* Si vous prévoyez d’utiliser d’autres fonctionnalités du projet Rome qui sont disponibles seulement via les kits SDK des plateformes, vous pouvez implémenter chacune des fonctionnalités de la même façon.

D’autres scénarios sont possibles en utilisant une combinaison des API Microsoft Graph et des kits SDK des clients. Les notifications en sont un exemple. Dans ce cas, l’API MS Graph est utilisée pour publier des notifications depuis le côté serveur d’application, et les kits SDK des clients de plateforme natifs sont utilisés pour recevoir et gérer les notifications dans chacune des applications natives côté client.

## <a name="sdk"></a>Kit de développement logiciel

Le projet Rome est actuellement implémenté pour les plateformes ci-dessous. Suivez les liens pour obtenir des exemples et pour le téléchargement des kits SDK.

[windows-sdk]:             https://developer.microsoft.com/en-us/windows/downloads
[windows-sdk-badge]:       https://img.shields.io/badge/sdk-April%202018%20Update-brightgreen.svg
[windows-drsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems
[windows-afsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserActivity 

[winredist-sdk]:           https://www.nuget.org/packages/Microsoft.ConnectedDevices.UserNotifications
[winredist-sdk-badge]:     https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.UserNotifications.svg
[winredist-sample]:        https://github.com/Microsoft/project-rome/tree/release/1.0.0/Windows/samples

[xamarin-sdk]:             https://www.nuget.org/packages/Microsoft.ConnectedDevices.Xamarin.Droid
[xamarin-sdk-badge]:       https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.Xamarin.Droid.svg
[xamarin-sample]:          https://github.com/Microsoft/project-rome/tree/0.8.1/Xamarin/samples

[ios-sdk]:                 https://cocoapods.org/pods/ProjectRomeSdk
[ios-sdk-badge]:           https://img.shields.io/cocoapods/v/ProjectRomeSdk.svg
[ios-sample]:              https://github.com/Microsoft/project-rome/tree/release/1.0.0/iOS/samples

[android-sdk]:             https://bintray.com/connecteddevices/maven/com.microsoft.connecteddevices:connecteddevices-sdk?version=1.1.0
[android-sdk-badge]:       https://img.shields.io/bintray/v/connecteddevices/maven/com.microsoft.connecteddevices:connecteddevices-sdk.svg
[android-sample]:          https://github.com/Microsoft/project-rome/tree/release/1.0.0/Android/samples

[graph-relay]:             https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities]:        https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification]:      https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview

[graph-relay-badge]:       https://img.shields.io/badge/Device_Relay-Beta-orange.svg
[graph-activities-badge]:  https://img.shields.io/badge/Activities-1.0-brightgreen.svg
[graph-notification-badge]:https://img.shields.io/badge/Graph_Notifications-Beta-orange.svg

[graph-relay-sample]:        https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities-sample]:   https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification-sample]: https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview



|   Plateforme                        | Fonctionnalités                                                         |           Package SDK                          |   Exemples                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| **SDK Windows**                   | Relais d’appareils, activités/chronologie                                | [![SDK][windows-sdk-badge]][windows-sdk]       | [Exemple Windows du projet Rome pour les relais d’appareils][windows-drsample] <br> [Exemple Windows du projet Rome pour les activités][windows-afsample]
| **Windows (préversion)**             |                                    Notifications Microsoft Graph | [![Nuget][winredist-sdk-badge]][winredist-sdk] | [Exemple de notifications Graph pour Windows][winredist-sample] 
| **Android**             | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph | [![Maven][android-sdk-badge]][android-sdk]     | [Exemples du projet Rome pour Android][android-sample]
| **iOS**                 | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph | [![CocoaPod][ios-sdk-badge]][ios-sdk]          | [Exemples du projet Rome pour iOS][ios-sample]
| **Xamarin pour Android (préversion)** | Relais d’appareils                                                     | [![Nuget][xamarin-sdk-badge]][xamarin-sdk]     | [Exemple Xamarin pour Android][xamarin-sample]
| **MSGraph**                       | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph | [![REST][graph-relay-badge]][graph-relay]<br> [![REST][graph-activities-badge]][graph-activities]<br>[![REST][graph-notification-badge]][graph-notification]          | [Relais d’appareils][graph-relay-sample]<br>[Activités/chronologie][graph-activities-sample]<br>[Notifications Graph][graph-notification-sample]

## <a name="project-rome-blog-posts"></a>Billets de blog du projet Rome
* [Expériences multiplateformes avec le projet Rome](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [Going social: Project Rome, Maps, & Social Network Integration](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [Présentation du kit de développement logiciel (SDK) Android du projet Rome](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [Project Rome for Android Update: Now with App Services Support](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [Création d’une application Compagnon de contrôle à distance pour Android avec le projet Rome](https://blog.xamarin.com/building-remote-control-companion-app-android-project-rome/)

* [New Share Experience in Windows 10 Creators Update](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [Liaison application-site web avec les AppUriHandlers](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

## <a name="other-resources"></a>Autres ressources

* [Liaison web-application](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/web-to-app-linking)

* [//Build 2016 talk](https://channel9.msdn.com/Events/Build/2016/B831)

* [MS Dev Show podcast](http://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

## <a name="give-feedback"></a>Envoyer vos commentaires

|[UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/183208-connected-apps-and-devices-project-rome)|[Hub de commentaires](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[Nous contacter](mailto:projectrometeam@microsoft.com)|
|-----|-----|-----|
