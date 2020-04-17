---
title: Projets
description: Les projets vous permettent de regrouper des ressources dans une seule entité dont l’environnement commun et partagé facilite la gestion de vos projets.
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Projets {#projects}

Les projets permettent de regrouper des ressources dans une seule entité. Un environnement commun et partagé permet de gérer facilement vos projets. Dans AEM, les types de ressources que vous pouvez associer à un projet s’appellent des mosaïques. Les mosaïques peuvent inclure des informations de projet et d’équipe, des ressources numériques, des workflows et d’autres types d’informations, comme le précise en détail la section [Mosaïques de projet](#project-tiles).

>[!CAUTION]
>
>Pour que les utilisateurs participant à des projets voient d’autres utilisateurs/groupes lorsqu’ils se servent de fonctionnalités de la console Projets comme créer des projets, créer des tâches/workflows, afficher et contrôler l’équipe, ils doivent disposer d’un accès en lecture à `/home/users` et à `/home/groups`. Pour ce faire, le plus facile consiste à octroyer au groupe **projects-users** un accès en lecture à `/home/users` et à `/home/groups`.

En tant qu’utilisateur, vous pouvez effectuer les opérations suivantes :

* Créer des projets
* Associer du contenu et des dossiers de ressources à un projet
* Supprimer des projets
* Supprimer les liens de contenu d’un projet

Reportez-vous aux rubriques supplémentaires suivantes :

* [Gestion de projets](/help/sites-cloud/authoring/projects/managing.md)
* [Utilisation de tâches](/help/sites-cloud/authoring/projects/tasks.md)
* [Utilisation des workflows de projet](/help/sites-cloud/authoring/projects/workflows.md)

## Console Projets {#projects-console}

Dans AEM, la console Projets permet d’accéder à vos projets et de les gérer.

![Console Projets](/help/sites-cloud/authoring/assets/projects-console.png)

* Sélectionnez **Chronologie**, puis un projet pour afficher sa chronologie.
* Cliquez/appuyez sur **Sélectionner** pour passer en mode de sélection.
* Cliquez sur **Créer** pour ajouter des projets.
* L’option **Activer/désactiver les projets actifs** vous permet de basculer entre tous les projets et uniquement ceux qui sont actifs.
* L’option **Afficher la vue Statistiques** permet d’afficher les statistiques de projet relatives à la réalisation de tâches.

## Mosaïques de projet   {#project-tiles}

Dans la console Projets, vous devez associer différents types d’informations à vos projets. Elles sont connues sous le nom de **mosaïques**. Toutes les mosaïques, ainsi que le type d’informations qu’elles contiennent, sont décrites dans cette section.

Vous pouvez associer les mosaïques suivantes à votre projet. Chacune d’elles est décrite dans les sections ci-après :

* Ressources et collections de ressources
* Expériences
* Liens
* Informations sur le projet
* Équipe
* Pages d’entrée
* Courriels
* Workflows
* Lancements
* Tâches

### Ressources   {#assets}

Dans la mosaïque **Ressources**, vous pouvez regrouper tous les éléments dont vous avez besoin pour un projet particulier.

![Mosaïque Ressources](/help/sites-cloud/authoring/assets/projects-assets-tile.png)

Vous chargez des ressources directement dans la mosaïque. En outre, vous pouvez créer des visionneuses d’images, des visionneuses à 360° ou des visionneuses de médias mixtes si vous avez installé le complément Médias dynamiques.

![Visionneuse d’images](/help/sites-cloud/authoring/assets/projects-image-sets.png)

### Collections de ressources {#asset-collections}

Comme avec les ressources, vous pouvez ajouter des collections de ressources directement à votre projet. Vous définissez les collections dans AEM Assets. <!--Similar to assets, you can add [asset collections](/help/assets/managing-collections-touch-ui.md) directly to your project. You define collections in Assets.-->

![Collection de ressources](/help/sites-cloud/authoring/assets/projects-asset-collections.png)

Ajoutez une collection en cliquant sur **Ajouter une collection** et en sélectionnant une collection dans la liste.

### Expériences   {#experiences}

La mosaïque **Expériences** permet d’ajouter au projet une application mobile, un site web ou une publication.

![Expériences](/help/sites-cloud/authoring/assets/project-experiences.png)

Les icônes indiquent le type d’expérience qui est représenté : site web, application mobile ou publication. Ajoutez des expériences en cliquant sur le signe + ou en cliquant sur **Ajouter une expérience** et en sélectionnant le type d’expérience.

![Ajout d’une expérience](/help/sites-cloud/authoring/assets/projects-add-experience.png)

Sélectionnez le chemin des miniatures, et le cas échéant, modifiez la miniature de l’expérience. Les expériences sont regroupées dans la mosaïque **Expériences**.

### Liens {#links}

La mosaïque Liens permet d’associer des liens externes à votre projet.

![Liens](/help/sites-cloud/authoring/assets/project-links.png)

Vous pouvez donner au lien un nom facile à reconnaître et changer de miniature.

![Ajout d’un lien](/help/sites-cloud/authoring/assets/projects-add-link.png)

### Informations sur le projet {#project-info}

La mosaïque Informations sur le projet fournit des informations générales sur le projet, notamment sa description, son état (actif ou inactif), son échéance et ses membres. En outre, vous pouvez ajouter une miniature de projet qui sera visible dans la page principale Projets.

![Informations sur le projet](/help/sites-cloud/authoring/assets/project-info.png)

Des membres d’équipe peuvent être attribués et supprimés de cette mosaïque (ou leurs rôles peuvent être modifiés) et de la mosaïque Équipe.

![Ajout de membres de l’équipe au projet](/help/sites-cloud/authoring/assets/projects-add-team.png)

### Tâche de traduction {#translation-job}

La mosaïque Tâche de traduction est l’endroit où vous commencez une traduction et où vous pouvez voir l’état de toutes vos traductions. Pour configurer votre traduction, voir Création de projets de traduction. <!--To set up your translation, see [Creating Translation Projects](/help/assets/translation-projects.md).-->

![Tâche de traduction](/help/sites-cloud/authoring/assets/projects-translation-job.png)

Cliquez sur les points de suspension en bas de la carte **Tâche de traduction** pour afficher les ressources du workflow de traduction. La liste des tâches de traduction contient également des entrées pour les balises et les métadonnées des ressources. Ces entrées indiquent que les métadonnées et les balises des ressources sont également traduites.

![Détails de la tâche de traduction](/help/sites-cloud/authoring/assets/projects-translation-job-detail.png)

### Équipe {#team}

Dans cette mosaïque, vous pouvez définir les membres de l’équipe de projet. En mode d’édition, vous pouvez saisir le nom des membres d’équipe et attribuer des rôles utilisateur.

![Mosaïque Équipe](/help/sites-cloud/authoring/assets/projects-team-tile.png)

Vous pouvez ajouter et supprimer des membres de l’équipe. De plus, vous pouvez modifier le [rôle utilisateur](#user-roles-in-a-project) attribué à chaque membre de l’équipe.

![Ajout d’une équipe à partir de la liste](/help/sites-cloud/authoring/assets/projects-add-team-list.png)

### Workflows {#workflows}

Vous pouvez configurer votre projet pour qu’il suive certains workflows. Si des workflows sont actifs, leur état s’affiche dans la mosaïque **Workflows** de la console Projets.

![Workflows](/help/sites-cloud/authoring/assets/project-workflows.png)

Vous pouvez configurer votre projet pour qu’il suive certains workflows. Selon le type de projet que vous sélectionnez, différents workflows sont disponibles.

Ils sont décrits à la section [Utilisation des workflows de projet](/help/sites-cloud/authoring/projects/workflows.md).

### Lancements {#launches}

La mosaïque Lancements présente tous les programmes qui ont été demandés avec un [workflow de demande de lancement](/help/sites-cloud/authoring/projects/workflows.md).

![Lancements](/help/sites-cloud/authoring/assets/project-launches.png)

### Tâches {#tasks}

Les tâches vous permettent de surveiller l’état de toutes les activités associées à un projet, y compris des workflows. Les tâches sont décrites en détail à la section [Utilisation des tâches](/help/sites-cloud/authoring/projects/tasks.md).

![Tâches](/help/sites-cloud/authoring/assets/projects-tasks.png)

## Modèles de projet {#project-templates}

AEM est fourni avec trois modèles prêts à l’emploi :

* Un projet simple : un modèle de référence pour tous les projets auxquels les autres catégories ne sont pas adaptées. Il comprend trois rôles de base (propriétaires, éditeurs et observateurs) et quatre workflows (Approbation de projet, Demander un lancement, Demander la page d’entrée et Demander un courrier électronique).
* Un projet de média : un modèle de référence pour des activités multimédias. Il comprend plusieurs rôles de projet relatifs aux médias (photographes, éditeurs, rédacteurs, concepteurs, propriétaires et observateurs). Il comprend également deux workflows liés au contenu multimédia : Demander la copie (pour demander et réviser du texte) et Projet de séance photo du produit (pour gérer des photos relatives à des produits).
* Un projet de traduction : modèle de référence pour gérer les activités liées à la traduction. Il prévoit trois rôles de base (propriétaires, éditeurs et observateurs). Il comprend deux workflows accessibles dans l’interface utilisateur Workflows. <!--* [A translation project](/help/sites-administering/translation.md) - A reference sample for managing translation related activities. It includes three basic roles (Owners, Editors, and Observers). It includes two workflows that are accessed in the Workflows user interface.-->

En fonction du modèle sélectionné, plusieurs options s’offrent à vous, notamment en termes de rôles utilisateur et de workflows.

## Rôles utilisateur dans un projet   {#user-roles-in-a-project}

Différents rôles utilisateur sont définis dans un modèle de projet et utilisés pour deux principales raisons :

1. Autorisations. Les rôles utilisateur peuvent faire partie de l’une des trois catégories répertoriées : Observateur, Éditeur, Propriétaire. Par exemple, un photographe ou un rédacteur aura les mêmes privilèges qu’un éditeur. Les autorisations déterminent ce que les utilisateurs peuvent faire avec le contenu d’un projet.
1. Workflows. Les workflows déterminent l’utilisateur associé à telles ou telles tâches d’un projet. Les tâches peuvent être associées à un rôle de projet. Par exemple, une tâche peut être attribuée à des photographes, de sorte que tous les membres de l’équipe disposant du rôle Photographe se la voient attribuer.

Pour vous permettre de gérer les autorisations de sécurité et de contrôle, tous les projets prennent en charge les rôles par défaut suivants :

| Rôle | Description | Autorisations | Appartenance à un groupe |
|---|---|---|---|
| Observateur | Un utilisateur disposant de ce rôle peut afficher les détails du projet, y compris son état. | Droits en lecture seule sur un projet | `workflow-users` groupe |
| Éditeur | Un utilisateur disposant de ce rôle peut télécharger et modifier le contenu d’un projet. | Accès en lecture et en écriture à un projet, aux métadonnées associées et aux ressources connexes ; droits permettant à l’utilisateur de charger une liste de plans ou une séance photo et de passer en revue et d’approuver des ressources ; droits en écriture sur /etc/commerce ; droits de modification sur un projet spécifique | groupe workflow-users |
| Propriétaire | Un utilisateur disposant de ce rôle peut lancer un projet. Le propriétaire peut créer un projet, lancer une tâche pour un projet et déplacer les ressources approuvées vers le dossier Production. Toutes les autres tâches de projet peuvent également être visualisées et implémentées par le propriétaire. | Droits en écriture sur `/etc/commerce` | groupe `dam-users` (pour pouvoir créer un projet) groupe project-administrators (pour pouvoir déplacer des ressources) |

>[!NOTE]
>
>Lorsque vous créez un projet et ajoutez des utilisateurs pour les différents rôles, des groupes liés au projet sont automatiquement créés pour gérer les autorisations correspondantes. Par exemple, un projet nommé Monprojet serait associé à trois groupes **Propriétaires Monprojet**, **Editeurs Monprojet**, **Observateurs Monprojet**. Cependant, si le projet est supprimé, ces groupes ne le sont pas automatiquement. Un administrateur doit supprimer manuellement les groupes dans **Outils** > **Sécurité** > **Groupes**.
