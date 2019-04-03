---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907791"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>Programme d’installation préliminaire pour la plateforme d’appareils connectés

Avant d’implémenter la connectivité à distance, il existe quelques étapes, que vous devrez prendre pour permettre à votre application Android pour se connecter à des appareils distants.

### <a name="sign-in"></a>Connexion

Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour toutes les fonctionnalités du SDK, à l’exception de partage de Nearby API. 

Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).

Ensuite, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/) (si vous n’avez pas un compte de développeur Microsoft, vous devez créer un premier). Vous devez recevoir une chaîne d’ID client pour votre application ; Enregistrer ce paramètre pour une utilisation ultérieure. Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft. Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.

### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.

```Java
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

Ensuite, accédez à l’ou les classes activité où vous souhaitez que les fonctionnalités d’appareils connectés à live. Importer les espaces de noms suivants.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
