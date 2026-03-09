---
title: Prise en main de l’agent de modernisation de l’expérience pour les projets de création AEM
description: Découvrez les étapes de configuration spécifiques requises pour les projets de création AEM lors de la prise en main de l’agent de modernisation à l’aide de la console de modernisation de l’expérience.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: a1b2c3d4-e5f6-4789-a012-3456789abcde
source-git-commit: df23c3a4c497943135f8719425225526ae14aa92
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 1%

---


# Prise en main de l’agent de modernisation de l’expérience pour les projets de création AEM {#getting-started-aem-authoring}

Pour les projets de création AEM à l’aide de l’éditeur universel, la préparation de l’agent de modernisation de l’expérience diffère du flux Edge Delivery standard. Ce document couvre ces différences de configuration. Une fois les étapes ci-dessous terminées, suivez le guide principal [Prise en main de l’agent de modernisation de l’expérience](getting-started.md).

## Création De Votre Référentiel De Projet Edge Delivery Services {#create-repo}

1. Utilisez le référentiel [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk) comme modèle (et non comme modèle standard de Edge Delivery Services).
1. Suivez le [tutoriel de l’éditeur universel](https://www.aem.live/developer/ue-tutorial) pour configurer votre référentiel.
   * Arrêtez lorsque l’on vous demande de créer un site dans AEM.
1. Supprimez `paths.json` et validez cette modification dans `main`.
1. Ajoutez l’application [AEM Code Connector](https://github.com/apps/aem-code-connector/installations/select_target) à votre référentiel.
   * Cela permet à la console d’inspecter votre code.

## Création d’un site dans AEM {#create-site}

1. Dans la console AEM Sites, sélectionnez **Créer** > **Site à partir d’un modèle**.
1. Sélectionnez le **site AEM avec modèle Edge Delivery Services**.
   * Vous ne le voyez pas répertorié ? [Installez le modèle.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)
1. Conservez le **nom** du site (et non le titre) tel qu’il est fourni.
   * Le nom du site est utilisé comme identifiant unique.
   * Le titre peut être modifié pour l’affichage.
1. Cliquez sur **Créer**.
   * Vous êtes redirigé vers la page Sites.
   * Actualisez la page si le nouveau site n’apparaît pas immédiatement.
1. Si vous ne l’avez pas déjà fait lors de la [configuration de votre référentiel](#create-repo) mettez à jour `fstab.yaml` afin qu’il pointe vers votre hôte AEM, le propriétaire Git et le référentiel Git et validez ces modifications dans `main`.
   * Voir [Configurer la source de contenu](/help/implementing/cloud-manager/edge-delivery/configure-content-source.md) pour obtenir des instructions.

## Continuez avec les étapes de prise en main standard {#continue}

Une fois les étapes ci-dessus terminées, vous pouvez poursuivre avec le guide de prise en main standard pour commencer à migrer votre contenu.

![Import de contenu](assets/content-import.png)

Suivez ces étapes à partir du guide standard.

1. [Préparation d’un référentiel GitHub Edge Delivery](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#prepare-repo)
1. [Ouvrir la console de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#open-console)
1. [Connexion de votre référentiel GitHub](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#connect-repo)
1. [Démarrer l&#39;invite](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#start-prompting)

![ Contenu importé ](assets/content-imported-aem-authoring.png)

Une fois ces étapes effectuées pour migrer le contenu, procédez comme suit.

## Valider le contenu {#validate-content}

Validez le contenu de la page sélectionnée dans le panneau d’aperçu. Toutes les erreurs s’affichent en cliquant sur le bouton **Erreurs**.
Poursuivez votre conversation avec l’agent pour corriger les erreurs. Utilisez la fonction **Ajouter à la conversation** pour cibler des correctifs sur des éléments spécifiques de la page, des fichiers d’analyse ou des fichiers de transformateur.

![Discussion contextuelle](assets/contextual-chat.png)

## Chargement du contenu {#upload-content}

Pour charger votre contenu vers AEM :

1. Assurez-vous que vous êtes dans la vue **Contenu** et cliquez sur le bouton **Charger le contenu** en haut à droite.
1. Dans la boîte de dialogue **Créer un package de contenu**, choisissez les pages à inclure dans le package.
   * Vous pouvez éventuellement saisir un **Nom du package** (par défaut, le nom du site s’il est vide).
   * Utilisez **Tout sélectionner** **Effacer la sélection**, **Tout développer** ou **Tout réduire** pour gérer la liste.
1. Cliquez sur **Créer un package**.

   ![Créer un package de contenu - Sélection des pages et création](assets/content-package.png)

1. Une fois le package créé, la boîte de dialogue **Télécharger le package de contenu** indique que le package est prêt.
   1. Vous pouvez **Télécharger le package** pour l’enregistrer localement ou procéder au chargement.
   1. Sous **Télécharger vers AEM**, confirmez le **site AEM** et l’**hôte AEM** (pré-renseigné à partir des paramètres du projet).
      * Si vous le souhaitez, laissez la case **Télécharger des images** cochée pour inclure des images.
   1. Cliquez sur **Télécharger vers AEM**.

   ![Package prêt à être téléchargé sur AEM ou téléchargé](assets/upload-package-start.png)

1. La boîte de dialogue affiche la progression du chargement au fur et à mesure que les pages et les ressources sont envoyées à AEM. Une fois le chargement terminé, un message de réussite et le journal de chargement s’affichent. Cliquez sur **Fermer** pour fermer la boîte de dialogue.

   ![Progression et fin du chargement dans AEM](assets/upload-package-complete.png)

Le contenu que vous avez importé se trouve désormais dans AEM. Continuez avec [Modifications du code push](getting-started.md#push-code-changes) dans le guide de prise en main principal.

## Ressources supplémentaires {#additional-resources}

* [Prise en main de l’agent de modernisation de l’expérience](getting-started.md) - Workflow complet comprenant la console, l’invite, le chargement et la prévisualisation
* [Console de modernisation de l’expérience](console.md) - Référence de la console
* [tutoriel de l’éditeur universel](https://www.aem.live/developer/ue-tutorial) - Configuration d’un projet de création et d’éditeur universel AEM
* [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk) - Référentiel de modèles pour les projets de création AEM et d’éditeur universel
