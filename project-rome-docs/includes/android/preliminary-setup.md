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
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>Configuration préliminaire pour la Plateforme d’appareils connectés et les notifications

Avant d’implémenter la connectivité à distance, vous devez effectuer plusieurs étapes pour permettre à votre application Android de se connecter à des appareils distants mais aussi d’envoyer et recevoir des notifications.

### <a name="register-your-app"></a>Inscrire votre application

L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour pratiquement toutes les fonctionnalités du SDK du projet Rome (les API de partage de proximité étant l’exception). Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.

En utilisant la méthode d’authentification de votre choix, vous devez inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/). Si vous n’avez pas de compte de développeur Microsoft, vous devrez en créer un.

Quand vous inscrivez une application à l’aide d’un compte MSA, vous devez recevoir une chaîne d’ID client. Enregistrez-la pour plus tard. Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft. Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.

### <a name="add-the-sdk"></a>Ajouter le kit SDK

Insérez les références de référentiel ci-dessous dans le fichier *build.gradle* à la racine de votre projet.

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
Insérez ensuite la dépendance suivante dans le fichier _build.gradle_ qui se trouve dans le dossier de votre projet.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

Dans le fichier *AndroidManifest.xml* de votre projet, ajoutez les autorisations suivantes à l’intérieur de l’élément `<manifest>` (si elles ne s’y trouvent pas déjà). Cela donne à votre application l’autorisation de se connecter à Internet et d’activer la découverte Bluetooth sur votre appareil.

Notez que les autorisations liées à Bluetooth servent uniquement à la découverte Bluetooth ; elles n’ont pas d’utilité pour les autres fonctionnalités de la Plateforme d’appareils connectés. Par ailleurs, `ACCESS_COARSE_LOCATION` est nécessaire uniquement pour les SDK Android version 21 et ultérieure. Sur les SDK Android version 23 et ultérieures, le développeur doit aussi demander à l’utilisateur d’accorder l’accès à l’emplacement au moment de l’exécution.


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Ensuite, accédez aux classes d’activité dans lesquelles vous voulez activer la fonctionnalité Appareils connectés. Importez les packages suivants.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```