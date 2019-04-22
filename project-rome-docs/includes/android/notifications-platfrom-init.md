---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801794"
---
### <a name="add-the-sdk"></a><span data-ttu-id="e191c-103">Ajoutez le kit SDK</span><span class="sxs-lookup"><span data-stu-id="e191c-103">Add the SDK</span></span>

<span data-ttu-id="e191c-104">Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="e191c-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="e191c-105">Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="e191c-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="e191c-106">Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API.</span><span class="sxs-lookup"><span data-stu-id="e191c-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="e191c-107">Créez un fichier appelé *proguard rules.txt* dans le *application* dossier de votre projet, puis collez le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="e191c-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="e191c-108">Dans votre projet *AndroidManifest.xml* , ajoutez les autorisations suivantes à l’intérieur de la `<manifest>` (s’ils ne figurent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="e191c-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="e191c-109">Ainsi, votre application l’autorisation pour se connecter à Internet et pour activer la découverte de Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="e191c-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="e191c-110">Les autorisations liées à Bluetooth sont uniquement nécessaires pour à l’aide de la découverte de Bluetooth ; ils ne sont pas nécessaires pour les autres fonctionnalités de la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="e191c-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="e191c-111">En outre, `ACCESS_COARSE_LOCATION` est uniquement requis sur Android SDK 21 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e191c-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="e191c-112">Sur Android SDK 23 et versions ultérieures, le développeur doit également l’utilisateur pour accorder l’accès à l’emplacement lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e191c-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="e191c-113">Ensuite, accédez à l’ou les classes activité où vous souhaitez ajouter les fonctionnalités des appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="e191c-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="e191c-114">Importer le **connecteddevices** espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="e191c-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="e191c-115">Selon les scénarios que vous implémentez, vous nombreuses pas besoin de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="e191c-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="e191c-116">Vous devez également ajouter d’autres espaces de noms Android natives en tant que vous progressez.</span><span class="sxs-lookup"><span data-stu-id="e191c-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="e191c-117">Initialiser la plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="e191c-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="e191c-118">Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="e191c-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="e191c-119">Les étapes d’initialisation doivent se produire dans votre classe principale **onCreate** ou **onResume** (méthode), car ils sont requis avant d’autres scénarios d’appareils connectés peuvent avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="e191c-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="e191c-120">Vous devez instancier le **plateforme** classe.</span><span class="sxs-lookup"><span data-stu-id="e191c-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="e191c-121">Le **plateforme** constructeur accepte trois paramètres : le **contexte** pour l’application, un **NotificationProvider**et un **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="e191c-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="e191c-122">Le **NotificationProvider** paramètre est uniquement nécessaire pour certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="e191c-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="e191c-123">En cas d’utilisation de notification Microsoft Graph, il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e191c-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="e191c-124">Laissez ce champ `null` pour l’instant et découvrez comment activer le logiciel (SDK) pour gérer les notifications entrantes centrés sur l’utilisateur via des canaux de push natif dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="e191c-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="e191c-125">Le **UserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="e191c-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="e191c-126">Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée.</span><span class="sxs-lookup"><span data-stu-id="e191c-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="e191c-127">Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous avons fourni des implémentations de fournisseur pour Android et iOS de compte.</span><span class="sxs-lookup"><span data-stu-id="e191c-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="e191c-128">Ces implémentations, trouvé dans le [exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), peut être utilisé pour obtenir le jeton d’accès OAuth 2.0 et actualiser le jeton pour votre application.</span><span class="sxs-lookup"><span data-stu-id="e191c-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="e191c-129">Dans le code ci-dessous, `mSignInHelper` références un **MSAAccountProvider**, il est également initialisée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e191c-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="e191c-130">Cette classe implémente condition fournie le **UserAccountProvider** interface.</span><span class="sxs-lookup"><span data-stu-id="e191c-130">This provided class implements the **UserAccountProvider** interface.</span></span>

```java
private MSAAccountProvider mSignInHelper;

// ...

// Create sign-in helper from helper lib, which does user account and access token management for us
// Takes two parameters: a client id for msa, and the Context
mSignInHelper = new MSAAccountProvider(Secrets.MSA_CLIENT_ID, getContext());

// add an event listener, which changes the button text when account state changes
mSignInHelper.addUserAccountChangedListener(new EventListener<UserAccountProvider, Void>() {
    @Override
    public void onEvent(UserAccountProvider provider, Void aVoid){
        if (mSignInHelper.isSignedIn()) {
            // update the UI indicating a user is signed in.
        }
        else
        {
            // update the UI indicating a user is not signed in.
        }
    }
});
```

<span data-ttu-id="e191c-131">Maintenant que vous pouvez construire un **plateforme** instance.</span><span class="sxs-lookup"><span data-stu-id="e191c-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="e191c-132">Vous pouvez souhaiter placer le code suivant dans une classe d’assistance distincte.</span><span class="sxs-lookup"><span data-stu-id="e191c-132">You may wish to put the following code in a separate helper class.</span></span> 

```java
// Platform helper class:

private static Platform sPlatform;

//...

// This is the main Platform-generating method
public static synchronized Platform getOrCreatePlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    // check whether the local platform variable is already initialized.
    Platform platform = getPlatform();

    if (platform == null) {
        // if it is not initialized, do so:
        platform = createPlatform(context, accountProvider, notificationProvider);
    }
    return platform;
}

// gets the local platform variable
public static synchronized Platform getPlatform() {
        return sPlatform;
}

// creates and returns a new Platform instance
public static synchronized Platform createPlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    sPlatform = new Platform(context, accountProvider, notificationProvider);
    return sPlatform;
}
```
<span data-ttu-id="e191c-133">Dans votre classe principale, où `mSignInHelper` est initialisé, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e191c-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="e191c-134">Vous devez arrêter la plateforme quand votre application s’arrête au premier plan.</span><span class="sxs-lookup"><span data-stu-id="e191c-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
