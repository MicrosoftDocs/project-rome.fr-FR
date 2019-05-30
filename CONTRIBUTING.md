---
ms.openlocfilehash: efd862261f2d1a6cce52214b56135d2c40f632c6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907441"
---
# <a name="contributing-to-the-project-rome-documentation"></a>Contribution à la documentation de Project Rome

Nous vous remercions de votre intérêt dans notre documentation. Nous apprécions vos commentaires, modifications, ajouts et les aider à améliorer notre documentation. Cette page traite les étapes de base et les instructions pour votre contribution.

## <a name="sign-a-cla"></a>Signature d’un CLA

Si vous souhaitez contribuer plus de quelques lignes, et vous n’êtes pas un employé de Microsoft, vous devez [signer un Microsoft licences accord de contribution](https://cla.microsoft.com/). 

## <a name="propose-a-minor-change"></a>Proposer une modification mineure

Pour suggérer une modification simple à la documentation, procédez comme suit :

1. Si vous affichez la page de Docs.microsoft.com, cliquez sur le **modifier** bouton dans le coin supérieur droit de la page.  Vous êtes redirigé vers le fichier de source de Markdown correspondant dans le [référentiel GitHub](https://github.com/MicrosoftDocs/project-rome). Si vous êtes déjà dans le référentiel GitHub, vous pouvez accédez au fichier source que vous souhaitez modifier.
2. Si vous ne disposez pas d’un compte GitHub, cliquez sur **s’inscrire** dans le coin supérieur droit et créer un nouveau compte.
3. Dans la page GitHub que vous souhaitez modifier, cliquez sur l’icône de crayon. 
4. Modifiez le fichier et utilisez l’onglet Aperçu pour vous assurer que les modifications sont de bonne qualitées.
5. Lorsque vous avez terminé, validez vos modifications et ouvrir une demande de tirage.

Après avoir créé la demande de tirage, elle sera examinée par un membre de l’équipe de docs Windows 10. Si votre demande est acceptée, les mises à jour seront publiées à [ https://docs.microsoft.com/windows/project-rome/ ](https://docs.microsoft.com/windows/project-rome/).

## <a name="make-more-substantial-changes"></a>Apporter des modifications plus importantes

### <a name="fork-the-github-repo"></a>Répliquer le référentiel GitHub

Pour apporter des modifications importantes à un article existant, ajouter ou modifier les images ou contribuer un nouvel article, nous vous recommandons de duplication du dépôt dans votre compte GitHub (cliquez sur le bouton « Duplication » dans le coin supérieur droit de la [référentiel GitHub](https://github.com/MicrosoftDocs/project-rome), puis Création d’un clone local (cliquez sur le vert **cloner ou télécharger** copier dans le Presse-papiers, puis, dans votre ligne de commande de bouton, entrée `git clone <paste your repo clone link>`).

Pour plus d’informations, consultez [branchement de référentiel](https://help.github.com/articles/fork-a-repo/).

Si vous n’êtes pas familiarisé avec l’utilisation de Git, consultez le [formation de Lynda.com Git Essentials](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html).

### <a name="author-your-contribution"></a>Créer votre contribution

Une fois que vous avez dupliqué et cloné le référentiel sur votre ordinateur local, vous pouvez commencer à créer avec l’éditeur de texte de votre choix. Nous vous recommandons de [Visual Studio Code](https://code.visualstudio.com/), un éditeur léger open source gratuit de Microsoft.

### <a name="submit-your-contribution-by-issuing-a-pull-request-pr"></a>Envoyer votre contribution en émettant une demande de tirage (PR)

Une fois que vous avez enregistré les modifications à votre référentiel git local, entrez les commandes suivantes dans la ligne de commande pour valider et de les transmettre à votre référentiel BIFURQUÉ local :
- `git status`: Cette commande affiche les fichiers que vous avez modifié afin que vous puissiez confirmer que vous voulez apporter ces modifications. 
- `git add -A`: Cette commande ajoute toutes vos modifications à l’index de la modification. Si vous préférez ajouter uniquement les modifications apportées à un fichier particulier, entrez la commande : `git add <yourfile.md>`.
- `git commit -m "your commit message"`: Cette commande indique à git pour valider les modifications que vous avez ajouté à l’étape précédente, ainsi que d’un bref message décrivant les modifications que vous avez apportées.
- `git push origin <yourbranchname>`: Cette commande exécute un push de vos modifications dans le référentiel distant que vous dupliqués sur GitHub (« l’origine »), dans la branche que vous avez spécifiées.

Après avoir diffusé votre contribution dans le référentiel distant, vous recevrez un e-mail à partir de *Open Publishing Service de Build* vous informant si votre contribution a été créé avec succès et en fournissant des liens vers des erreurs ou avertissements dans votre référentiel, tels que des liens rompus. Cliquez sur les liens dans le rapport pour afficher votre contenu intermédiaire sur le site. Lorsque vos modifications sont effacées des erreurs et avertissements, vous êtes prêt à envoyer une demande de tirage.
- Accédez à votre branchement du dépôt de projet-rome : https://github.com/  **\<your-github-alias\>**/project-rome.
- Cliquez sur le **nouvelle requête de tirage** bouton. Le « branchement de base : » est répertorié comme « MicrosoftDocs/project-rome » et le « branchement principal : » doit afficher votre embranchement du référentiel et de la branche dans laquelle vous vos modifications. Vous pouvez consulter vos modifications ici également. 
- Cliquez sur le **créer une demande de tirage** bouton. Vous devrez donner votre demande de tirage, un titre et une description. Enfin, cliquez sur le **créer une demande de tirage** bouton une fois de plus.

Une fois votre demande de tirage est envoyée, elle sera examinée par un membre de l’équipe de docs Windows 10. Lorsqu’elle est acceptée, vous serez en mesure d’afficher vos modifications sur le [site intermédiaire](https://review.docs.microsoft.com/windows/project-rome/). Ces mises à jour seront finalement publiées en direct dans [ https://docs.microsoft.com/windows/project-rome/ ](https://docs.microsoft.com/windows/project-rome/).

## <a name="using-issues-to-provide-feedback-on-project-rome-documentation"></a>À l’aide des problèmes pour fournir des commentaires sur la documentation de Project Rome

Pour fournir des commentaires plutôt que de modifier directement les pages de documentation, [créer un problème](https://github.com/MicrosoftDocs/project-rome/issues).

Veillez à inclure le titre de rubrique et l’URL de la page en question.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Mise en route avec l’écriture et mise en forme sur GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Ressources supplémentaires pour les employés de Microsoft
- [Connecter votre compte GitHub et alias de MS](https://review.docs.microsoft.com/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Ressources pour l’écriture de Markdown](https://review.docs.microsoft.com/windows-authoring-guide/writing-guidance/writing-markdown)