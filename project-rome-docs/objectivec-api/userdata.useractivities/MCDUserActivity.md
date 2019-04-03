---
title: MCDUserActivity
description: Cette classe représente une instance d’activité utilisateur unique.
keywords: Microsoft, windows, activités des utilisateurs, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907421"
---
# <a name="class-mcduseractivity"></a>Classe `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

Cette classe représente une instance d’activité utilisateur unique. Une activité de l’utilisateur est créée par une application pendant son exécution pour notifier le système d’un flux de travail d’utilisateur qui peut être poursuivi sur un autre appareil ou à un autre moment sur le même appareil. Il fournit des informations sur une tâche que prend part à l’utilisateur.

>**Remarque :** Les instances de MCDUserActivity ont une limite de taille de 100 Ko, au-delà de laquelle ils ne peuvent pas être publiés.

## <a name="properties"></a>Properties

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

ID unique pour cette activité.

### <a name="state"></a>État
`@property(nonatomic, readonly) MCDUserActivityState state;`

L’état de cette activité.

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

L’URI à suivre lors de cette activité utilisateur est activée.

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

L’URI web conviviale détenue par cette activité, à utiliser si l’URI principal échoue.

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

L’URI de contenu pour cette activité (l’URI de l’image qui sera utilisé pour représenter l’activité sur un autre périphérique).

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

le type MIME (Multipurpose Internet Mail Extensions) du contenu stocké dans **contentUri**. Par exemple, « text/plain ».

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

Informations de contenu de base pour cette activité. Par exemple, si votre activité a été lu un flux RSS, la chaîne de contenu peut inclure le nom de l’article et son auteur.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

Le nom d’affichage application pour cette activité.

### <a name="visualelements"></a>VisualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

Les éléments visuels pour cette activité (les informations qui peuvent être utilisées pour la vignette « détails » de l’activité).

### <a name="roamable"></a>transférable
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

Obtient ou définit si cette activité est itinérant pour les autres points de terminaison.

## <a name="constructors"></a>Constructeurs

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

Crée une instance de cette classe avec un ID donné.

#### <a name="parameters"></a>Paramètres
* `activityId` 

L’identificateur pour cette activité (doit être d’une chaîne unique).

#### <a name="returns"></a>Returns
Retourne une instance de cette classe.

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

Crée une instance de cette classe avec un ID donné.

#### <a name="parameters"></a>Paramètres
* `activityId`

L’identificateur pour cette activité (doit être d’une chaîne unique).

#### <a name="returns"></a>Returns
Retourne une instance de cette classe.

## <a name="methods"></a>Méthodes

### <a name="createsession"></a>createSession
`- (nonnull MCDUserActivitySession*)createSession;`

Crée une session d’activité utilisateur qui sera associé ce MCDUserActivity. Une MCDUserActivitySession associée indique que l’utilisateur actuellement engagée dans l’activité.

#### <a name="returns"></a>Returns
La session créée.

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Publie l’activité des utilisateurs. Le MCDUserActivity doit avoir une URI d’activation et de membre VisualElements avec texte à afficher ensemble avant que cette méthode est appelée. Cette méthode doit être appelée chaque fois que l’application modifie une propriété de la MCDUserActivity (afin de publier la mise à jour).

#### <a name="parameters"></a>Paramètres
* `completionBlock` Le bloc de code à exécuter en cas de saisie semi-automatique.