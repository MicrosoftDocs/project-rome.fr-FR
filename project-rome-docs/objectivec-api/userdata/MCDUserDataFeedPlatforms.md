---
title: MCDUserDataFeedPlatforms
description: Fournit la plateforme valide pour le MCDUserDataFeedSyncScope.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 7474c5896fec97a94799423ba0748bd2814d2c7a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801213"
---
# <a name="class-mcduserdatafeedplatforms"></a>Classe `MCDUserDataFeedPlatforms`

```
@interface MCDUserDataFeedPlatforms : NSObject

This class is responsible for providing the valid platform for the MCDUserDataFeedSyncScope.
```

## <a name="properties"></a>Properties

### <a name="all"></a>tous
`@property(class, nonatomic, readonly, nonnull) NSString* all;`

Tous les objets de la plateforme

### <a name="android"></a>android
`@property(class, nonatomic, readonly, nonnull) NSString* android;`

Objet de la plateforme Android

### <a name="ios"></a>iOS
`@property(class, nonatomic, readonly, nonnull) NSString* iOS;`

objet de la plateforme iOS

### <a name="windowsuwp"></a>windowsUWP
`@property(class, nonatomic, readonly, nonnull) NSString* windowsUWP;`

Objet de la plateforme UWP

### <a name="windows32"></a>windows32
`@property(class, nonatomic, readonly, nonnull) NSString* windows32;`

Objet de plateforme Windows32 prennent en charge

### <a name="linux"></a>linux
`@property(class, nonatomic, readonly, nonnull) NSString* linux;`

Objet de plateforme Linux