---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801794"
---
### <a name="add-the-sdk"></a><span data-ttu-id="020f6-103">Ajouter le kit SDK</span><span class="sxs-lookup"><span data-stu-id="020f6-103">Add the SDK</span></span>

<span data-ttu-id="020f6-104">Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="020f6-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="020f6-105">Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.</span><span class="sxs-lookup"><span data-stu-id="020f6-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="020f6-106">Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API.</span><span class="sxs-lookup"><span data-stu-id="020f6-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="020f6-107">Créez un fichier appelé *proguard-rules.txt* dans le dossier *App* de votre projet, puis collez-y le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="020f6-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="020f6-108">Dans le fichier *AndroidManifest.xml* de votre projet, ajoutez les autorisations suivantes à l’intérieur de l’élément `<manifest>` (si elles ne s’y trouvent pas déjà).</span><span class="sxs-lookup"><span data-stu-id="020f6-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="020f6-109">Cela donne à votre application l’autorisation de se connecter à Internet et d’activer la découverte Bluetooth sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="020f6-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="020f6-110">Les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="020f6-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="020f6-111">Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure.</span><span class="sxs-lookup"><span data-stu-id="020f6-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="020f6-112">Sur les SDK Android version 23 et ultérieures, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="020f6-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="020f6-113">Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="020f6-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="020f6-114">Importez les espaces de noms **connecteddevices**.</span><span class="sxs-lookup"><span data-stu-id="020f6-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="020f6-115">Selon les scénarios que vous implémentez, vous n’avez peut-être pas besoin de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="020f6-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="020f6-116">Vous pouvez être aussi amené à ajouter d’autres espaces natifs Android à mesure que vous progressez.</span><span class="sxs-lookup"><span data-stu-id="020f6-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="020f6-117">Initialiser la Plateforme d’appareils connectés</span><span class="sxs-lookup"><span data-stu-id="020f6-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="020f6-118">Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application.</span><span class="sxs-lookup"><span data-stu-id="020f6-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="020f6-119">Les étapes d’initialisation doivent se produire dans la méthode **OnCreate** ou **onResume** de votre classe principale, car elles constituent une condition préalable pour que d’autres scénarios Appareils connectés puissent se dérouler.</span><span class="sxs-lookup"><span data-stu-id="020f6-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="020f6-120">Vous devez instancier la classe **Platform**.</span><span class="sxs-lookup"><span data-stu-id="020f6-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="020f6-121">Le constructeur **Platform** accepte trois paramètres : **Context** pour l’application, **NotificationProvider** et **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="020f6-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="020f6-122">Le paramètre **NotificationProvider** est nécessaire uniquement pour certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="020f6-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="020f6-123">Il est obligatoire dans le cas d’une utilisation des notifications Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="020f6-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="020f6-124">Laissez-le défini sur `null` pour l’instant et découvrez comment permettre au SDK client de gérer les notifications entrantes centrées sur l’utilisateur via des canaux Push natifs dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="020f6-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="020f6-125">Le paramètre **UserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés.</span><span class="sxs-lookup"><span data-stu-id="020f6-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="020f6-126">Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="020f6-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="020f6-127">Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Android et iOS.</span><span class="sxs-lookup"><span data-stu-id="020f6-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="020f6-128">Ces implémentations, qui se trouvent dans l’[exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), permettent d’obtenir le jeton d’accès OAuth 2.0 et le jeton d’actualisation pour votre application.</span><span class="sxs-lookup"><span data-stu-id="020f6-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="020f6-129">Dans le code ci-dessous, `mSignInHelper` référence un **MSAAccountProvider**, également initialisé plus bas.</span><span class="sxs-lookup"><span data-stu-id="020f6-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="020f6-130">Cette classe fournie implémente l’interface **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="020f6-130">This provided class implements the **UserAccountProvider** interface.</span></span>

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

<span data-ttu-id="020f6-131">À présent, vous pouvez construire une instance de **Platform**.</span><span class="sxs-lookup"><span data-stu-id="020f6-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="020f6-132">Si vous le souhaitez, vous pouvez placer le code suivant dans une classe d’assistance distincte.</span><span class="sxs-lookup"><span data-stu-id="020f6-132">You may wish to put the following code in a separate helper class.</span></span> 

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
<span data-ttu-id="020f6-133">Dans votre classe principale, où `mSignInHelper` est initialisé, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="020f6-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="020f6-134">Nous vous recommandons d’arrêter la plateforme quand votre application quitte le premier plan.</span><span class="sxs-lookup"><span data-stu-id="020f6-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
