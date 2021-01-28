---
title: Créer des applications multiappareils
description: Découvrez les fonctionnalités multiappareils et multiplateformes activées pour les applications Windows 10 avec le projet Rome.
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: dc66e86ea9ed5c5750fc31a2961798b7335d5fb0
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901417"
---
# <a name="project-rome"></a>Projet Rome

Le [projet Rome](https://developer.microsoft.com/windows/project-rome) est la plateforme des expériences multiappareils de Microsoft pour les applications.

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

## <a name="sdk"></a>Kit SDK

Le projet Rome est actuellement implémenté pour les plateformes ci-dessous. Suivez les liens pour obtenir des exemples et pour le téléchargement des kits SDK.

[windows-sdk]:             https://developer.microsoft.com/windows/downloads
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

[android-sdk]:             https://github.com/microsoft/project-rome/tree/mvn-repo/com/microsoft/connecteddevices/connecteddevices-sdk
[android-sdk-badge]:       https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Fraw.github.com%2Fmicrosoft%2Fproject-rome%2Fmvn-repo%2Fcom%2Fmicrosoft%2Fconnecteddevices%2Fconnecteddevices-sdk%2Fmaven-metadata.xml
[android-sample]:          https://github.com/microsoft/project-rome/tree/master/Android/samples

[graph-relay]:             /graph/api/resources/project-rome-overview
[graph-activities]:        /graph/api/resources/activity-feed-api-overview
[graph-notification]:      /graph/api/resources/notifications-api-overview

[graph-relay-badge]:       https://img.shields.io/badge/Device_Relay-Beta-orange.svg
[graph-activities-badge]:  https://img.shields.io/badge/Activities-1.0-brightgreen.svg
[graph-notification-badge]:https://img.shields.io/badge/Graph_Notifications-Beta-orange.svg

[graph-relay-sample]:        /graph/api/resources/project-rome-overview
[graph-activities-sample]:   /graph/api/resources/activity-feed-api-overview
[graph-notification-sample]: /graph/api/resources/notifications-api-overview



|   Plateforme                        | Fonctionnalités                                                         |           Package du SDK                          |   Exemples                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| **SDK Windows**                   | Relais d’appareils, activités/chronologie                                | [![Kit SDK][windows-sdk-badge]][windows-sdk]       | [Exemple Windows du projet Rome pour les relais d’appareils][windows-drsample] <br> [Exemple Windows du projet Rome pour les activités][windows-afsample]
| **Windows (préversion)**             |                                    Notifications Microsoft Graph | [![Nuget][winredist-sdk-badge]][winredist-sdk] | [Exemple de notifications Graph pour Windows][winredist-sample]
| **Android**             | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph (préversion) | [![Maven][android-sdk-badge]][android-sdk]     | [Exemples du projet Rome pour Android][android-sample]
| **iOS**                 | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph (préversion) | [![CocoaPod][ios-sdk-badge]][ios-sdk]          | [Exemple du projet Rome pour iOS][ios-sample]
| **Xamarin pour Android (préversion)** | Relais d’appareils                                                     | [![Nuget][xamarin-sdk-badge]][xamarin-sdk]     | [Exemple Xamarin pour Android][xamarin-sample]
| **MSGraph**                       | Relais d’appareils, Activités/chronologie, Notifications Microsoft Graph | [![REST][graph-relay-badge]][graph-relay]<br> [![REST][graph-activities-badge]][graph-activities]<br>[![REST][graph-notification-badge]][graph-notification]          | [Relais d’appareils][graph-relay-sample]<br>[Activités/chronologie][graph-activities-sample]<br>[Notifications Graph][graph-notification-sample]

## <a name="project-rome-blog-posts"></a>Billets de blog du projet Rome
* [Annonce du kit SDK Project Rome pour Android et iOS version 1.0 !](https://blogs.windows.com/windowsdeveloper/2019/01/29/announcing-project-rome-sdk-for-android-and-ios-version-1-0/)

* [Expériences multiplateformes avec le projet Rome](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [Going social: Project Rome, Maps, & Social Network Integration](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [Annonce du kit Android SDK du projet Rome](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [Project Rome for Android Update: Now with App Services Support](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [Création d’une application Compagnon de contrôle à distance pour Android avec le projet Rome](https://devblogs.microsoft.com/xamarin/building-remote-control-companion-app-android-project-rome/)

* [New Share Experience in Windows 10 Creators Update](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [Web-to-App Linking with AppUriHandlers](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

* [Project Rome: Driving user engagement across devices, apps and platforms](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#jsUX3bEM6c8SpkIF.97)

* [Création d'applications connectées à l'aide d'UWP et du projet Rome](/archive/msdn-magazine/2018/may/universal-windows-platform-building-connected-apps-with-uwp-and-project-rome)

* [Projet Rome : attirer les utilisateurs sur plusieurs appareils, applications et plateformes](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#hZYfcfYVCFfBv0pS.97)

* [Activation d’expériences de notification orientées utilisateur avec des notifications Microsoft Graph](/graph/notifications-concept-overview)

## <a name="podcasts-and-recordings"></a>Enregistrements et podcasts

* [Projet Rome lors de la conférence Microsoft //Build 2018](https://channel9.msdn.com/Events/Build/2018/BRK2417)

* [Build 2017 : Channel 9 en direct : Q&R sur le projet Rome](https://channel9.msdn.com/Events/Build/2017/C9R11)

* [Build 2017 : MS Dev Show : projet Rome](https://channel9.msdn.com/Shows/msdevshow/Episode-153-Project-Rome-with-Vikas-Bhatia-and-Shawn-Henry)

* [Podcast du MS Dev Show : projet Rome avec Shawn Henry (8 novembre 2016)](https://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

* [Liaison web-application](/windows/uwp/launch-resume/web-to-app-linking)

* [Build 2016 : susciter l'intérêt des utilisateurs avec des applications et des appareils connectés](https://channel9.msdn.com/Events/Build/2016/B831)

* [La minute du développeur : Créer des applications multi-appareils avec Project Rome](https://www.youtube.com/watch?v=7jn-kooKE8U)

* [Bien démarrer avec Microsoft Graph et les notifications](https://www.youtube.com/watch?v=cmpPFhrS8ZA)

## <a name="give-feedback"></a>Envoyer des commentaires

|[Hub de commentaires](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[Nous contacter](mailto:projectrometeam@microsoft.com)|
|-----|-----|