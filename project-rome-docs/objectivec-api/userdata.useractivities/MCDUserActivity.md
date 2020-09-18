---
title: MCDUserActivity
description: En savoir plus sur la classe MCDUserActivity et ses propriétés. Cette classe représente une instance d’activité utilisateur unique.
keywords: Microsoft, Windows, activités utilisateur, iOS, iPhone, objectiveC, appareils connectés, projet Rome
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760143"
---
# <a name="class-mcduseractivity"></a>type `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

Cette classe représente une instance d’activité utilisateur unique. Une activité utilisateur est créée par une application pendant son exécution pour notifier au système d’un flux de travail de l’utilisateur qui peut être poursuivi sur un autre appareil ou à un autre moment sur le même appareil. Il fournit des informations sur une tâche dans laquelle l’utilisateur est engagé.

>**Remarque :** Les instances MCDUserActivity ont une limite de taille de 100 Ko, au-delà de laquelle elles ne peuvent pas être publiées.

## <a name="properties"></a>Propriétés

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

ID unique de cette activité.

### <a name="state"></a>state
`@property(nonatomic, readonly) MCDUserActivityState state;`

État de cette activité.

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

URI à suivre lorsque l’activité de l’utilisateur est activée.

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

URI convivial du Web détenu par cette activité, à utiliser en cas d’échec de l’URI principal.

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

URI de contenu pour cette activité (l’URI de l’image qui sera utilisée pour représenter l’activité sur un autre appareil).

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

type MIME (Multipurpose Internet Mail Extensions) du contenu stocké dans **contentUri**. Par exemple, « text/plain ».

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

Informations de base sur le contenu pour cette activité. Par exemple, si votre activité lit un flux RSS, la chaîne de contenu peut inclure le nom de l’article et son auteur.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

Nom complet de l’application pour cette activité.

### <a name="visualelements"></a>visualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

Éléments visuels pour cette activité (informations qui peuvent être utilisées pour la vignette « détails » de l’activité).

### <a name="roamable"></a>itinérance
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

Obtient ou définit une valeur indiquant si cette activité est itinérante vers d’autres points de terminaison.

## <a name="constructors"></a>Constructeurs

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

Crée une instance de cette classe avec un ID donné.

#### <a name="parameters"></a>Paramètres
* `activityId` 

Identificateur de cette activité (doit être une chaîne unique).

#### <a name="returns"></a>Retours
Retourne une instance de cette classe.

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

Crée une instance de cette classe avec un ID donné.

#### <a name="parameters"></a>Paramètres
* `activityId`

Identificateur de cette activité (doit être une chaîne unique).

#### <a name="returns"></a>Retours
Retourne une instance de cette classe.

## <a name="methods"></a>Méthodes

### <a name="createsession"></a>createSession
`- (nonnull MCDUserActivitySession*)createSession;`

Crée une session d’activité utilisateur à laquelle ce MCDUserActivity sera associé. Un MCDUserActivitySession associé indique que l’utilisateur est actuellement engagé dans l’activité.

#### <a name="returns"></a>Retours
Session créée.

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Publie l’activité de l’utilisateur. Le MCDUserActivity doit avoir un URI d’activation et un membre VisualElements avec le texte d’affichage défini avant que cette méthode soit appelée. Cette méthode doit être appelée chaque fois que l’application modifie une propriété de MCDUserActivity (afin de publier la mise à jour).

#### <a name="parameters"></a>Paramètres
* `completionBlock` Bloc de code à exécuter à la fin de l’opération.