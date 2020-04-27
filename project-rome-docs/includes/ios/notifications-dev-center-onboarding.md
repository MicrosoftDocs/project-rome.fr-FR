---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909291"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="508af-103">Inscrire votre application aux notifications Push</span><span class="sxs-lookup"><span data-stu-id="508af-103">Register your app for push notifications</span></span>

<span data-ttu-id="508af-104">Pour assurer une prise en charge d’[Apple Push Notification](https://developer.apple.com/notifications/), inscrivez votre application auprès d’Apple.</span><span class="sxs-lookup"><span data-stu-id="508af-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="508af-105">Veillez à noter l’ID d’expéditeur et la clé serveur que vous recevez, car vous en aurez besoin par la suite.</span><span class="sxs-lookup"><span data-stu-id="508af-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="508af-106">Une fois l’inscription effectuée, vous devez associer la fonctionnalité de notification Push à la Plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="508af-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="508af-107">Inscrire votre application dans le Centre de développement Microsoft pour des expériences inter-appareils</span><span class="sxs-lookup"><span data-stu-id="508af-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="508af-108">Cette étape n’est nécessaire que si vous souhaitez utiliser les fonctionnalités du projet Rome pour accéder à des données ou effectuer des demandes à partir d’appareils non Windows.</span><span class="sxs-lookup"><span data-stu-id="508af-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="508af-109">Si vous ciblez uniquement des appareils Windows, vous n’avez pas besoin d’effectuer cette étape.</span><span class="sxs-lookup"><span data-stu-id="508af-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="508af-110">Inscrivez votre application pour la [fonctionnalité Expériences inter-appareils du tableau de bord Développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="508af-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="508af-111">Il s’agit d’une procédure différente de celle visant à inscrire une application MSA et AAD décrite plus haut.</span><span class="sxs-lookup"><span data-stu-id="508af-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="508af-112">L’objectif principal de ce processus est de mapper les identités d’application d’une plateforme spécifique à une identité d’application multiplateforme qui est reconnue par la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="508af-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="508af-113">Cette étape permettra aussi l’envoi de notifications à l’aide des services de notification Push natifs correspondant aux plateformes mobiles utilises par votre application.</span><span class="sxs-lookup"><span data-stu-id="508af-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="508af-114">Dans le cas d’iOS, elle permet l’envoi de notifications aux points de terminaison d’application iOS via APNS (Apple Push Notification Service).</span><span class="sxs-lookup"><span data-stu-id="508af-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="508af-115">Dans le tableau de bord du Centre de développement, accédez à Expériences inter-appareils dans le volet de navigation de gauche, puis choisissez de configurer une nouvelle application inter-appareils.</span><span class="sxs-lookup"><span data-stu-id="508af-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="508af-116">![Tableau de bord du Centre de développement – Expériences inter-appareils](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="508af-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="508af-117">Le processus d’intégration du Centre de développement comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="508af-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="508af-118">Sélectionnez les plateformes prises en charge, à savoir celles sur lesquelles votre application sera présente et compatible avec les expériences inter-appareils.</span><span class="sxs-lookup"><span data-stu-id="508af-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="508af-119">Dans le cas de l’intégration des notifications Graph, vous pouvez sélectionner Windows, Android et/ou iOS, selon les plateformes que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="508af-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![Expériences inter-appareils – Plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="508af-121">Fournissez des ID d’application pour chaque plateforme utilisée.</span><span class="sxs-lookup"><span data-stu-id="508af-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="508af-122">Pour les applications iOS, il s’agit du nom de package que vous avez attribué à votre application au moment de créer le projet.</span><span class="sxs-lookup"><span data-stu-id="508af-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="508af-123">Notez que vous pouvez ajouter des ID différents (jusqu’à dix) par plateforme. Cela peut être utile si vous disposez de plusieurs versions d’une même application, voire différentes applications, et que vous souhaitez qu’elles puissent recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur.</span><span class="sxs-lookup"><span data-stu-id="508af-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![Expériences inter-appareils – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="508af-125">Fournissez ou sélectionnez les ID d’application des inscriptions d’application MSA et/ou AAD obtenus aux étapes d’inscription d’application MSA/AAD précédentes.</span><span class="sxs-lookup"><span data-stu-id="508af-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![Expériences inter-périphériques – Inscriptions d’application MSA et AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="508af-127">Fournissez vos informations d’identification pour les plateformes de notification natives correspondant à votre application (c’est-à-dire, WNS pour Windows, FCM pour Android et/ou APNS pour iOS) pour permettre à votre serveur d’applications de transmettre les notifications ciblant l’utilisateur, dans le cas où vous en publiez.</span><span class="sxs-lookup"><span data-stu-id="508af-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![Expériences inter-périphériques – Informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="508af-129">Enfin, vérifiez votre domaine d’application inter-appareils pour être certain que votre application en est propriétaire et que vous pouvez l’utiliser comme identité inter-appareils pour votre application.</span><span class="sxs-lookup"><span data-stu-id="508af-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![Expériences inter-appareils – Vérification de domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
