---
title: Utilisation des workflows de projet
description: Plusieurs workflows de projet sont directement disponibles.
exl-id: a5c9a6df-7def-43f3-b41b-524a4f4211e9
source-git-commit: 89972691dadb9573160ba16a220c5b7cb3ae9742
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 100%

---

# Utilisation des workflows de projet {#working-with-project-workflows}

Les workflows de projet disponibles et prêts à l’emploi sont les suivants :

* **Workflow d’approbation de projet** : Ce workflow vous permet d’attribuer le contenu à un utilisateur, de le passer en revue, puis de l’approuver.
* **Demander le lancement** : ce workflow demande un lancement.
* **Demander la page d’entrée** : ce workflow demande une page d’entrée.
* **Demander l’adresse électronique** : ce workflow demande une adresse électronique.
* **Gestion des actifs numériques (DAM) – Créer et traduire la copie et Gestion des actifs numériques (DAM) – Créer une copie de langue** : crée des fichiers binaires, des métadonnées et des balises traduits pour les ressources et les dossiers.

Selon le modèle de projet sélectionné, certains workflows sont disponibles :

|  | **Projet simple** | **Projet de traduction** |
|---|:-:|:-:|
| Workflow d’approbation de projet | x |  |
| Demander le lancement | x |  |
| Demander la page d’entrée | x |  |
| Adresse de demande | x |  |
| DAM Créer copie de langue&amp;ast; |  | x |
| DAM Créer et traduire copie de langue&amp;ast; |  | x |

>[!NOTE]
>
>&amp;ast; Ces workflows ne sont pas lancés via la mosaïque **Workflow** dans les projets. Reportez-vous à la section [Création de copies de langue pour les ressources](/help/sites-cloud/administering/translation/managing-projects.md).

Les étapes permettant de lancer et de terminer les workflows sont identiques quel que soit le workflow choisi. Seules les étapes changent.

Vous commencez un workflow directement dans les projets (à l’exception de Gestion des actifs numériques (DAM) – Créer une copie de langue ou Gestion des actifs numériques (DAM) – Créer et traduire la copie de langue). Les informations sur les tâches en attente d’un projet sont répertoriées dans la mosaïque **Tâches**. Les notifications correspondant aux tâches à achever s’affichent en regard de l’icône d’utilisateur.

Pour plus d’informations sur l’utilisation des workflows dans AEM, reportez-vous aux sections suivantes :

* [Participation aux workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Application de workflows aux pages](/help/sites-cloud/authoring/workflows/applying.md)
* [Configuration de workflow](/help/sites-cloud/administering/workflows-administering.md)

Cette section décrit les workflows disponibles pour les projets.

## Workflow d’approbation de projet {#project-approval-workflow}

Dans le workflow d’approbation de projet, vous attribuez du contenu à un utilisateur et passez en revue ce contenu, puis vous l’approuvez.

1. Dans votre projet Simple, sélectionnez le signe **`+`** dans la mosaïque **Workflows**, puis sélectionnez **Workflow d’approbation de projet**.
1. Entrez un titre et sélectionnez la personne à laquelle l’affecter dans la liste Équipe. Le cas échéant, entrez une description, le chemin d’accès au contenu, la priorité de tâche et la date d’échéance.

   ![Demande d’approbation](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Cliquez sur **Créer**. Le workflow commence. La tâche apparaît dans la mosaïque **Tâches**.

## Workflow Demander le lancement {#request-launch-workflow}

Ce workflow vous permet de demander un lancement.

1. Dans votre projet simple, sélectionnez l’option de connexion **+** dans la mosaïque **Workflows**, puis sélectionnez **Workflow Demander le lancement**.
1. Entrez le titre du lancement et indiquez le chemin d’accès à la source du lancement. Vous pouvez également ajouter une description et une date active, le cas échéant. Sélectionnez l’option Hériter des données actives de la page source ou excluez les sous-pages selon la manière dont le lancement doit se produire.

   ![Demander le lancement](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Cliquez sur **Créer**. Le workflow commence. Le workflow apparaît dans la liste **Workflows** (cliquez sur les points de suspension **...** de la mosaïque **Workflows** pour accéder à cette liste).

## Workflow Créer (et traduire) la copie de la langue pour les ressources {#create-and-translate-language-copy-workflow-for-assets}

Les workflows **Créer une copie de langue** et **Créer et traduire la copie de langue** sont présentés en détail dans la section [Création de copies de langue pour les ressources](/help/assets/translate-assets.md).
