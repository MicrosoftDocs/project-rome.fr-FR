---
title: Publication et la lecture des activités de l’utilisateur (iOS)
description: Ce guide montre comment créer, publier et lire des activités des utilisateurs dans votre application iOS basée sur Windows.
ms.topic: article
keywords: Microsoft, windows, project rome, d’activités des utilisateurs, d’ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801671"
---
# <a name="implementing-user-activities-for-ios"></a>Implémentation d’activités des utilisateurs pour iOS

Activités de l’utilisateur sont des constructions de données qui représentent les tâches d’un utilisateur dans une application. Ils permettent d’enregistrer un instantané d’une tâche en cours de se poursuivre ultérieurement. Le [Windows chronologie](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) fonctionnalité offre aux utilisateurs Windows une liste déroulante de toutes leurs activités récentes, représenté sous forme de cartes avec le texte et les graphiques. Pour plus d’informations sur les activités des utilisateurs en général, consultez [continuer les activités des utilisateurs, même sur les appareils](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Pour obtenir des recommandations concernant créer ou mettre à jour des activités, consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.

Avec le Kit de développement Project Rome, votre application iOS peut publier pas uniquement les activités de l’utilisateur pour une utilisation dans les fonctionnalités de Windows telles que la chronologie, mais il peut également agir comme un point de terminaison et lire des activités à l’utilisateur comme le fait de chronologie. Cela permet aux applications d’inter-périphériques transcender complètement les leurs plateformes et des expériences présentes qui suivent les utilisateurs plutôt que des appareils.

Les fonctionnalités de Project Rome sont pris en charge par une plateforme sous-jacente, appelée la plateforme d’appareils connectés. Ce guide décrit les étapes nécessaires pour commencer à utiliser la plateforme d’appareils connectés, puis explique comment utiliser la plateforme pour implémenter des fonctionnalités connexes d’activités utilisateur.

Présente les étapes ci-dessous référencera le code à partir de la [exemple d’application de Project Rome iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) qui est disponible sur GitHub.  

Consultez le [référence de l’API](api-reference-for-ios.md) page pour des liens vers la documentation de référence relatives à ces scénarios.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuration de la plateforme de périphériques connectés et les Notifications

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>À l’aide de la plateforme

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Initialiser un canal de l’activité des utilisateurs

Pour implémenter les fonctionnalités de l’activité des utilisateurs dans votre application, vous devez d’abord initialiser le flux en créant un MCDUserActivityChannel d’activité utilisateur. Vous devez le considérer comme l’étape d’initialisation de plateforme ci-dessus : il doit être vérifié et éventuellement restauré chaque fois que l’application s’affiche au premier plan (mais pas avant l’initialisation de plateforme).

Vous devez un compte d’utilisateur connecté pour cette étape. Comme ci-dessus, vous pouvez utiliser une classe à partir de l’exemple de fournisseur d’authentification pour acquérir facilement le MCDUserAccount(s). Vous devez également votre ID d’application multiplateforme, qui a été récupérée via l’inscription de tableau de bord de développement Microsoft.
La méthode suivante à partir de l’exemple d’application initialise un MCDUserActivityChannel.

La méthode suivante à partir de l’exemple d’application initialise un MCDUserActivityChannel.

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
À ce stade, vous devez avoir une référence MCDUserActivityChannel dans le canal.

### <a name="create-and-publish-a-user-activity"></a>Créer et publier une activité utilisateur

L’exemple suivant de code montre comment un nouveau **MCDUserActivity** instance est créée.

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

Dans la méthode suivante, les données visuelles de la **MCDUserActivity** est définie avant la publication de l’activité. L’URI de l’activation déterminent quelle action est effectuée lorsque l’activité est activée (lorsqu’il est sélectionné dans la chronologie, par exemple). Le texte d’affichage s’affichera sur d’autres appareils lorsqu’ils les consultent l’activité (dans la chronologie de Windows, par exemple). L’iconUri est un lien web vers une image d’icône.


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

Une fois le **MCDUserActivity** est rempli avec ces données, l’opération de publication a lieu.

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
> Outre les propriétés ci-dessus, il existe de nombreuses autres fonctionnalités qui peuvent être configurées. Pour une présentation plus détaillée sur les différentes façons qu’un UserActivity peut être personnalisé, consultez le  **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, et **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes. Consultez le [les activités utilisateur meilleures pratiques](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide pour obtenir des recommandations détaillées quant à la conception d’activités des utilisateurs.

## <a name="update-an-existing-user-activity"></a>Mettre à jour d’une activité utilisateur existant

Si vous disposez d’une activité existante et que vous souhaitez mettre à jour ses informations (en cas d’un engagement nouvelle page modifiée et ainsi de suite), vous pouvez le faire en utilisant un **MCDUserActivitySession**. 

Une fois que vous avez créé une session, votre application peut effectuer les modifications souhaitées aux propriétés de la **UserActivity**. Lorsque vous avez terminé d’apporter des modifications, fermez la session. 

La méthode suivante à partir de l’exemple d’application active ou désactive une session sur Active et inactive.

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


Un **MCDUserActivitySession** peut être considéré comme un moyen de créer un **MCDUserActivitySessionHistoryItem** (présenté dans la section suivante). Au lieu de créer un nouveau **MCDUserActivity** chaque fois qu’un utilisateur accède à une nouvelle page, vous pouvez simplement créer une nouvelle session pour chaque page. Vous serez ainsi pour une activité plus intuitive et organisée expérience de lecture.

## <a name="read-user-activities"></a>Activités de l’utilisateur en lecture

Votre application peut lire les activités des utilisateurs et les présenter à l’utilisateur comme le fait de la fonctionnalité de montage de Windows. Pour configurer la lecture de l’activité des utilisateurs, vous utilisez le même **MCDUserActivityChannel** instance indiquée précédemment. Cette instance peut exposer **MCDUserActivitySessionHistoryItem** instances, qui représentent l’engagement d’un utilisateur dans une activité particulière pendant une période spécifique.

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

Maintenant votre application doit disposer d’une liste de **MCDUserActivitySessionHistoryItem**s. Chacun d'entre eux peut fournir sous-jacent **MCDUserActivity** (consultez **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** pour plus d’informations), que vous pouvez ensuite afficher à l’utilisateur.
