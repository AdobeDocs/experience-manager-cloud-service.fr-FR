---
title: Tâche de mise à jour du contenu
description: Découvrez ce qu’est la tâche de mise à jour de contenu de Brand Experience Agent et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: dcf2b9f2966144fac969563a395a72fa81ce2751
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 1%

---


# Tâche de mise à jour du contenu {#content-update}

La tâche de mise à jour de contenu de l’[agent de production Experience](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) automatise la production de contenu afin d’accélérer les tâches quotidiennes pour Adobe Experience Manager (AEM) as a Cloud Service et Edge Delivery Services.

## Vue d’ensemble {#overview}

La tâche de mise à jour du contenu met à jour le contenu existant, y compris les fragments de contenu, les pages, les formulaires et les ressources. La tâche peut effectuer des actions telles que la mise à jour, la suppression, le remplacement ou l’ajout d’éléments de contenu pour que les expériences restent exactes et à jour. Les entrées peuvent être des descriptions en langage naturel et, lorsqu’elles sont utilisées avec des PDF et des captures d’écran Jira, elles peuvent également fournir des entrées.

La tâche de mise à jour de contenu transforme les détails que vous fournissez, en langage naturel ou visuel, en mises à jour de contenu sur votre page. Vous fournissez l’URL d’une page à mettre à jour, ainsi que des détails sur les éléments à mettre à jour, et le traitement de l’agent termine votre tâche. Utilisée avec AEM as a Cloud Service, la tâche crée un [lancement](/help/sites-cloud/authoring/launches/overview.md) afin que vous puissiez consulter les mises à jour avant l’application. Lorsqu’elle est utilisée avec la création de documents, la tâche crée une [version](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#).

>[!VIDEO](https://video.tv.adobe.com/v/3486418?learn=on)

## Fonctionnalités {#capabilities}

Vous pouvez accéder à la tâche de mise à jour de contenu à partir de :

* [L’assistant AI](#ai-assistant)
* [Jira](#jira)

## Assistant IA {#ai-assistant}

Vous pouvez accéder au traitement dans AEM à partir de l’assistant AI.

Ouvrez l’[assistant AI](/help/implementing/cloud-manager/ai-assistant-in-aem.md#ai-use) dans la barre d’outils supérieure droite pour démarrer une conversation.

![Icône Assistant IA de la barre d’outils](/help/ai-in-aem/agents/brand-experience/experience-production/assets/ai-assistant-icon.png)

### Configuration de l’URL de publication {#configuring-the-publish-url}

Pour indiquer à l’agent où appliquer les mises à jour, vous devez fournir un lien vers la page. Vous pouvez fournir une URL de création ou une URL de publication.

Pour utiliser une URL de publication (publique), une configuration unique doit être effectuée :

* Conditions préalables :

   * Pour effectuer la configuration, l’utilisateur doit disposer des droits d’administrateur système ou d’administrateur de produit.

* Configuration :

   1. Appelez la tâche de mise à jour de contenu en demandant une mise à jour de contenu pour l’URL.
   1. L’assistant vous guidera à travers la configuration, en vous posant un certain nombre de questions.
   1. Une fois l’opération terminée, l’URL de publication est configurée et peut être utilisée.

Par exemple :

![Tâche de mise à jour du contenu - Configuration de l’URL de publication](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### Invites {#prompts}

Pour lancer les mises à jour de contenu, vous pouvez donner un large éventail d’invites en langage naturel. Vous devez spécifier l’URL publique (publication) ou l’URL de l’environnement de création de la page que vous souhaitez mettre à jour. Certains des verbes pris en charge, mais pas tous ; remplacez, mettez à jour, supprimez, modifiez, modifiez, modifiez, ajustez, supprimez.

### Exemples d’invites {#sample-prompts}

Voici quelques exemples d’invites :

* lors de `<your-publish-URL>` mise à jour : « Votre café parfait est à quatre questions ! » à « Ton café, ton chemin ! »
* sur `<your-author-env-URL>`, remplacez l’image de « holdingcup.png » par « stairhead.png »
* En `<your-publish-URL>`, remplacez le bouton « Choisir notre quiz pour le café » par une version plus attrayante.
* sur `<your-author-env-URL>` supprimer la section « Récompenses non réclamées est un cadeau manqué ! »
* lors de `<your-author-env-URL>` mise à jour basée sur le joint

### Chargement de fichier dans l’assistant AI {#file-upload-in-ai-assistant}

Outre la saisie directe d’invites en langage naturel, vous pouvez également charger un document pour demander des modifications.

Utilisez l’icône `+` en bas à gauche du menu d’invite pour charger un fichier spécifiant vos besoins. Les formats de fichiers pris en charge sont les suivants : PDF, JPG, PNG, DOCX, etc.

![Tâche de mise à jour du contenu - Chargement de fichier](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-file-upload.png)

Par exemple, un PDF annoté spécifiant les modifications demandées :

![Tâche de mise à jour de contenu - PDF annoté](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-annotated-pdf.png)

>[!VIDEO](https://video.tv.adobe.com/v/3491297?learn=on)

### Orchestration avec l’agent de gouvernance de marque  {#orchestration-with-the-brand-governance-agent}

Si l’organisation a importé sa politique de marque, la tâche de mise à jour de contenu utilisera cette politique lors des mises à jour de contenu agentic (voir la vidéo [Présentation](#overview)).

Pour une invite *prescriptive* telle que :

* `on <your-publish-URL> update “Your perfect coffee is four questions away!” to “Your coffee, your way!”`

La tâche de mise à jour de contenu orchestre avec l’[agent de gouvernance de marque](/help/ai-in-aem/agents/brand-experience/overview.md) et informe l’utilisateur si la copie fournie est sur la marque ou non.

![Tâche de mise à jour de contenu - orchestration avec l’agent de gouvernance de marque](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-brand-experience.png)

Pour des invites plus abstraites telles que :

* `on <your-publish-env-URL> change “Take our Coffee Quiz” button to a more engaging version`

Pendant la génération, l’agent utilise les directives de la marque pour s’assurer que la sortie est sur la marque.

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

## Amélioration de la création {#further-refinement-in-authoring}

Une fois que vous avez choisi de modifier la page dans AEM, elle s’ouvre dans votre environnement de création (par exemple, l’[éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) ou l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)).

Dans l’[éditeur universel](#universal-editor-edit-text-with-the-assistant), l’assistant d’IA est *contextuel* : vous pouvez sélectionner des éléments sur la zone de travail et les utiliser avec l’assistant.

### Éditeur universel : permet de modifier du texte avec l’assistant. {#universal-editor-edit-text-with-the-assistant}

Pour affiner la copie à partir de l’assistant lors de la création :

1. Sélectionnez l’élément dans l’[éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md).
1. Ouvrez l’assistant d’IA dans le coin supérieur droit, saisissez votre invite, puis effectuez l’envoi.

Exemples d’invites :

* `Update to Explore the World of Coffee`
* `Update to be more engaging for the 30-40 year old age demographic and avid coffee drinker`

Sélectionnez **Appliquer les modifications** (ou l’équivalent) pour que les mises à jour apparaissent sur la page.

## Activation {#activation}

Vous pouvez explorer les agents AEM via l’[aire de jeu](https://www.aem.live/developer/aem-playground) ou vous connecter à votre CSM ou à votre TAM pour discuter de l’accès via le SKU de l’agent.

## Ressources supplémentaires {#additional-resources}

Les ressources suivantes peuvent s’avérer utiles lorsque vous continuez à explorer l’agent de production d’expérience :

* Vous pouvez également utiliser le [classeur de l’agent de production Experience](https://www.adobe.com/go/aem-epa-workbook_fr) pour obtenir des instructions pratiques et guidées.
