---
title: Publication et lecture d’activités de l’utilisateur (iOS)
description: Ce guide montre comment créer, publier et lire des activités de l’utilisateur Windows dans votre application iOS.
ms.topic: article
keywords: microsoft, windows, projet rome, activités de l’utilisateur, ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801671"
---
# <a name="implementing-user-activities-for-ios"></a>Implémentation d’activités de l’utilisateur pour iOS

Les activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application. Elles permettent d’enregistrer une capture instantanée d’une tâche en cours à poursuivre ultérieurement. La fonctionnalité [Chronologie Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représentées sous forme de cartes comportant du texte et des graphiques. Pour plus d’informations sur les activités de l’utilisateur en général, consultez [Poursuivre l’activité utilisateur, même sur différents appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Pour savoir quand créer ou mettre à jour des activités, consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices).

Avec le SDK Projet Rome, votre application iOS peut non seulement publier des activités de l’utilisateur pour une utilisation dans des fonctionnalités Windows telles que la Chronologie, mais elle peut également agir comme point de terminaison et relire des activités à l’utilisateur comme le fait la Chronologie. Cela permet aux applications inter-appareils de transcender totalement leurs plateformes et de proposer des expériences qui suivent les utilisateurs plutôt que les appareils.

Les fonctionnalités du projet Rome sont prises en charge par une plateforme sous-jacente appelée Plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la Plateforme d’appareils connectés, puis explique comment implémenter les fonctionnalités liées aux activités de l’utilisateur à l’aide de cette plateforme.

Les étapes ci-dessous font référence à du code tiré de l’[exemple d’application iOS du projet Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

Consultez la page [Informations de référence sur les API](api-reference-for-ios.md) pour obtenir des liens vers la documentation de référence pertinente pour ces scénarios.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la Plateforme d’appareils connectés et des notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Utilisation de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Initialiser un canal des activités de l’utilisateur

Pour implémenter les fonctionnalités Activité de l’utilisateur dans votre application, vous devez d’abord initialiser le flux des activités de l’utilisateur en créant un MCDUserActivityChannel. Vous devez considérer cette opération comme l’étape d’initialisation de la plateforme ci-dessus : elle doit être vérifiée et éventuellement refaite chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de la plateforme).

Pour cette étape, vous devez disposer d’un compte d’utilisateur connecté. Comme ci-dessus, vous pouvez utiliser une classe de l’exemple de fournisseur d’authentification pour acquérir facilement le ou les MCDUserAccounts. Vous aurez aussi besoin de votre ID d’application multiplateforme, qui a été récupéré par le biais de l’inscription au tableau de bord du développeur Microsoft.
La méthode suivante de l’exemple d’application initialise un MCDUserActivityChannel.

La méthode suivante de l’exemple d’application initialise un MCDUserActivityChannel.

```ObjectiveC

    // Get a UserActivity channel, getting the default channel        
    NSLog(@"Creating UserActivityChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserActivityChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserActivityChannel userActivityChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must have an active account to publish activities!");
    self.createActivityStatusField.text = @"Need to be logged in!";
}
```
À ce stade, vous devez avoir une référence à MCDUserActivityChannel dans le canal.

### <a name="create-and-publish-a-user-activity"></a>Créer et publier une activité de l’utilisateur

L’exemple de code suivant montre comment une nouvelle instance de **MCDUserActivity** est créée.

```ObjectiveC
- (IBAction)createActivityButton:(id)sender
{
    // Step #2: Create a UserActivity
    [self.channel getOrCreateUserActivityAsync:[[NSUUID UUID] UUIDString]
        completion:^(MCDUserActivity* activity, NSError* error) {
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error creating activity!";
            }
            else if (!activity)
            {
                NSLog(@"No activity created!");
            }
            else
            {
                dispatch_async(dispatch_get_main_queue(), ^{
                    self.activity = activity;

                    // Create an activityId so the app knows so you know how to get back
                    self.activityId.text = activity.activityId;
                    self.createActivityStatusField.text = @"Created by iOSSample";
                    // Create a deep link so the app can get right back to where it was
                    self.activationUri.text = @"roman-app:";
                    self.createActivityStatusField.text = @"Activity created";
                });
            }
        }];
}
```

Dans la méthode suivante, les données visuelles de **MCDUserActivity** sont définies avant la publication de l’activité. L’URI d’activation détermine l’action qui est effectuée quand l’activité est activée (quand elle est sélectionnée dans la Chronologie, par exemple). Le texte d’affichage s’affiche sur d’autres appareils quand ils consultent l’activité (dans la Chronologie Windows, par exemple). L’iconUri est un lien web vers une image d’icône.


```ObjectiveC
- (IBAction)publishActivityButton:(id)sender
{
    self.createActivityStatusField.text = @"Saving";
    self.activity.activationUri = self.activationUri.text;
    // Set the display text for your activity.
    self.activity.visualElements.displayText = @"Visual Element, like an Adaptive Card";
    self.activity.visualElements.attribution.iconUri = @"https://www.microsoft.com/favicon.ico";

    // ...
```

Une fois le **MCDUserActivity** rempli avec ces données, l’opération de publication a lieu.

```ObjectiveC
    // ...

    // Publish the Activity
    [self.activity saveAsync:^(NSError* error) {
        dispatch_async(dispatch_get_main_queue(), ^{
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error saving activity";
            }
            else
            {
                self.createActivityStatusField.text = @"Saved successfully!";
                [self.sessionButton setTitle:@"Start Session" forState:normal];
            }
        });
    }];
}

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```
> [!TIP] 
> Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées. Pour obtenir une étude complète des différentes façons de personnaliser un UserActivity, consultez les classes **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)** , **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)** et **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** . Consultez le guide [Bonnes pratiques concernant les activités de l’utilisateur](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) pour obtenir des recommandations détaillées sur la façon de concevoir des activités de l’utilisateur.

## <a name="update-an-existing-user-activity"></a>Mettre à jour une activité d’utilisateur existante

Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas de nouvel engagement, de page modifiée, etc.), vous pouvez le faire en utilisant un **MCDUserActivitySession**. 

Une fois que vous avez créé une session, votre application peut apporter les changements souhaités aux propriétés de **UserActivity**. Quand vous avez terminé d’apporter les changements, fermez la session. 

La méthode suivante de l’exemple d’application active ou désactive une session.

```ObjectiveC
- (IBAction)manageSessionButton:(id)sender
{

    // Start a new a session for the UserActivity
    if (self.session == nil)
    {
       self.session = [self.activity createSession];
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has started %@", self.session);
            self.session = [self.activity createSession];
            dispatch_async(dispatch_get_main_queue(), ^{ [self.sessionButton setTitle:@"Stop Session" forState:normal]; });
        });
    }
    else
    {
        // Stop the UserActivitySession
        [self.session close];
        self.session = nil;
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has stopped %@", self.session);
            [self.sessionButton setTitle:@"Start Session" forState:normal];
        });
    }
}
```


Un **MCDUserActivitySession** peut être considéré comme un moyen de créer un **MCDUserActivitySessionHistoryItem** (décrit dans la section suivante). Au lieu de créer un **MCDUserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une session pour chaque page. Cela constitue une expérience de lecture d’activité plus intuitive et plus organisée.

## <a name="read-user-activities"></a>Lire des activités de l’utilisateur

Votre application peut lire les activités de l’utilisateur et les présenter à l’utilisateur exactement comme le fait la fonctionnalité Chronologie Windows. Pour configurer la lecture des activités de l’utilisateur, vous utilisez la même instance de **MCDUserActivityChannel** que précédemment. Cette instance peut exposer des instances de **MCDUserActivitySessionHistoryItem**, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.

```ObjectiveC
- (IBAction)readActivityButton:(id)sender
{

    // Read/sync your UserActivities
    [self.channel getRecentUserActivitiesAsync:(NSInteger)5
        completion:^(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull result, NSError* _Nullable error) {
            dispatch_async(dispatch_get_main_queue(), ^{
                if (error)
                {
                    self.readActivityStatusField.text = @"Error reading activity!";
                }
                else if (result.count == 0)
                {
                    self.readActivityStatusField.text = @"Read completed, no activities returned";
                }
                else
                {
                    self.readActivityStatusField.text = @"Read completed!";
                    MCDUserActivitySessionHistoryItem* item = result.firstObject;
                    self.activityList.text = item.userActivity.activityId;
                    self.activityDisplay.text = item.userActivity.visualElements.displayText;
                }
            });
        }];
}
```

Votre application doit maintenant disposer d’une liste d’éléments **MCDUserActivitySessionHistoryItem**. Chacun d’entre eux peut fournir le **MCDUserActivity** sous-jacent (consultez **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.
