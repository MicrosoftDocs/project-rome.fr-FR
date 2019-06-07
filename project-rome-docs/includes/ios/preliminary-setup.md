---
title: Fichier Include
description: Fichier Include
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b979c0b7891aaa6ce5c422d8349809b429a47201
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755748"
---
### <a name="register-your-app"></a>Inscrire votre application

Authentification de compte Microsoft (MSA) ou Azure Active Directory (AAD) est requise pour presque toutes les fonctionnalités de Project Rome SDK (l’exception en cours de l’API de partage à proximité). Si vous ne pas déjà un compte de service administré et souhaiter utiliser une, inscrire sur [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> Les comptes Azure Active Directory (AAD) ne sont pas pris en charge avec les API de relais d’appareil.

À l’aide de votre méthode d’authentification choisi, vous devez inscrire votre application auprès de Microsoft en suivant les instructions la [portail d’inscription des applications](https://apps.dev.microsoft.com/). Si vous n’avez pas un compte de développeur Microsoft, vous devrez créer un.

Lorsque vous inscrivez une application à l’aide d’un compte de service administré, vous devez recevoir une chaîne d’ID de client. Enregistrer ce paramètre pour une utilisation ultérieure. Cela permettra à votre application d’accéder aux ressources de la plate-forme de périphériques connectés de Microsoft. Si vous utilisez AAD, consultez [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) pour obtenir des instructions sur l’obtention de chaîne d’ID du client.

### <a name="add-the-sdk"></a>Ajoutez le kit SDK

Le plus simple pour ajouter la plateforme d’appareils connectés à votre application iOS consiste à l’aide de la [CocoaPods](https://cocoapods.org/) Gestionnaire de dépendances. Accédez à votre projet iOS *Podfile* et insérez l’entrée suivante :

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
> Afin de consommer CocoaPod, vous devez utiliser le _.xcworkspace_ fichier dans votre projet.
