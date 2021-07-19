---
title: Publier le contenu traduit
description: Découvrez comment publier votre contenu localisé.
source-git-commit: 3ab886361dc01c943bd00025695d34a218b1aa41
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 1%

---

# Publier le contenu traduit {#publish-content}

Découvrez comment publier votre contenu localisé.

## La démarche à ce stade {#story-so-far}

Dans le document précédent du parcours de localisation sans interface utilisateur AEM, [Traduire le contenu,](configure-connector.md) vous avez appris à utiliser AEM projets de traduction pour traduire votre contenu sans interface utilisateur. Vous devez maintenant :

* Comprendre ce qu’est un projet de traduction.
* Vous pouvez créer de nouveaux projets de traduction.
* Utilisez des projets de traduction pour traduire votre contenu sans tête.

Maintenant que votre traduction initiale est terminée, cet article vous guide tout au long de l’étape suivante de la publication de ce contenu et de ce que vous devez faire pour mettre à jour vos traductions à mesure que le contenu racine de la langue sous-jacente change.

## Objectif {#objective}

Ce document vous aide à comprendre comment publier du contenu sans interface dans AEM et comment créer un workflow continu pour maintenir vos traductions à jour. Après avoir lu ce document, vous devez :

* Comprendre le modèle d’AEM auteur-publication.
* Découvrez comment publier votre contenu traduit.
* Vous pouvez mettre en oeuvre un modèle de mise à jour continue pour votre contenu traduit.

## AEM modèle Auteur-Publication {#author-publish}

Avant de publier votre contenu, il est préférable de comprendre AEM modèle auteur-publication. En termes simples, AEM divise les utilisateurs du système en deux groupes.

1. Les personnes qui créent et gèrent le contenu et le système
1. Ceux qui utilisent le contenu du système.

AEM est donc physiquement séparé en deux instances.

1. L’instance **author** est le système dans lequel les auteurs et les administrateurs de contenu travaillent à créer et à gérer du contenu.
1. L’instance **publish** est le système qui diffuse le contenu aux consommateurs.

Une fois le contenu créé sur l’instance d’auteur, il doit être transféré sur l’instance de publication pour qu’il puisse être utilisé. Le processus de transfert de l’auteur à la publication s’appelle **publication**.

## Publication de contenu traduit {#publishing}

Une fois que vous êtes satisfait de l’état de votre contenu traduit, vous pouvez le publier afin que les services sans interface puissent l’utiliser. Pour ce faire, la méthode la plus simple consiste à accéder au dossier des ressources du projet.

```text
/content/dam/<your-project>/
```

Sous ce chemin d’accès, vous disposez de sous-dossiers pour chaque langue de traduction et vous pouvez choisir celle à publier.

1. Accédez à **Navigation** -> **Ressources** -> **Fichiers** et ouvrez le dossier du projet.
1. Vous y verrez le dossier racine de langue et tous les autres dossiers de langue. Sélectionnez la ou les langues localisées que vous souhaitez publier.
   ![Sélectionner le dossier de langue](assets/select-language-folder.png)
1. Appuyez ou cliquez sur **Gérer la publication**.
1. Dans la fenêtre **Gérer la publication** , vérifiez que **Publier** est automatiquement sélectionné sous **Action** et que **Maintenant** est sélectionné sous **Planification**. Cliquez ou appuyez sur **Suivant**.
   ![Gérer les options de publication](assets/manage-publication-options.png)
1. Dans la fenêtre **Gérer la publication** suivante, vérifiez que le ou les chemins appropriés sont/sont sélectionnés. Appuyez ou cliquez sur **Publier**.
   ![Gérer l’étendue de la publication](assets/manage-publication-scope.png)
1. AEM confirme l’action de publication avec un message contextuel en bas de l’écran.
   ![Bannière Ressources publiées](assets/resources-published-message.png)

Votre contenu localisé sans interface est maintenant publié ! Il est désormais accessible et utilisé par vos services sans interface utilisateur graphique.

>[!TIP]
>
>Vous pouvez sélectionner plusieurs éléments (c’est-à-dire plusieurs dossiers de langues) lors de la publication afin de publier plusieurs éléments à la fois.

Il existe d’autres options lors de la publication de votre contenu, telles que la planification d’une heure de publication qui dépasse le cadre de ce parcours. Pour plus d’informations, voir la section [Ressources supplémentaires](#additional-resources) à la fin du document.

## Mise à jour de votre contenu traduit {#updating-translations}

La localisation et la traduction sont rarement un exercice ponctuel. En règle générale, vos auteurs de contenu continuent à ajouter et à modifier votre contenu à la racine de langue une fois la localisation initiale terminée. Cela signifie que vous devrez également mettre à jour votre contenu traduit.

Les exigences spécifiques au projet définissent la fréquence à laquelle vous devrez mettre à jour vos traductions et le processus de décision qui sera suivi avant d’effectuer une mise à jour. Une fois que vous avez décidé de mettre à jour vos traductions, le processus en AEM est très simple. Comme la traduction initiale était basée sur un projet de traduction, il en va de même pour toutes les mises à jour.

1. Accédez à **Navigation** -> **Ressources** -> **Fichiers**. N’oubliez pas que le contenu sans interface dans AEM est stocké en tant que ressources appelées fragments de contenu.
1. Sélectionnez la racine de langue de votre projet. Dans ce cas, nous avons sélectionné `/content/dam/wknd/en`.
1. Appuyez ou cliquez sur le sélecteur de rail et affichez le panneau **Références** .
1. Appuyez ou cliquez sur **Copies de langue**.
1. Cochez la case **Copies de langue** .
1. Développez la section **Mettre à jour les copies de langue** au bas du panneau Références.
1. Dans la liste déroulante **Projet**, sélectionnez **Ajouter à un projet de traduction existant**.
1. Dans la liste déroulante **Projet de traduction existant** , sélectionnez le projet créé pour la traduction initiale.
1. Appuyez ou cliquez sur **Démarrer**.

![Ajout d’éléments à un projet de traduction existant](assets/add-to-existing-project.png)

Le contenu est ajouté au projet de traduction existant. Pour afficher le projet de traduction :

1. Accédez à **Navigation** -&amp; **Projets**.
1. Appuyez ou cliquez sur le projet que vous venez de mettre à jour.
1. Appuyez ou cliquez sur la langue ou l’une des langues que vous avez mises à jour.

Vous verrez qu’une nouvelle carte de tâche a été ajoutée au projet. Dans cet exemple, une autre traduction espagnole a été ajoutée.

![Tâche de traduction supplémentaire ajoutée](assets/additional-translation-job.png)

Vous remarquerez que les statistiques répertoriées sur la nouvelle carte (nombre de ressources et fragments de contenu) sont différentes. Cela est dû au fait qu’AEM reconnaît ce qui a changé depuis la dernière traduction et inclut uniquement le nouveau contenu qui doit être traduit (contenu mis à jour à nouveau traduit ou première traduction de nouveau contenu).

À partir de là, vous [démarrez et gérez votre tâche de traduction comme vous l’avez fait pour l’original.](translate-content.md#using-translation-project)

## Fin du Parcours ? {#end-of-journey}

Félicitations ! Vous avez terminé le parcours de localisation sans interface ! Vous devez maintenant :

* disposer d’une vue d’ensemble de la diffusion de contenu sans interface ;
* Comprendre de base AEM fonctions sans tête.
* Découvrez AEM fonctionnalités de localisation et comment elles sont liées au contenu sans interface.
* Vous pouvez commencer à localiser votre propre contenu sans interface.

Vous êtes maintenant prêt à localiser votre propre contenu sans interface dans AEM. Cependant, AEM est un outil puissant et de nombreuses autres options sont disponibles. Consultez certaines des ressources supplémentaires disponibles dans la section suivante pour en savoir plus sur les fonctionnalités que vous avez vues dans ce parcours.

## Ressources supplémentaires {#additional-resources}

* [Gestion des projets de traduction](/help/sites-cloud/administering/translation/managing-projects.md)  : découvrez les détails des projets de traduction et les fonctionnalités supplémentaires telles que les processus de traduction humaine et les projets multilingues.
* [Concepts de création](/help/sites-cloud/authoring/getting-started/concepts.md)  : découvrez plus en détail le modèle d’AEM de création et de publication. Ce document se concentre sur la création de pages plutôt que sur les fragments de contenu, mais la théorie s’applique toujours.
* [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  : découvrez les fonctionnalités supplémentaires disponibles lors de la publication de contenu. Ce document se concentre sur la création de pages plutôt que sur les fragments de contenu, mais la théorie s’applique toujours.
