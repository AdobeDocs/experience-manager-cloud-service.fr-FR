---
title: Tâche de mise à jour du contenu
description: Découvrez la tâche de mise à jour de contenu de Brand Experience Agent et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: a3b00916c0d949fe9fac50bc0c3056b0a1b05358
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 2%

---


# Tâche de mise à jour du contenu {#content-update}

La tâche de mise à jour de contenu de [Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) automatise la production de contenu afin d’accélérer les tâches quotidiennes pour Adobe Experience Manager (AEM) as a Cloud Service et Edge Delivery Services.

## Vue d’ensemble {#overview}

La tâche de mise à jour du contenu met à jour le contenu existant, y compris les fragments de contenu, les pages, les formulaires et les ressources. La tâche peut effectuer des actions telles que la mise à jour, la suppression, le remplacement ou l’ajout d’éléments de contenu pour que les expériences restent exactes et à jour. Les entrées peuvent être des descriptions en langage naturel et, lorsqu’elles sont utilisées avec des PDF et des captures d’écran Jira, elles peuvent également fournir des entrées.

La tâche de mise à jour de contenu transforme les détails que vous fournissez, en langage naturel ou visuel, en mises à jour de contenu sur votre page. Vous fournissez l’URL d’une page qui doit être mise à jour, ainsi que des détails sur ce qui doit être mis à jour et les compétences de l’agent terminent votre tâche. Utilisée avec Adobe Experience Manager (AEM) as a Cloud Service, la tâche crée un [launch](/help/sites-cloud/authoring/launches/overview.md) afin que vous puissiez consulter les mises à jour avant l’application. Lorsqu’elle est utilisée avec la création de documents, la tâche crée une [version](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#).

## Fonctionnalités {#capabilities}

Vous pouvez accéder à la compétence de mise à jour de contenu à partir de :

* [L’assistant AI](#ai-assistant)
* [Jira](#jira)

## Assistant IA {#ai-assistant}

Vous pouvez accéder au traitement dans AEM à partir de l’assistant AI.

Ouvrez l’assistant d’IA depuis [`experience.adobe.com`,](https://experience.adobe.com) puis commencez à interagir en spécifiant votre invite en langage naturel à l’aide du champ `Ask AI Assistant anything` :

![Tâche de mise à jour du contenu](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### Configuration de l’URL de publication {#configuring-the-publish-url}

Pour utiliser une URL de publication (publique), une configuration unique doit être effectuée :

* Conditions préalables :

   * Pour effectuer la configuration, l’utilisateur doit disposer des droits d’administrateur système ou d’administrateur de produit.

* Configuration :

   1. Appelez la compétence Mise à jour de contenu en demandant une mise à jour de contenu pour l’URL.
   1. L’assistant vous guidera à travers la configuration, en vous posant un certain nombre de questions.
   1. Une fois l’opération terminée, l’URL de publication est configurée et peut être utilisée.

Par exemple :

![Compétences de mise à jour de contenu - Configuration de l’URL de publication](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### Invites {#prompts}

Pour lancer les mises à jour de contenu, vous pouvez donner un large éventail d’invites en langage naturel. Vous devez spécifier l’URL publique (publication) ou l’URL de l’environnement de création de la page que vous souhaitez mettre à jour. Certains des verbes pris en charge, mais pas tous ; remplacez, mettez à jour, supprimez, modifiez, modifiez, modifiez, ajustez, supprimez.

>[!NOTE]
>
>Les chargements de fichiers peuvent être utilisés lors de l’interaction à l’aide de [Jira](#jira), mais ne sont pas pris en charge avec l’assistant AI.

### Exemples d’invites {#sample-prompts}

Voici quelques exemples d’invites :

* lors de `<your-publish-URL>` mise à jour : « Votre café parfait est à quatre questions ! » à « Ton café, ton chemin ! »
* sur `<your-author-env-URL>`, remplacez l’image de « holdingcup.png » par « stairhead.png »
* En `<your-publish-URL>`, remplacez le bouton « Choisir notre quiz pour le café » par une version plus attrayante.
* sur `<your-author-env-URL>` supprimer la section « Récompenses non réclamées est un cadeau manqué ! »

## Jira {#jira}

L’utilisation de la tâche de mise à jour de contenu avec Jira vous permet de créer un ticket avec des instructions qui automatisent vos modifications.

### Créer un ticket {#create-a-ticket}

Créez un ticket Jira (de n’importe quel type). Deux informations essentielles sont nécessaires dans le champ **Description** de votre ticket :

1. URL publique de la page à modifier.

1. Les modifications nécessaires.

   La tâche prend en charge les formats suivants pour décrire vos modifications :

   * Langage naturel dans la description du ticket
      * par exemple, « Modifier le titre de X en Y »
   * PDF annoté joint
      * par exemple, créez un PDF de votre page et ajoutez des annotations détaillant ce que vous souhaitez modifier
   * Commentaires dans le PDF joint
      * par exemple, créez un PDF de votre page et ajoutez des commentaires détaillant ce que vous souhaitez modifier
   * Capture d’écran annotée jointe
      * par exemple, prenez une capture d’écran d’une partie de votre page et ajoutez des annotations détaillant ce que vous souhaitez modifier
   * Fichier Microsoft Word joint, contenant les modifications du langage naturel

### Appeler le traitement à partir de votre ticket {#invoke-the-job-from-your-ticket}

Pour utiliser le traitement, ajoutez un commentaire à votre ticket. Dans le commentaire, mentionnez la tâche avec le symbole `@`, ainsi que les instructions.

Par exemple :

* `@aemagent@adobe.com process this ticket`

### Interaction de la tâche {#how-the-agent-interacts}

Une fois que vous avez envoyé une commande à la tâche, elle répond avec des commentaires dans le fichier Jira. Les commentaires détaillent la progression du traitement et les actions entreprises.

Dans le cas d&#39;une commande `process` pour déclencher des mises à jour, les réponses peuvent suivre la séquence :

* Le commentaire initial confirme que le traitement a commencé.

* Une fois la tâche terminée, le traitement répond avec un autre commentaire contenant des détails sur les actions entreprises.
   * Les mises à jour de contenu effectuées par la tâche sont non destructives, ce qui signifie qu’elles sont effectuées sur une instance d’aperçu.
   * Le commentaire contient des liens vers les mises à jour, de sorte que vous puissiez les examiner et les publier selon vos besoins, ou attribuer le fichier Jira à la personne responsable.

* L’image suivante présente un exemple de Jira qui déclenche la commande `process` pour la tâche de mise à jour du contenu :

  ![Exemple de Jira utilisant la tâche de mise à jour de contenu de Brand Experience Agent](assets/content-update-jira-example.png)

## Activation {#activation}

Vous pouvez explorer les agents AEM via l’[aire de jeu](https://www.aem.live/developer/aem-playground) ou vous connecter à votre CSM ou à votre TAM pour discuter de l’accès via le SKU de l’agent.

## Limites {#limitations}

Gardez à l’esprit les limites suivantes :

* Les chargements de fichiers peuvent être utilisés lors de l’interaction avec [Jira](#jira), mais ne sont pas pris en charge lors de l’interaction avec l’assistant [AI.](#ai-assistant)
