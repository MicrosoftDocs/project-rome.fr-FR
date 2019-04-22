---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909291"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="90b70-103">Inscrire votre application pour les notifications push</span><span class="sxs-lookup"><span data-stu-id="90b70-103">Register your app for push notifications</span></span>

<span data-ttu-id="90b70-104">Inscrire votre application auprès d’Apple pour [Apns](https://developer.apple.com/notifications/) prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="90b70-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="90b70-105">Veillez à prenez note de l’expéditeur clé ID et le serveur que vous recevez comme vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="90b70-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="90b70-106">Une fois inscrit, vous devez associer les fonctionnalités de notification push avec la plateforme d’appareils connectés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="90b70-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="90b70-107">Inscrire votre application dans Microsoft Windows Dev Center pour des expériences entre les périphériques</span><span class="sxs-lookup"><span data-stu-id="90b70-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="90b70-108">Cette étape est uniquement nécessaire si vous souhaitez utiliser les fonctionnalités de Project Rome pour accéder aux données à partir d’ou effectuer des demandes des appareils non Windows.</span><span class="sxs-lookup"><span data-stu-id="90b70-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="90b70-109">Si vous ciblez uniquement les appareils Windows, il est inutile d’effectuer cette étape.</span><span class="sxs-lookup"><span data-stu-id="90b70-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="90b70-110">Inscrire votre application pour le [fonctionnalité inter-périphériques expériences du tableau de bord du développeur Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="90b70-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="90b70-111">Il s’agit d’une autre procédure à partir du compte de service administré et AAD inscription d’application ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="90b70-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="90b70-112">L’objectif principal de ce processus consiste à mapper les identités d’application spécifiques de plateforme avec une identité d’application multiplateforme qui est reconnu par la plateforme de périphériques connectés.</span><span class="sxs-lookup"><span data-stu-id="90b70-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="90b70-113">Cette étape active également l’envoi de notifications à l’aide de correspondant pour les plateformes mobiles que votre application utilise les services de notification push natif.</span><span class="sxs-lookup"><span data-stu-id="90b70-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="90b70-114">Pour iOS, il active les notifications à envoyer aux points de terminaison iOS app via APNS, Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="90b70-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="90b70-115">Accédez au tableau de bord de centre de développement, accédez à des expériences entre les périphériques à partir du volet de navigation de gauche et sélectionnez la configuration d’une nouvelle application entre les périphériques.</span><span class="sxs-lookup"><span data-stu-id="90b70-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="90b70-116">![Tableau de bord de centre de développement, des expériences entre les périphériques](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="90b70-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="90b70-117">Le processus d’intégration de centre de développement requièrent les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="90b70-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="90b70-118">Sélectionnez les plateformes prises en charge : sélectionnez les plateformes où votre application aura une présence et être activée pour des expériences entre les périphériques.</span><span class="sxs-lookup"><span data-stu-id="90b70-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="90b70-119">Dans le cas d’intégration de Notifications de graphique, vous pouvez sélectionner à partir de Windows, Android ou iOS, en fonction des plateformes que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="90b70-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![Expériences inter-périphériques – plateformes prises en charge](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="90b70-121">Fournir l’ID d’application – permet de fournir des ID d’application pour chaque plateforme que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="90b70-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="90b70-122">Pour les applications iOS, ceci est le nom du package affecté à votre application lorsque vous avez créé le projet.</span><span class="sxs-lookup"><span data-stu-id="90b70-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="90b70-123">Notez que vous pouvez ajouter des ID différents (jusqu'à dix) par plateforme, c'est-à-dire au cas où vous avez plusieurs versions de la même application, ou même différentes applications, que vous souhaitez être en mesure de recevoir les mêmes notifications envoyées par votre serveur d’applications ciblant le même utilisateur.</span><span class="sxs-lookup"><span data-stu-id="90b70-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![Expériences inter-périphériques – ID d’application](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="90b70-125">Fournir ou sélectionnez l’ID d’application à partir des inscriptions d’application MSA et/ou AAD obtenues dans les cours MSA/AAD application d’enregistrement des étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="90b70-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![Expériences inter-périphériques – MSA et les inscriptions d’application AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="90b70-127">Fournissez vos informations d’identification pour les plateformes de notification native pertinentes pour votre application (WNS pour Windows, FCM pour Android ou APNS pour iOS) pour activer la remise des notifications à partir de votre serveur d’applications lorsque vous publiez des notifications ciblées de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="90b70-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![Expériences inter-périphériques – informations d’identification Push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="90b70-129">Enfin, vérifiez votre domaine d’application d’entre les périphériques pour vous assurer que votre application est propriétaire du domaine et pouvez l’utiliser comme une identité entre les périphériques pour votre application.</span><span class="sxs-lookup"><span data-stu-id="90b70-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![Expériences inter-périphériques – vérification du domaine](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
