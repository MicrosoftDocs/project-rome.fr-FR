---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b979c0b7891aaa6ce5c422d8349809b429a47201
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755748"
---
### <a name="register-your-app"></a><span data-ttu-id="61b08-103">Inscrire votre application</span><span class="sxs-lookup"><span data-stu-id="61b08-103">Register your app</span></span>

<span data-ttu-id="61b08-104">Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour presque toutes les fonctionnalités de Project Rome SDK (l’exception en cours de l’API de partage à proximité).</span><span class="sxs-lookup"><span data-stu-id="61b08-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="61b08-105">Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="61b08-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="61b08-106">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.</span><span class="sxs-lookup"><span data-stu-id="61b08-106">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="61b08-107">À l’aide de votre méthode d’authentification choisi, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="61b08-107">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="61b08-108">Si vous n’avez pas un compte de développeur Microsoft, vous devrez créer un.</span><span class="sxs-lookup"><span data-stu-id="61b08-108">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="61b08-109">Lorsque vous inscrivez une application à l’aide d’un compte de service administré, vous devez recevoir une chaîne d’ID de client.</span><span class="sxs-lookup"><span data-stu-id="61b08-109">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="61b08-110">Enregistrer ce paramètre pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="61b08-110">Save this for later.</span></span> <span data-ttu-id="61b08-111">Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="61b08-111">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="61b08-112">Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.</span><span class="sxs-lookup"><span data-stu-id="61b08-112">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="61b08-113">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="61b08-113">Add the SDK</span></span>

<span data-ttu-id="61b08-114">Le plus simple pour ajouter la plateforme d’appareils connectés à votre application iOS consiste à l’aide de la [CocoaPods](https://cocoapods.org/) Gestionnaire de dépendances.</span><span class="sxs-lookup"><span data-stu-id="61b08-114">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="61b08-115">Accédez à votre projet iOS *Podfile* et insérez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="61b08-115">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> <span data-ttu-id="61b08-116">Afin de consommer CocoaPod, vous devez utiliser le _.xcworkspace_ fichier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="61b08-116">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>
