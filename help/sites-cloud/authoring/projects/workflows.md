---
title: Utilisation des workflows de projet
description: Plusieurs workflows de projet sont directement disponibles.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Utilisation des workflows de projet {#working-with-project-workflows}

Les workflows de projet disponibles et prêts à l’emploi sont les suivants :

* **Processus** d’approbation de projet : ce processus vous permet d’affecter du contenu à un utilisateur, de le consulter, puis de l’approuver.
* **Lancement** de la demande : processus qui demande un lancement.
* **Demande de page** d&#39;entrée : ce processus demande une page d&#39;entrée.
* **Demander l’adresse électronique** - ce workflow demande une adresse électronique.
* **Gestion des actifs numériques – Créer et traduire la copie et Gestion des actifs numériques – Créer une copie de langue** : crée des fichiers binaires, des métadonnées et des balises traduits pour les ressources et les dossiers.

Selon le modèle de projet sélectionné, certains workflows sont disponibles :

|  | **Projet simple** | **Projet de média** | **Projet de traduction** |
|---|:-:|:-:|:-:|
| Demander la copie |  | x |  |
| Séance photo du produit |  | x |  |
| Approbation de projet | x |  |  |
| Lancement de la demande | x |  |  |
| Demander la page d’entrée | x |  |  |
| Adresse de demande | x |  |  |
| DAM Create Language Copy&amp;ast; |  |  | x |
| DAM Créer et traduire la copie et la traduction de langue;ast; |  |  | x |

>[!NOTE]
>
>&amp;ast; These workflows are not started from the **Workflow** tile in Projects. Reportez-vous à la section Création de copies de langue pour les ressources. 
<!--
>&ast; These workflows are not started from the **Workflow** tile in Projects. See [Creating Language Copies for Assets.](/help/sites-administering/tc-manage.md)
-->

Les étapes permettant de lancer et de terminer les workflows sont identiques quel que soit le workflow choisi. Seules les étapes changent.

Vous commencez un workflow directement dans les projets (à l’exception de Gestion des actifs numériques – Créer une copie de langue ou Gestion des actifs numériques – Créer et traduire la copie de langue). Les informations sur les tâches en attente d’un projet sont répertoriées dans la mosaïque **Tâches**. Les notifications correspondant aux tâches à achever s’affichent en regard de l’icône d’utilisateur.

Pour plus d’informations sur l’utilisation des processus dans AEM, voir :

* [Participation aux workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Application de workflows aux pages](/help/sites-cloud/authoring/workflows/applying.md)
* Configuration de workflow<!--* [Configuring workflows](/help/sites-administering/workflows.md)--> 

Cette section décrit les workflows disponibles pour les projets.

## Workflow de demande de copie {#request-copy-workflow}

Ce workflow vous permet de demander un manuscrit à un utilisateur, puis de l’approuver. Pour démarrer le workflow de demande de copie :

1. Dans votre projet de média, sélectionnez l’option de connexion **+** dans la mosaïque **Workflows**, puis sélectionnez le workflow **Demander la copie**.
1. Saisissez un titre de manuscrit et un bref résumé de votre demande. Le cas échéant, entrez un nombre de mots cible, la priorité de la tâche et une date d’échéance.

   ![Processus de demande de copie](/help/sites-cloud/authoring/assets/projects-request-copy.png)

1. Cliquez sur **Créer**. Le workflow commence. La tâche apparaît dans la mosaïque **Tâches**.

   ![Copie de demande ajoutée](/help/sites-cloud/authoring/assets/projects-request-copy-add.png)

## Workflow d’approbation de projet {#project-approval-workflow}

Dans le workflow d’approbation de projet, vous attribuez du contenu à un utilisateur et passez en revue ce contenu, puis vous l’approuvez.

1. In your Simple project, select the **`+`** sign in the **Workflows** tile and select **Project Approval Workflow**.
1. Entrez un titre et sélectionnez la personne à laquelle l’affecter dans la liste Équipe. Le cas échéant, entrez une description, le chemin d’accès au contenu, la priorité de tâche et la date d’échéance.

   ![Demande d’approbation](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Cliquez sur **Créer**. Le workflow commence. La tâche apparaît dans la mosaïque **Tâches**.

   ![Demande d’approbation ajoutée](/help/sites-cloud/authoring/assets/projects-approval-add.png)

## Worfklow Lancement de la demande {#request-launch-workflow}

Ce workflow vous permet de demander un lancement.

1. Dans votre projet simple, sélectionnez l’option de connexion **+** dans la mosaïque **Workflows**, puis sélectionnez **Worfklow Lancement de la demande**.
1. Entrez le titre du lancement et indiquez le chemin d’accès à la source du lancement. Vous pouvez également ajouter une description et une date active, le cas échéant. Sélectionnez l’option Hériter des données actives de la page source ou excluez les sous-pages selon la manière dont le lancement doit se produire.

   ![Lancement de la demande](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Cliquez sur **Créer**. Le workflow commence. **Le flux de travaux s’affiche dans la liste** Processus **(cliquez sur ellipses**... sur le volet **Processus** pour accéder à cette liste).

## Workflow Créer (et traduire) la copie de la langue pour les ressources {#create-and-translate-language-copy-workflow-for-assets}

The **Create Language Copy** and the **Create and Translate Language Copy** workflows are covered in detail in creating language copies for assets.
