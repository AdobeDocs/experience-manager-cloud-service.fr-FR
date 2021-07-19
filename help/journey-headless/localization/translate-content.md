---
title: Traduire le contenu
description: Utilisez le connecteur et les règles de traduction pour traduire votre contenu sans interface utilisateur graphique.
source-git-commit: 016b1126effb96598c9700377291333fb326c292
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 3%

---

# Traduire le contenu {#translate-content}

Utilisez le connecteur et les règles de traduction pour traduire votre contenu sans interface utilisateur graphique.

## La démarche à ce stade {#story-so-far}

Dans le document précédent du parcours de localisation AEM sans interface utilisateur graphique, [Configurer les règles de traduction](translation-rules.md) vous avez appris à utiliser AEM règles de traduction pour identifier votre contenu de traduction. Vous devez maintenant :

* Comprendre ce que font les règles de traduction.
* Vous pouvez définir vos propres règles de traduction.

Maintenant que votre connecteur et vos règles de traduction sont configurés, cet article vous guide tout au long de l’étape suivante de la traduction de votre contenu sans interface.

## Objectif {#objective}

Ce document vous aide à comprendre comment utiliser AEM projets de traduction avec le connecteur et vos règles de traduction pour traduire le contenu. Après avoir lu ce document, vous devriez :

* Comprendre ce qu’est un projet de traduction.
* Vous pouvez créer de nouveaux projets de traduction.
* Utilisez des projets de traduction pour traduire votre contenu sans tête.

## Création d’un projet de traduction {#creating-translation-project}

Les projets de traduction permettent de gérer la traduction de contenu AEM sans interface utilisateur. Un projet de traduction contient le contenu à traduire dans d’autres langues.

Lorsque du contenu est ajouté à un projet de traduction, une tâche de traduction est créée pour celui-ci. Les tâches comportent les commandes et les informations sur le statut utilisées pour gérer les processus de traduction humaine et automatique exécutés sur les ressources.

Pour créer un projet de traduction :

1. Accédez à **Navigation** -> **Ressources** -> **Fichiers**. N’oubliez pas que le contenu sans interface dans AEM est stocké en tant que ressources appelées fragments de contenu.
1. Sélectionnez la racine de langue de votre projet. Dans ce cas, nous avons sélectionné `/content/dam/wknd/en`.
1. Appuyez ou cliquez sur le sélecteur de rail et affichez le panneau **Références** .
1. Appuyez ou cliquez sur **Copies de langue**.
1. Cochez la case **Copies de langue** .
1. Développez la section **Mettre à jour les copies de langue** au bas du panneau Références.
1. Dans la liste déroulante **Projet**, sélectionnez **Créer un projet de traduction**.
1. Attribuez un titre approprié à votre projet de traduction.
1. Appuyez ou cliquez sur **Démarrer**.

![Créer un projet de traduction](assets/create-translation-project.png)

Vous recevez un message indiquant que le projet a été créé.

>[!NOTE]
>
>On suppose que la structure linguistique nécessaire pour les langues de traduction a déjà été créée dans le cadre de la [définition de votre structure de contenu.](getting-started.md#content-structure) Cela doit être fait en collaboration avec l’architecte de contenu.

## Utilisation d’un projet de traduction {#using-translation-project}

Lors de la création du projet de traduction, AEM a évalué le contenu sans en-tête sous le chemin que vous avez sélectionné, ainsi que selon les règles que vous avez précédemment définies. En fonction de ces règles, il a extrait le contenu qui doit être traduit dans un nouveau projet de traduction.

Pour afficher le projet de traduction :

1. Accédez à **Navigation** -&amp; **Projets**.
1. Appuyez ou cliquez sur le projet qui a été créé dans la section précédente.

![Projet de traduction](assets/translation-project.png)

Le projet est divisé en plusieurs cartes.

* **Résumé**  : cette carte affiche les informations d’en-tête de base du projet, y compris le propriétaire, la langue et le fournisseur de traduction.
* **Tâche de traduction**  : cette carte présente un aperçu de la tâche de traduction proprement dite, y compris l’état, le nombre de ressources, etc.
* **Équipe**  : cette carte présente les utilisateurs qui collaborent à ce projet de traduction. Ce parcours ne traitera pas de ce sujet.
* **Tâches**  : tâches supplémentaires associées à la traduction du contenu, telles que la réalisation d’éléments ou d’éléments de workflow. Ce parcours ne traitera pas de ce sujet.

Pour afficher le détail du contenu sans en-tête inclus dans ce projet :

1. Appuyez ou cliquez sur le bouton représentant des points de suspension en bas de la carte **Tâche de traduction** .
1. La fenêtre **Tâche de traduction** répertorie tous les éléments de la tâche.
   ![Détails de la tâche de traduction](assets/translation-job-detail.png)
1. Appuyez ou cliquez sur une ligne pour afficher le détail de cette ligne, en gardant à l’esprit qu’une ligne peut représenter plusieurs éléments de contenu à traduire.
1. Appuyez ou cliquez sur la case à cocher de sélection d’un élément de ligne pour afficher d’autres options, telles que la possibilité de le supprimer de la tâche ou de l’afficher dans les consoles Fragments de contenu ou Ressources.

![Options de tâche de traduction](assets/translation-job-options.png)

En règle générale, le contenu de la tâche de traduction commence à l’état **Version préliminaire** comme indiqué par la colonne **État** dans la fenêtre **Tâche de traduction**.

Pour démarrer la tâche de traduction, revenez à la présentation du projet de traduction et appuyez ou cliquez sur le bouton chevron situé en haut de la carte **Tâche de traduction** et sélectionnez **Démarrer**.

![Démarrage d’une tâche de traduction](assets/start-translation-job.png)

AEM communique maintenant avec votre configuration de traduction et votre connecteur pour envoyer le contenu au service de traduction. Vous pouvez afficher la progression de la traduction en revenant à la fenêtre **Tâche de traduction** et en affichant la colonne **État** des entrées.

![Tâche de traduction approuvée](assets/translation-job-approved.png)

Les traductions automatiques sont automatiquement renvoyées avec l’état **Approuvé**. La traduction humaine permet plus d&#39;interaction, mais dépasse la portée de ce parcours.

## Vérification du contenu traduit {#reviewing}

[Comme nous l&#39;avons vu précédemment, le contenu traduit par ](#using-translation-project) machine revient en AEM avec le statut  **** Approuvé puisque l&#39;hypothèse est que, puisque la traduction automatique est utilisée, aucune intervention humaine n&#39;est requise. Cependant, il est bien sûr toujours possible de consulter le contenu traduit.

Il vous suffit d’accéder à la tâche de traduction terminée et de sélectionner un élément de ligne en appuyant ou en cliquant sur la case à cocher. L’icône **Afficher dans le fragment de contenu** s’affiche dans la barre d’outils.

![Affichage dans le fragment de contenu](assets/reveal-in-content-fragment.png)

Appuyez ou cliquez sur cette icône pour ouvrir le fragment de contenu traduit dans sa console d’éditeur afin d’afficher les détails du contenu traduit.

![Un fragment de contenu traduit](assets/translated-content-fragment.png)

Vous pouvez modifier le fragment de contenu si nécessaire, à condition que vous disposiez des autorisations appropriées, mais la modification des fragments de contenu dépasse la portée de ce parcours. Pour plus d’informations sur cette rubrique, voir la section [Ressources supplémentaires](#additional-resources) à la fin de ce document.

Le travail du projet est de collecter dans un même endroit toutes les ressources liées à une traduction pour un accès facile et un aperçu clair. Cependant, comme vous pouvez le voir en affichant le détail d’un élément traduit, les traductions sont elles-mêmes renvoyées dans le dossier de ressources de la langue de traduction. Dans notre exemple ici

```text
/content/dam/wknd/es
```

Si vous accédez à ce dossier via **Navigation** -> **Fichiers** -> **Ressources**, le contenu traduit s’affiche.

![Structure de dossiers de contenu traduit](assets/translated-file-content.png)

AEM structure de traduction reçoit les traductions du connecteur de traduction, puis crée automatiquement la structure de contenu en fonction de la racine de langue et à l’aide des traductions fournies par le connecteur.

Il est important de comprendre que ce contenu n’est pas publié. Il reste sur l’instance de création d’AEM jusqu’à ce que vous décidiez qu’il est prêt à être publié. Nous allons voir comment procéder à l’étape suivante du parcours de localisation.

## Traduction humaine {#human-translation}

Si votre service de traduction fournit une traduction humaine, le processus de révision offre d’autres options. Par exemple, les traductions reviennent dans le projet avec le statut **Brouillon** et doivent être examinées et approuvées ou rejetées manuellement.

La traduction humaine dépasse le cadre de ce parcours de localisation. Pour plus d’informations sur cette rubrique, voir la section [Ressources supplémentaires](#additional-resources) à la fin de ce document.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de localisation sans interface utilisateur graphique, vous devez :

* Comprendre ce qu’est un projet de traduction.
* Vous pouvez créer de nouveaux projets de traduction.
* Utilisez des projets de traduction pour traduire votre contenu sans tête.

Tirez parti de ces connaissances et continuez votre parcours de localisation sans interface utilisateur AEM en consultant le document [Publier le contenu traduit](publish-content.md) dans lequel vous apprendrez à publier votre contenu traduit et comment mettre à jour ces traductions à mesure que le contenu racine de votre langue change.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de localisation sans interface utilisateur graphique en consultant le document [Publier le contenu traduit,](publish-content.md) les ressources facultatives supplémentaires ci-dessous approfondissent certains concepts mentionnés dans ce document, mais elles ne sont pas requises pour continuer sur le parcours sans interface.

* [Gestion des projets de traduction](/help/sites-cloud/administering/translation/managing-projects.md)  : découvrez les détails des projets de traduction et les fonctionnalités supplémentaires telles que les processus de traduction humaine et les projets multilingues.
