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
### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API. Créez un fichier appelé *proguard rules.txt* dans le *application* dossier de votre projet, puis collez le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).

Dans votre projet *AndroidManifest.xml* , ajoutez les autorisations suivantes à l’intérieur de la `<manifest>` (s’ils ne figurent pas déjà). Ainsi, votre application l’autorisation pour se connecter à Internet et pour activer la découverte de Bluetooth sur votre appareil.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Les autorisations liées à Bluetooth sont uniquement nécessaires pour à l’aide de la découverte de Bluetooth ; ils ne sont pas nécessaires pour les autres fonctionnalités de la plateforme d’appareils connectés. En outre, `ACCESS_COARSE_LOCATION` est uniquement requis sur Android SDK 21 et versions ultérieures. Sur Android SDK 23 et versions ultérieures, le développeur doit également l’utilisateur pour accorder l’accès à l’emplacement lors de l’exécution.

Ensuite, accédez à l’ou les classes activité où vous souhaitez ajouter les fonctionnalités des appareils connectés. Importer le **connecteddevices** espaces de noms.

```java
import com.microsoft.connecteddevices.*;
```

Selon les scénarios que vous implémentez, vous nombreuses pas besoin de tous les espaces de noms. Vous devez également ajouter d’autres espaces de noms Android natives en tant que vous progressez.

### <a name="initialize-the-connected-devices-platform"></a>Initialiser la plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités des appareils connectés, la plateforme doit être initialisée au sein de votre application. Les étapes d’initialisation doivent se produire dans votre classe principale **onCreate** ou **onResume** (méthode), car ils sont requis avant d’autres scénarios d’appareils connectés peuvent avoir lieu. 

Vous devez instancier le **plateforme** classe. Le **plateforme** constructeur accepte trois paramètres : le **contexte** pour l’application, un **NotificationProvider**et un **UserAccountProvider**.

Le **NotificationProvider** paramètre est uniquement nécessaire pour certains scénarios. En cas d’utilisation de notification Microsoft Graph, il est nécessaire. Laissez ce champ `null` pour l’instant et découvrez comment activer le logiciel (SDK) pour gérer les notifications entrantes centrés sur l’utilisateur via des canaux de push natif dans la section suivante.

Le **UserAccountProvider** est nécessaire pour fournir un jeton d’accès OAuth 2.0 pour l’accès de l’utilisateur actuel à la plateforme d’appareils connectés. Elle sera appelée la première fois que l’application est exécutée et le jeton d’actualisation lors de l’expiration d’une plateforme gérée. 

Afin d’aider les développeurs à intégrer avec la plateforme plus facilement, nous avons fourni des implémentations de fournisseur pour Android et iOS de compte. Ces implémentations, trouvé dans le [exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), peut être utilisé pour obtenir le jeton d’accès OAuth 2.0 et actualiser le jeton pour votre application.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

Dans le code ci-dessous, `mSignInHelper` références un **MSAAccountProvider**, il est également initialisée ci-dessous. Cette classe implémente condition fournie le **UserAccountProvider** interface.

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

Maintenant que vous pouvez construire un **plateforme** instance. Vous pouvez souhaiter placer le code suivant dans une classe d’assistance distincte. 

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
Dans votre classe principale, où `mSignInHelper` est initialisé, ajoutez le code suivant.

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

Vous devez arrêter la plateforme quand votre application s’arrête au premier plan.

```Java
mPlatform.shutdownAsync();
```
