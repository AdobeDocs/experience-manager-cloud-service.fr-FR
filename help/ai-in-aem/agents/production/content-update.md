---
title: Compétence de mise à jour du contenu
description: Découvrez la compétence de mise à jour de contenu de l’agent de production d’expérience et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 7f42357292fab3001a3905919dfcb78f4dfd30ba
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---


# Compétence de mise à jour du contenu {#content-update}

Les compétences de mise à jour de contenu de l’agent de production Experience automatisent la production de contenu afin d’accélérer les tâches quotidiennes pour Adobe Experience Manager (AEM) as a Cloud Service et Edge Delivery Services.

La compétence de mise à jour de contenu met à jour le contenu existant dans CMS, y compris les fragments de contenu, les pages, les formulaires et les ressources. L’agent peut effectuer des actions telles que la mise à jour, la suppression, le remplacement ou l’ajout d’éléments de contenu pour que les expériences restent exactes et à jour. Les entrées peuvent être des descriptions en langage naturel et, lorsqu’elles sont utilisées avec des PDF et des captures d’écran Jira, elles peuvent également fournir des entrées.

## Vue d’ensemble {#overview}

La compétence de mise à jour de contenu transforme les détails que vous fournissez, en langage naturel ou visuel, en mises à jour de contenu sur votre page. Vous fournissez l’URL d’une page qui doit être mise à jour, ainsi que des détails sur ce qui doit être mis à jour et les compétences de l’agent terminent votre tâche.

## Fonctionnalités {#capabilities}

Vous pouvez accéder à la compétence de mise à jour de contenu à partir de :

* [Assistant IA](#ai-assistant)

* [Jira](#jira)

## Assistant IA {#ai-assistant}

Vous pouvez accéder aux agents AEM Business par le biais de l’assistant AI.

Ouvrez l’assistant d’IA à l’adresse experience.adobe.com, puis commencez à interagir en spécifiant votre invite en langage naturel à l’aide du champ `Ask AI Assistant anything` :

![Accéder à l&#39;agent Discovery](/help/ai-in-aem/agents/production/assets/content-update-ai-assistant-example.png)

### Exemples d’invites {#sample-prompts}

Pour lancer les mises à jour de contenu, vous pouvez donner un large éventail d’invites en langage naturel. Vous devez également spécifier l’URL publique de la page que vous souhaitez mettre à jour. Par exemple :

* modifiez la page suivante https://www.your-url.com/sale Mettez à jour l’en-tête principal du héros vers « Black Friday Mega Sale - Jusqu’à 70 % de réduction », modifiez le compte à rebours pour afficher « Se termine dans 48 heures », supprimez « S’inscrire aux mises à jour », modifiez tous les boutons « Shop Now » pour « Saisir l’offre ».

* https://www.your-url.com/laptops/your-laptop-model Mettre à jour la copie de bannière vers « Economisez 300 USD aujourd'hui seulement », Mettre à jour le prix de 1 299 USD à 999 USD, Supprimer la bannière d'option de financement

* https://www.your-url.com/your-sneaker Mettez à jour le statut du stock de « Stock faible » vers « Stock de retour - Quantités limitées », modifiez le sélecteur de taille pour mettre en surbrillance les tailles disponibles en vert, supprimez le badge « Bientôt disponible »

* https://www.your-url.com/your-sneaker Mettez à jour les images du produit pour afficher de nouvelles couleurs

>[!NOTE]
>
>Les chargements de fichiers peuvent être utilisés lors de l’interaction à l’aide de [Jira](#jira), mais ne sont pas pris en charge avec l’assistant AI.

## Jira {#jira}

L’utilisation de la compétence de mise à jour de contenu avec Jira vous permet de créer un ticket avec des instructions qui automatisent vos modifications.

### Créer un ticket {#create-a-ticket}

Créez un ticket Jira (de n’importe quel type).

Deux informations essentielles sont nécessaires dans le champ **Description** de votre ticket :

1. URL publique de la page à modifier.

1. Les modifications nécessaires.

   Actuellement, la compétence prend en charge les formats suivants pour décrire vos modifications :

   * Langage naturel dans la description du ticket
      * par exemple, « Modifier le titre de X en Y »
   * PDF annoté joint
      * par exemple, créez un PDF de votre page et ajoutez des annotations détaillant ce que vous souhaitez modifier
   * Commentaires dans le PDF joint
      * par exemple, créez un PDF de votre page et ajoutez des commentaires détaillant ce que vous souhaitez modifier
   * Capture d’écran annotée jointe
      * par exemple, prenez une capture d’écran d’une partie de votre page et ajoutez des annotations détaillant ce que vous souhaitez modifier
   * Fichier Microsoft Word joint, contenant les modifications du langage naturel

### Appeler l’agent à partir de votre ticket {#invoke-the-agent-from-your-ticket}

Pour utiliser l’agent, ajoutez un commentaire à votre ticket. Dans le commentaire, mentionnez l’agent avec le symbole `@`, ainsi que la commande qu’il doit exécuter ; par exemple :

* `@aemagent@adobe.com process`

Actuellement, l’agent comprend les commandes :

* `process` - traiter la demande
* `cancel` - annuler une demande de traitement
* `retry` - retraiter une demande
* `feedback` - appliquer le retour d’informations à une génération précédente
* `reprocess` - retraiter la demande d’origine

### Interaction de l’agent {#how-the-agent-interacts}

Après avoir envoyé une commande à l’agent, il répond avec des commentaires dans le fichier Jira. Les commentaires détaillent la progression de l’agent et les mesures prises.

Dans le cas d&#39;une commande `process` pour déclencher des mises à jour, les réponses peuvent suivre la séquence :

* Le commentaire initial confirme que l’agent a commencé.

* Une fois la tâche terminée. l’agent répond avec un autre commentaire contenant des détails sur les actions entreprises.
   * Les mises à jour de contenu effectuées par l’agent sont non destructives, ce qui signifie qu’elles sont effectuées sur une instance d’aperçu.
   * Le commentaire contient des liens vers les mises à jour, de sorte que vous puissiez les examiner et les publier selon vos besoins, ou attribuer le fichier Jira à la personne responsable.

* L’image suivante présente un exemple de Jira qui déclenche la commande `process` pour la compétence de mise à jour de contenu :

  ![Exemple de Jira utilisant la compétence de mise à jour de contenu de l’agent de production Experience](assets/content-update-jira-example.png)

### Activation {#activation}

Pour activer l’agent de production Experience avec Jira et y accéder, vous devez envoyer un e-mail à Adobe. Pour commencer, vous pouvez contacter :

* `experience-production-agent@adobe.com`
* ou contactez votre équipe de compte

Pour accélérer le processus, il est utile de fournir les informations suivantes :

* Pour AEM as a Cloud Service
   * Vous devez fournir vos :
      * Identifiant d&#39;organisation
      * `product_id`
      * `profile_id`

   * Ces valeurs sont disponibles en procédant comme suit :
      * Votre administrateur doit visiter <https://adminconsole.adobe.com/>
      * Sélectionner **Adobe Experience Manager as a Cloud Service**
      * Sélectionnez l’instance AEM appropriée
      * Sélectionnez le profil qui autorise les opérations de lecture et d’écriture pour le contenu en question
      * Récupérer l’URL du navigateur
      * Extrayez les `product_id` et les `profile_id` de l’URL.
Par exemple, <https://adminconsole.adobe.com/products/profiles/users>.

* Création de documents Edge Delivery
   * Fournissez les informations suivantes à votre équipe Adobe :
      * Domaines pertinents
      * Informations Github pertinentes :
         * Org
         * Référentiel
         * Branche

## Limites {#limitations}

Actuellement, les limites du programme de mise à jour de contenu sont les suivantes :

* Les chargements de fichiers peuvent être utilisés lors de l’interaction avec [Jira](#jira), mais ne sont pas pris en charge lors de l’interaction avec l’assistant [AI](#ai-assistant).
