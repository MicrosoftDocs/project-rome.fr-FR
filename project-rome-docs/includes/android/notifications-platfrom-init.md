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
### <a name="add-the-sdk"></a>Ajouter le kit SDK

Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

Si vous souhaitez utiliser ProGuard dans votre application, ajoutez les règles ProGuard pour ces nouvelles API. Créez un fichier appelé *proguard-rules.txt* dans le dossier *App* de votre projet, puis collez-y le contenu de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).

Dans le fichier *AndroidManifest.xml* de votre projet, ajoutez les autorisations suivantes à l’intérieur de l’élément `<manifest>` (si elles ne s’y trouvent pas déjà). Cela donne à votre application l’autorisation de se connecter à Internet et d’activer la découverte Bluetooth sur votre appareil.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés. Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure. Sur les SDK Android version 23 et ultérieures, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.

Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés. Importez les espaces de noms **connecteddevices**.

```java
import com.microsoft.connecteddevices.*;
```

Selon les scénarios que vous implémentez, vous n’avez peut-être pas besoin de tous les espaces de noms. Vous pouvez être aussi amené à ajouter d’autres espaces natifs Android à mesure que vous progressez.

### <a name="initialize-the-connected-devices-platform"></a>Initialiser la Plateforme d’appareils connectés

Avant de pouvoir utiliser les fonctionnalités d’Appareils connectés, la plateforme doit être initialisée au sein de votre application. Les étapes d’initialisation doivent se produire dans la méthode **OnCreate** ou **onResume** de votre classe principale, car elles constituent une condition préalable pour que d’autres scénarios Appareils connectés puissent se dérouler. 

Vous devez instancier la classe **Platform**. Le constructeur **Platform** accepte trois paramètres : **Context** pour l’application, **NotificationProvider** et **UserAccountProvider**.

Le paramètre **NotificationProvider** est nécessaire uniquement pour certains scénarios. Il est obligatoire dans le cas d’une utilisation des notifications Microsoft Graph. Laissez-le défini sur `null` pour l’instant et découvrez comment permettre au SDK client de gérer les notifications entrantes centrées sur l’utilisateur via des canaux Push natifs dans la section suivante.

Le paramètre **UserAccountProvider** est nécessaire pour remettre un jeton d’accès OAuth 2.0 permettant à l’utilisateur actif d’accéder à la Plateforme d’appareils connectés. Il est appelé à la première exécution de l’application et à l’expiration d’un jeton d’actualisation géré par la plateforme. 

Pour faciliter l’intégration des développeurs dans la plateforme, nous avons fourni des implémentations de fournisseur de compte pour Android et iOS. Ces implémentations, qui se trouvent dans l’[exemple de fournisseur d’authentification](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), permettent d’obtenir le jeton d’accès OAuth 2.0 et le jeton d’actualisation pour votre application.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

Dans le code ci-dessous, `mSignInHelper` référence un **MSAAccountProvider**, également initialisé plus bas. Cette classe fournie implémente l’interface **UserAccountProvider**.

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

À présent, vous pouvez construire une instance de **Platform**. Si vous le souhaitez, vous pouvez placer le code suivant dans une classe d’assistance distincte. 

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

Nous vous recommandons d’arrêter la plateforme quand votre application quitte le premier plan.

```Java
mPlatform.shutdownAsync();
```
