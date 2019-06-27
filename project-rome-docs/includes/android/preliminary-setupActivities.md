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
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>Configuration préliminaire pour la Plateforme d’appareils connectés

Avant d’implémenter la connectivité à distance, vous devez effectuer plusieurs étapes pour permettre à votre application Android de se connecter à des appareils distants.

### <a name="sign-in"></a>Connexion

L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour toutes les fonctionnalités du SDK, à l’exception des API de partage de proximité. 

Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).

Vous devez ensuite inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas de compte développeur Microsoft, vous devez d’abord en créer un). Vous devez recevoir une chaîne d’ID client pour votre application ; enregistrez-la pour plus tard. Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft. Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.

### <a name="add-the-sdk"></a>Ajouter le kit SDK

Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.

```Java
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
> Les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés. Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure. Sur les kits SDK Android version 23 et ultérieure, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.

Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés. Importez les espaces de noms suivants.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
