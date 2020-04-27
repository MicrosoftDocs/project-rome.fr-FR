---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b979c0b7891aaa6ce5c422d8349809b429a47201
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755748"
---
### <a name="register-your-app"></a><span data-ttu-id="78c26-103">Inscrire votre application</span><span class="sxs-lookup"><span data-stu-id="78c26-103">Register your app</span></span>

<span data-ttu-id="78c26-104">L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour pratiquement toutes les fonctionnalités du SDK du projet Rome (les API de partage de proximité étant l’exception).</span><span class="sxs-lookup"><span data-stu-id="78c26-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="78c26-105">Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="78c26-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="78c26-106">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.</span><span class="sxs-lookup"><span data-stu-id="78c26-106">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="78c26-107">En utilisant la méthode d’authentification de votre choix, vous devez inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="78c26-107">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="78c26-108">Si vous n’avez pas de compte de développeur Microsoft, vous devrez en créer un.</span><span class="sxs-lookup"><span data-stu-id="78c26-108">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="78c26-109">Quand vous inscrivez une application à l’aide d’un compte MSA, vous devez recevoir une chaîne d’ID client.</span><span class="sxs-lookup"><span data-stu-id="78c26-109">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="78c26-110">Enregistrez-la pour plus tard.</span><span class="sxs-lookup"><span data-stu-id="78c26-110">Save this for later.</span></span> <span data-ttu-id="78c26-111">Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78c26-111">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="78c26-112">Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.</span><span class="sxs-lookup"><span data-stu-id="78c26-112">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="78c26-113">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="78c26-113">Add the SDK</span></span>

<span data-ttu-id="78c26-114">Le moyen le plus simple d’ajouter la Plateforme d’appareils connectés à votre application iOS est d’utiliser le gestionnaire de dépendances [CocoaPods](https://cocoapods.org/).</span><span class="sxs-lookup"><span data-stu-id="78c26-114">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="78c26-115">Accédez au fichier *Podfile* de votre projet iOS et insérez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="78c26-115">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="78c26-116">Pour utiliser CocoaPod, vous devez utiliser le fichier _.xcworkspace_ dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="78c26-116">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>
