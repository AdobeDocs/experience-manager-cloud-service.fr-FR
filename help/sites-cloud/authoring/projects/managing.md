---
title: Gestion de projets
description: La console Projets vous permet d’organiser un projet en regroupant les ressources dans une seule entité à laquelle vous pouvez accéder et que vous pouvez gérer.
exl-id: be4616e7-18bc-4b2d-89f6-d04178ac7f3a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 82%

---

# Gestion de projets {#managing-projects}

Les projets vous permettent d’organiser votre projet en regroupant les ressources dans une seule entité.

Dans la console **Projets**, vous accédez à vos projets et agissez en conséquence :

![Console Projets](/help/sites-cloud/authoring/assets/projects-console.png)

Dans Projets, vous pouvez créer un projet et lui associer des ressources, ou bien supprimer un projet ou des liens vers des ressources. Vous pouvez ouvrir une mosaïque pour afficher son contenu et ajouter des éléments à cette dernière. Cette rubrique décrit ces procédures.

## Création d’un projet {#creating-a-project}

AEM fournit les modèles prêts à l’emploi suivants à utiliser lors de la création d’un projet :

* Projet simple
* Projet de média
* Projet de traduction

<!-- Hiding product photoshoot via cqdoc-18072 as it is not available in Skyline.
* Product Photo Shoot Project 
-->

Les étapes de création d’un projet sont identiques d’un projet à l’autre. La différence entre les types de projets porte sur les [rôles utilisateur](/help/sites-cloud/authoring/projects/overview.md) et les [workflows](/help/sites-cloud/authoring/projects/workflows.md) disponibles. Pour créer un projet :

1. Dans **Projects**, sélectionnez **Create** pour ouvrir l’assistant **Create Project** :
1. Sélectionnez le modèle, puis cliquez sur **Suivant**.

   ![Création d’un projet](/help/sites-cloud/authoring/assets/projects-create.png)

1. Définissez le **titre** et la **description**, puis ajoutez une **miniature** s’il y a lieu. Vous pouvez également ajouter ou supprimer des utilisateurs et utilisatrices et le groupe auquel ils appartiennent. En outre, cliquez sur **Avancé** pour ajouter un nom utilisé dans l’URL.

   ![Ajout des détails du projet](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Sélectionnez **Créer**. Le message de confirmation vous demande si vous voulez ouvrir votre projet ou revenir à la console.

### Association de ressources à un projet {#associating-resources-with-your-project}

Comme les projets vous permettent de regrouper des ressources dans une seule entité, vous pouvez associer des ressources à votre projet. Ces ressources sont appelées **Mosaïques**. Les types de ressources que vous pouvez ajouter sont décrits à la section [Mosaïques de projet](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

Pour associer des ressources à votre projet :

1. Ouvrez votre projet à partir de la console **Projets**.
1. Sélectionnez **Ajouter une mosaïque** et sélectionnez la mosaïque à lier à votre projet. Vous pouvez sélectionner plusieurs types de mosaïque.

   ![Ajout d’une mosaïque à un projet](/help/sites-cloud/authoring/assets/projects-add-tile.png)

   >[!NOTE]
   >
   >Les mosaïques de projet qui peuvent être associées à un projet sont décrites en détail dans la rubrique [Mosaïques de projet](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

1. Sélectionnez **Créer**. La ressource est désormais associée à votre projet et vous pouvez y accéder à partir du projet.

### Suppression d’un projet ou d’un lien vers une ressource {#deleting-a-project-or-resource-link}

La méthode permettant de supprimer un projet à partir de la console est la même que celle employée pour supprimer une ressource liée de votre projet :

1. Accédez à l’emplacement concerné :

   * Pour supprimer un projet, accédez au niveau supérieur de la console **Projets**.
   * Pour supprimer un lien vers une ressource dans un projet, ouvrez le projet dans la console **Projets**.

1. Activez le mode de sélection en cliquant sur **Sélectionner** et sélectionnez le projet ou le lien vers une ressource.
1. Sélectionnez **Supprimer**.

1. Vous devez confirmer la suppression dans une boîte de dialogue. Si cette opération est confirmée, le projet ou le lien vers la ressource est supprimé. Sélectionnez **Désélectionner** pour quitter le mode de sélection.

>[!NOTE]
>
>Lorsque vous créez le projet et ajoutez des utilisateurs aux différents rôles, les groupes associés au projet sont automatiquement créés pour gérer les autorisations associées. Par exemple, un projet appelé Myproject aurait trois groupes **Myproject Owners**, **Myproject Editors**, **Myproject Observators**. Toutefois, si le projet est supprimé, ces groupes ne sont pas automatiquement supprimés. Un administrateur doit supprimer manuellement les groupes dans **Outils** > **Sécurité** > **Groupes**.

### Ajout d’éléments à une mosaïque {#adding-items-to-a-tile}

Dans certaines mosaïques, vous pouvez ajouter plusieurs éléments. Par exemple, plusieurs workflows ou expériences peuvent s’exécuter à la fois.

Pour ajouter des éléments à une mosaïque, procédez comme suit :

1. Dans **Projects**, accédez au projet et sélectionnez le chevron inférieur sur la mosaïque à laquelle vous souhaitez ajouter un élément.

   ![Ajout d’un élément à une mosaïque](/help/sites-cloud/authoring/assets/project-workflows.png)

1. Ajoutez un élément à la mosaïque comme vous le feriez lors de la création d’une mosaïque. Pour plus d’informations, voir [Mosaïques de projet](/help/sites-cloud/authoring/projects/overview.md#project-tiles) . Dans cet exemple, un autre workflow a été ajouté.

### Ouverture d’une mosaïque {#opening-a-tile}

Vous pouvez afficher les éléments inclus dans une mosaïque actuelle ou modifier ou supprimer des éléments dans la mosaïque.

Pour ouvrir une mosaïque afin d’afficher ou de modifier des éléments :

1. Dans la console Projets, sélectionnez l’icône représentant des points de suspension (..) au bas de la carte.

   ![Ouverture d’une mosaïque](/help/sites-cloud/authoring/assets/project-links.png)

1. AEM répertorie les éléments de cette mosaïque. Vous pouvez passer en mode de sélection pour modifier ou supprimer les éléments.

   ![Mosaïque ouverte](/help/sites-cloud/authoring/assets/projects-add-link.png)

## Affichage des statistiques d’un projet {#viewing-project-statistics}

Vous pouvez afficher les statistiques d’un projet dans la console des **Projets**.

### Affichage d’une chronologie de projet {#viewing-a-project-timeline}

La chronologie du projet fournit des informations sur le moment auquel les ressources du projet ont été utilisées pour la dernière fois. Pour afficher la chronologie du projet, sélectionnez **Chronologie**, puis passez en mode de sélection et sélectionnez le projet. Les ressources sont affichées dans le volet de gauche. Sélectionnez **Chronologie** pour revenir à la console **Projets**.

![Chronologie du projet](/help/sites-cloud/authoring/assets/projects-timeline.png)

### Affichage de projets actifs/inactifs {#viewing-active-inactive-projects}

Pour basculer entre vos projets actifs et inactifs, dans la console **Projets**, cliquez sur **Activer/désactiver les projets actifs**. Si l’icône est accompagnée d’une coche, cela signifie qu’elle affiche les projets actifs.

![Bouton Activer/désactiver les projets actifs](/help/sites-cloud/authoring/assets/projects-active.png)

Si l’icône est accompagnée d’une croix (x), elle affiche les projets inactifs.

![Bouton Activer/désactiver les projets inactifs](/help/sites-cloud/authoring/assets/projects-inactive.png)

## Activation/désactivation de projets {#making-projects-inactive-or-active}

Vous pouvez désactiver un projet que vous avez terminé, mais dont vous souhaitez conserver les informations.

Pour activer/désactiver un projet :

1. Dans la console **Projets**, ouvrez votre projet, puis recherchez la mosaïque **Informations sur le projet**.

   >[!NOTE]
   >
   >Vous devrez peut-être ajouter cette mosaïque si elle ne figure pas déjà dans votre projet. Voir [Ajout de mosaïques](#adding-items-to-a-tile).

1. Sélectionnez **Modifier**.
1. Remplacez le sélecteur **Actif** par **Inactif** (ou inversement).

   ![Activation d’un projet](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Sélectionnez **Terminé** pour enregistrer vos modifications.
