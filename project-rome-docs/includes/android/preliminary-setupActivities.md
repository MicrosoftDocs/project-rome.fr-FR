---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801661"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="f1435-103">Programme d’installation préliminaire pour la plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="f1435-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="f1435-104">Avant d’implémenter la connectivité à distance, il existe quelques étapes, que vous devrez prendre pour permettre à votre application Android pour se connecter à des appareils distants.</span><span class="sxs-lookup"><span data-stu-id="f1435-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="f1435-105">Connexion</span><span class="sxs-lookup"><span data-stu-id="f1435-105">Sign-in</span></span>

<span data-ttu-id="f1435-106">Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour toutes les fonctionnalités du SDK, à l’exception de partage de Nearby API.</span><span class="sxs-lookup"><span data-stu-id="f1435-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="f1435-107">Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="f1435-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="f1435-108">Ensuite, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas un compte de développeur Microsoft, vous devez créer un premier).</span><span class="sxs-lookup"><span data-stu-id="f1435-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="f1435-109">Vous devez recevoir une chaîne d’ID client pour votre application ; Enregistrer ce paramètre pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f1435-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="f1435-110">Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f1435-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="f1435-111">Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.</span><span class="sxs-lookup"><span data-stu-id="f1435-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="f1435-112">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="f1435-112">Add the SDK</span></span>

<span data-ttu-id="f1435-113">Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="f1435-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="f1435-114">Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="f1435-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="f1435-115">Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API.</span><span class="sxs-lookup"><span data-stu-id="f1435-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="f1435-116">Créez un fichier appelé *proguard rules.txt* dans le *application* dossier de votre projet, puis collez le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="f1435-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="f1435-117">Dans votre projet *AndroidManifest.xml* , ajoutez les autorisations suivantes à l’intérieur de la `<manifest>` (s’ils ne figurent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="f1435-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="f1435-118">Ainsi, votre application l’autorisation pour se connecter à Internet et pour activer la découverte de Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="f1435-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="f1435-119">Les autorisations liées à Bluetooth sont uniquement nécessaires pour à l’aide de la découverte de Bluetooth ; ils ne sont pas nécessaires pour les autres fonctionnalités de la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="f1435-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="f1435-120">En outre, `ACCESS_COARSE_LOCATION` est uniquement requis sur Android SDK 21 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1435-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="f1435-121">Sur Android SDK 23 et versions ultérieures, le développeur doit également l’utilisateur pour accorder l’accès à l’emplacement lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f1435-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="f1435-122">Ensuite, accédez à l’ou les classes activité où vous souhaitez que les fonctionnalités d’appareils connectés à live.</span><span class="sxs-lookup"><span data-stu-id="f1435-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="f1435-123">Importer les espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="f1435-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
