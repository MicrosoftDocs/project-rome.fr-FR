---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b2d1d764c4aae562a1fcafdb490db5a14522cda6
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755811"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="83780-103">Programme d’installation préliminaire pour la plateforme de périphériques connectés et les Notifications</span><span class="sxs-lookup"><span data-stu-id="83780-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="83780-104">Avant d’implémenter la connectivité à distance, il existe quelques étapes, que vous devrez suivre pour permettre à votre application Android à connecter des appareils à distance, ainsi que d’envoyer et recevoir des notifications.</span><span class="sxs-lookup"><span data-stu-id="83780-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="83780-105">Inscrire votre application</span><span class="sxs-lookup"><span data-stu-id="83780-105">Register your app</span></span>

<span data-ttu-id="83780-106">Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour presque toutes les fonctionnalités de Project Rome SDK (l’exception en cours de l’API de partage à proximité).</span><span class="sxs-lookup"><span data-stu-id="83780-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="83780-107">Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="83780-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="83780-108">Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.</span><span class="sxs-lookup"><span data-stu-id="83780-108">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="83780-109">À l’aide de votre méthode d’authentification choisi, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="83780-109">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="83780-110">Si vous n’avez pas un compte de développeur Microsoft, vous devrez créer un.</span><span class="sxs-lookup"><span data-stu-id="83780-110">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="83780-111">Lorsque vous inscrivez une application à l’aide d’un compte de service administré, vous devez recevoir une chaîne d’ID de client.</span><span class="sxs-lookup"><span data-stu-id="83780-111">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="83780-112">Enregistrer ce paramètre pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="83780-112">Save this for later.</span></span> <span data-ttu-id="83780-113">Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="83780-113">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="83780-114">Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.</span><span class="sxs-lookup"><span data-stu-id="83780-114">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="83780-115">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="83780-115">Add the SDK</span></span>

<span data-ttu-id="83780-116">Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="83780-116">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="83780-117">Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="83780-117">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="83780-118">Dans votre projet *AndroidManifest.xml* , ajoutez les autorisations suivantes à l’intérieur de la `<manifest>` (s’ils ne figurent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="83780-118">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="83780-119">Ainsi, votre application l’autorisation pour se connecter à Internet et pour activer la découverte de Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="83780-119">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="83780-120">Notez que les autorisations liées à Bluetooth sont uniquement nécessaires pour l’utilisation de découverte de Bluetooth ; ils ne sont pas nécessaires pour les autres fonctionnalités de la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="83780-120">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="83780-121">En outre, `ACCESS_COARSE_LOCATION` est uniquement requis sur Android SDK 21 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="83780-121">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="83780-122">Sur Android SDK 23 et versions ultérieures, le développeur doit également l’utilisateur pour accorder l’accès à l’emplacement lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="83780-122">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="83780-123">Ensuite, accédez à l’ou les classes activité où vous souhaitez que les fonctionnalités d’appareils connectés à live.</span><span class="sxs-lookup"><span data-stu-id="83780-123">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="83780-124">Importer les packages suivants.</span><span class="sxs-lookup"><span data-stu-id="83780-124">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
