---
title: Tâche de mise à jour du contenu
description: Découvrez la tâche de mise à jour de contenu de Brand Experience Agent et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 2%

---


# Tâche de mise à jour du contenu {#content-update}

La tâche de mise à jour de contenu de [Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) automatise la production de contenu afin d’accélérer les tâches quotidiennes pour Adobe Experience Manager (AEM) as a Cloud Service et Edge Delivery Services.

## Vue d’ensemble {#overview}

La tâche de mise à jour du contenu met à jour le contenu existant, y compris les fragments de contenu, les pages, les formulaires et les ressources. La tâche peut effectuer des actions telles que la mise à jour, la suppression, le remplacement ou l’ajout d’éléments de contenu pour que les expériences restent exactes et à jour. Les entrées peuvent être des descriptions en langage naturel et, lorsqu’elles sont utilisées avec des PDF et des captures d’écran Jira, elles peuvent également fournir des entrées.

La tâche de mise à jour de contenu transforme les détails que vous fournissez, en langage naturel ou visuel, en mises à jour de contenu sur votre page. Vous fournissez l’URL d’une page qui doit être mise à jour, ainsi que des détails sur ce qui doit être mis à jour et les compétences de l’agent terminent votre tâche.

## Fonctionnalités {#capabilities}

Vous pouvez accéder à la compétence de mise à jour de contenu à partir de :

* [L’assistant AI](#ai-assistant)
* [Jira](#jira)

## Assistant IA {#ai-assistant}

Vous pouvez accéder au traitement dans AEM à partir de l’assistant AI.

Ouvrez l’assistant d’IA depuis [`experience.adobe.com`,](https://experience.adobe.com) puis commencez à interagir en spécifiant votre invite en langage naturel à l’aide du champ `Ask AI Assistant anything` :

![Tâche de mise à jour du contenu](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### Exemples d’invites {#sample-prompts}

Pour lancer les mises à jour de contenu, vous pouvez donner un large éventail d’invites en langage naturel. Vous devez également spécifier l’URL publique de la page que vous souhaitez mettre à jour. Par exemple :

* Modifiez la page suivante `https://www.your-url.com/sale` Mettez à jour l’en-tête du héros principal vers « Vente de méga du vendredi noir - jusqu’à 70 % de réduction », modifiez le compte à rebours pour afficher « Se termine dans 48 heures », supprimez « S’inscrire aux mises à jour », modifiez tous les boutons « Acheter maintenant » pour « Saisir l’offre ».

* `https://www.your-url.com/laptops/your-laptop-model` Mettre à jour la copie de bannière vers « Economisez 300 USD aujourd&#39;hui seulement », Mettre à jour le prix de 1 299 USD à 999 USD, Supprimer la bannière d&#39;option de financement

* `https://www.your-url.com/your-sneaker` Mettre à jour le statut du stock de « Stock faible » à « Stock de retour - Quantités limitées », Modifier le sélecteur de taille pour mettre en surbrillance les tailles disponibles en vert, Supprimer le badge « Bientôt disponible »

* `https://www.your-url.com/your-sneaker` Mettre à jour les images du produit pour afficher de nouvelles couleurs

>[!NOTE]
>
>Les chargements de fichiers peuvent être utilisés lors de l’interaction à l’aide de [Jira](#jira), mais ne sont pas pris en charge avec l’assistant AI.

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

Pour utiliser le traitement, ajoutez un commentaire à votre ticket. Dans le commentaire, mentionnez la tâche avec le symbole `@`, ainsi que la commande qu’elle doit exécuter ; par exemple :

* `@aemagent@adobe.com process`

Actuellement, la tâche comprend les commandes :

* `process` - traiter la demande
* `cancel` - annuler une demande de traitement
* `retry` - retraiter une demande
* `feedback` - appliquer le retour d’informations à une génération précédente
* `reprocess` - retraiter la demande d’origine

### Interaction de la tâche {#how-the-agent-interacts}

Une fois que vous avez envoyé une commande à la tâche, elle répond avec des commentaires dans le fichier Jira. Les commentaires détaillent la progression du traitement et les actions entreprises.

Dans le cas d&#39;une commande `process` pour déclencher des mises à jour, les réponses peuvent suivre la séquence :

* Le commentaire initial confirme que le traitement a commencé.

* Une fois la tâche terminée, le traitement répond avec un autre commentaire contenant des détails sur les actions entreprises.
   * Les mises à jour de contenu effectuées par la tâche sont non destructives, ce qui signifie qu’elles sont effectuées sur une instance d’aperçu.
   * Le commentaire contient des liens vers les mises à jour, de sorte que vous puissiez les examiner et les publier selon vos besoins, ou attribuer le fichier Jira à la personne responsable.

* L’image suivante présente un exemple de Jira qui déclenche la commande `process` pour la tâche de mise à jour du contenu :

  ![Exemple de Jira utilisant la tâche de mise à jour de contenu de l’agent de production Experience](assets/content-update-jira-example.png)

## Activation {#activation}

Pour activer et accéder à la tâche de création de communication, vous devez contacter Adobe. Pour commencer, vous pouvez effectuer l’une des opérations suivantes :

* `experience-production-agent@adobe.com` de contact
* Ou contactez votre équipe de compte

Pour accélérer le processus, il est utile de fournir les informations suivantes :

* Pour AEM as a Cloud Service, vous devez fournir vos éléments suivants :
   * Identifiant d&#39;organisation
   * `product_id`
   * `profile_id`

   * Ces valeurs se présentent comme suit :
      1. Votre administrateur doit visiter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)
      1. Sélectionner **Adobe Experience Manager as a Cloud Service**
      1. Sélectionnez l’instance AEM appropriée
      1. Sélectionnez le profil qui autorise les opérations de lecture et d’écriture pour le contenu en question
      1. Récupérer l’URL du navigateur
      1. Extrayez les `product_id` et les `profile_id` de l’URL.
Par exemple, `https://adminconsole.adobe.com/products/profiles/users`.

* Création de documents Edge Delivery
   * Fournissez les informations suivantes à votre équipe Adobe :
      * Domaines pertinents
      * Informations Github pertinentes :
         * Org
         * Référentiel
         * Branche

## Limites {#limitations}

Gardez à l’esprit les limites suivantes :

* Les chargements de fichiers peuvent être utilisés lors de l’interaction avec [Jira](#jira), mais ne sont pas pris en charge lors de l’interaction avec l’assistant [AI.](#ai-assistant)
