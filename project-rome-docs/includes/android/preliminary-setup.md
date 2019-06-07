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
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>Programme d’installation préliminaire pour la plateforme de périphériques connectés et les Notifications

Avant d’implémenter la connectivité à distance, il existe quelques étapes, que vous devrez suivre pour permettre à votre application Android à connecter des appareils à distance, ainsi que d’envoyer et recevoir des notifications.

### <a name="register-your-app"></a>Inscrire votre application

Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour presque toutes les fonctionnalités de Project Rome SDK (l’exception en cours de l’API de partage à proximité). Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.

À l’aide de votre méthode d’authentification choisi, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/). Si vous n’avez pas un compte de développeur Microsoft, vous devrez créer un.

Lorsque vous inscrivez une application à l’aide d’un compte de service administré, vous devez recevoir une chaîne d’ID de client. Enregistrer ce paramètre pour une utilisation ultérieure. Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft. Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.

### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Insérer les références de référentiel suivantes dans le *build.gradle* fichier à la racine de votre projet.

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
Puis, insérez la dépendance suivante dans le _build.gradle_ fichier qui se trouve dans votre dossier de projet.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

Dans votre projet *AndroidManifest.xml* , ajoutez les autorisations suivantes à l’intérieur de la `<manifest>` (s’ils ne figurent pas déjà). Ainsi, votre application l’autorisation pour se connecter à Internet et pour activer la découverte de Bluetooth sur votre appareil.

Notez que les autorisations liées à Bluetooth sont uniquement nécessaires pour l’utilisation de découverte de Bluetooth ; ils ne sont pas nécessaires pour les autres fonctionnalités de la plateforme d’appareils connectés. En outre, `ACCESS_COARSE_LOCATION` est uniquement requis sur Android SDK 21 et versions ultérieures. Sur Android SDK 23 et versions ultérieures, le développeur doit également l’utilisateur pour accorder l’accès à l’emplacement lors de l’exécution.


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Ensuite, accédez à l’ou les classes activité où vous souhaitez que les fonctionnalités d’appareils connectés à live. Importer les packages suivants.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
