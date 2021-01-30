---
title: Fichier include
description: Fichier include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d0a91c583bda39cdef57adfdcab185e26e08195e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901545"
---
### <a name="register-your-app"></a>Inscrire votre application

L’authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est nécessaire pour pratiquement toutes les fonctionnalités du SDK du projet Rome (les API de partage de proximité étant l’exception). Si vous ne disposez pas déjà d’un compte MSA et que souhaitez en utiliser un, inscrivez-vous sur [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareils.

En utilisant la méthode d’authentification de votre choix, vous devez inscrire votre application auprès de Microsoft en suivant les instructions qui se trouvent sur le [portail d’inscription des applications](https://apps.dev.microsoft.com/). Si vous n’avez pas de compte de développeur Microsoft, vous devrez en créer un.

Quand vous inscrivez une application à l’aide d’un compte MSA, vous devez recevoir une chaîne d’ID client. Enregistrez-la pour plus tard. Elle permettra à votre application d’accéder aux ressources de la Plateforme d’appareils connectés de Microsoft. Si vous utilisez AAD, consultez [Bibliothèques d’authentification d’Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) pour savoir comment obtenir la chaîne d’ID client.

### <a name="add-the-sdk"></a>Ajouter le kit SDK

Le moyen le plus simple d’ajouter la Plateforme d’appareils connectés à votre application iOS est d’utiliser le gestionnaire de dépendances [CocoaPods](https://cocoapods.org/). Accédez au fichier *Podfile* de votre projet iOS et insérez l’entrée suivante :

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> Pour utiliser CocoaPod, vous devez utiliser le fichier _.xcworkspace_ dans votre projet.