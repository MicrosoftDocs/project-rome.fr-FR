---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801661"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="cc642-103">Configuration préliminaire pour la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="cc642-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="cc642-104">Avant d’implémenter la connectivité à distance, vous devez effectuer plusieurs étapes pour permettre à votre application Android de se connecter à des appareils distants.</span><span class="sxs-lookup"><span data-stu-id="cc642-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="cc642-105">Connexion</span><span class="sxs-lookup"><span data-stu-id="cc642-105">Sign-in</span></span>

<span data-ttu-id="cc642-106">L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour toutes les fonctionnalités du SDK, à l’exception des API de partage de proximité.</span><span class="sxs-lookup"><span data-stu-id="cc642-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="cc642-107">Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="cc642-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="cc642-108">Vous devez ensuite inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas de compte développeur Microsoft, vous devez d’abord en créer un).</span><span class="sxs-lookup"><span data-stu-id="cc642-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="cc642-109">Vous devez recevoir une chaîne d’ID client pour votre application ; enregistrez-la pour plus tard.</span><span class="sxs-lookup"><span data-stu-id="cc642-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="cc642-110">Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cc642-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="cc642-111">Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.</span><span class="sxs-lookup"><span data-stu-id="cc642-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="cc642-112">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="cc642-112">Add the SDK</span></span>

<span data-ttu-id="cc642-113">Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="cc642-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="cc642-114">Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.</span><span class="sxs-lookup"><span data-stu-id="cc642-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="cc642-115">Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API.</span><span class="sxs-lookup"><span data-stu-id="cc642-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="cc642-116">Créez un fichier appelé *proguard-rules.txt* dans le dossier *App* de votre projet, puis collez-y le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="cc642-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="cc642-117">Dans le fichier *AndroidManifest.xml* de votre projet, ajoutez les autorisations suivantes à l’intérieur de l’élément `<manifest>` (si elles ne s’y trouvent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="cc642-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="cc642-118">Cela donne à votre application l’autorisation de se connecter à Internet et d’activer la découverte Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="cc642-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="cc642-119">Les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="cc642-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="cc642-120">Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cc642-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="cc642-121">Sur les kits SDK Android version 23 et ultérieure, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc642-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="cc642-122">Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="cc642-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="cc642-123">Importez les espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="cc642-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
