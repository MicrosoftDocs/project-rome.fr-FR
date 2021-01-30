---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: aa784c8892e37226602632e6329c15ab483521b3
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901552"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="2a652-103">Configuration préliminaire pour la Plateforme d’appareils connectés et les notifications</span><span class="sxs-lookup"><span data-stu-id="2a652-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="2a652-104">Avant d’implémenter la connectivité à distance, vous devez effectuer plusieurs étapes pour permettre à votre application Android de se connecter à des appareils distants mais aussi d’envoyer et recevoir des notifications.</span><span class="sxs-lookup"><span data-stu-id="2a652-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="2a652-105">Inscrire votre application</span><span class="sxs-lookup"><span data-stu-id="2a652-105">Register your app</span></span>

<span data-ttu-id="2a652-106">L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour pratiquement toutes les fonctionnalités du SDK du projet Rome (les API de partage de proximité étant l’exception).</span><span class="sxs-lookup"><span data-stu-id="2a652-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="2a652-107">Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="2a652-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="2a652-108">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.</span><span class="sxs-lookup"><span data-stu-id="2a652-108">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="2a652-109">En utilisant la méthode d’authentification de votre choix, vous devez inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="2a652-109">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="2a652-110">Si vous n’avez pas de compte de développeur Microsoft, vous devrez en créer un.</span><span class="sxs-lookup"><span data-stu-id="2a652-110">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="2a652-111">Quand vous inscrivez une application à l’aide d’un compte MSA, vous devez recevoir une chaîne d’ID client.</span><span class="sxs-lookup"><span data-stu-id="2a652-111">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="2a652-112">Enregistrez-la pour plus tard.</span><span class="sxs-lookup"><span data-stu-id="2a652-112">Save this for later.</span></span> <span data-ttu-id="2a652-113">Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a652-113">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="2a652-114">Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.</span><span class="sxs-lookup"><span data-stu-id="2a652-114">If you're using AAD, see [Azure Active Directory Authentication Libraries](/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="2a652-115">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="2a652-115">Add the SDK</span></span>

<span data-ttu-id="2a652-116">Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="2a652-116">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="2a652-117">Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.</span><span class="sxs-lookup"><span data-stu-id="2a652-117">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="2a652-118">Dans le fichier *AndroidManifest.xml* de votre projet, ajoutez les autorisations suivantes à l’intérieur de l’élément `<manifest>` (si elles ne s’y trouvent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="2a652-118">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="2a652-119">Cela donne à votre application l’autorisation de se connecter à Internet et d’activer la découverte Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="2a652-119">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="2a652-120">Notez que les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="2a652-120">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="2a652-121">Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2a652-121">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="2a652-122">Sur les SDK Android version 23 et ultérieures, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2a652-122">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="2a652-123">Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="2a652-123">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="2a652-124">Importez les packages suivants.</span><span class="sxs-lookup"><span data-stu-id="2a652-124">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```