---
title: MCDAppServiceInfo
description: Cette classe décrit un service d’application qui appartient à une application ou un périphérique distant.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801161"
---
# <a name="class-mcdappserviceinfo"></a>Classe `MCDAppServiceInfo` 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

Cette classe décrit un service d’application qui appartient à une application ou un périphérique distant.

## <a name="properties"></a>Properties

### <a name="name"></a>name
`@property(nonatomic, readonly, nullable) NSString* name;`

Le nom du service d’application en cours de description.

### <a name="packageid"></a>packageId
`@property(nonatomic, readonly, nullable) NSString* packageId;`

L’ID de package du service d’application en cours de description.

## <a name="constructors"></a>Constructeurs

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

Initialiser la classe avec les informations et le nom du service d’application.

#### <a name="parameters"></a>Paramètres 
* `name` 

Le nom du service d’application en cours de description.

#### <a name="returns"></a>Returns
Retourne un objet MCDAppServiceInfo contenant le nom fourni.

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

Initialiser la classe avec le nom de l’app service.

#### <a name="parameters"></a>Paramètres 
* `name` 

Le nom du service d’application en cours de description.

#### <a name="returns"></a>Returns
Retourne un objet MCDAppServiceInfo initialisé avec le nom fourni.

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

Initialiser la classe avec les informations et le nom du service d’application.

#### <a name="parameters"></a>Paramètres 
* `name` 

Le nom du service d’application en cours de description.

* `packageId` 

L’ID de package du service d’application en cours de description.

#### <a name="returns"></a>Returns
Retourne un objet MCDAppServiceInfo contenant le nom fourni.

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

Initialiser la classe avec le nom de l’app service.

#### <a name="parameters"></a>Paramètres 
* `name` 

Le nom du service d’application en cours de description.

* `packageId` 

L’ID de package du service d’application en cours de description.

#### <a name="returns"></a>Returns
Retourne un objet MCDAppServiceInfo initialisé avec le nom fourni.
