---
title: Assistant d’IA dans Adobe Experience Manager (bêta privée)
description: Utilisez l’assistant AI dans Adobe Experience Manager pour vous aider à trouver des réponses, à résoudre les problèmes et à explorer Sites, Assets, Forms et Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 169de7971fba829b0d43e64d50a356439b6e57ca
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 1%

---

# À propos de l’assistant AI dans Adobe Experience Manager {#aem-home}

L’assistant d’IA dans AEM (Adobe Experience Manager) offre une interface de conversation conçue pour rationaliser la recherche de réponses à vos requêtes liées à Adobe Experience Manager. Il vous permet d’accéder aux connaissances sur les produits, de résoudre les problèmes et d’explorer les informations disponibles dans Experience League. Pendant le programme bêta privé, l’assistant AI prend en charge Adobe Experience Manager as a Cloud Service, notamment Sites, Assets, Forms et Cloud Manager.

>[!IMPORTANT]
>Assurez-vous d’avoir examiné et envoyé le contrat d’utilisation afin qu’Adobe puisse activer la fonctionnalité d’assistant d’IA pour que vous puissiez tester et participer au programme bêta privé.
>
>Pour toute question, envoyez un e-mail à [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.

## Confidentialité, sécurité et gouvernance

L’assistant d’IA d’AEM est conçu et met l’accent sur la confidentialité, la sécurité et la gouvernance.

Cet article décrit les fonctionnalités centrées sur la confiance que vous pouvez attendre de l’assistant AI :

* Aucune donnée personnelle n&#39;est utilisée par AI Assistant, y compris à des fins de formation.
* L’assistant AI n’a pas accès aux données des clients.
* Une autorisation explicite est requise pour interagir avec l’assistant AI.
* Les invites fournies par l&#39;utilisateur (questions, requêtes, etc.) ne sont pas partagées avec d&#39;autres clients.


## Découvrir l’assistant d’IA pour la connaissance des produits {#ai-prod-insights}

La connaissance des produits englobe les concepts et les sujets dérivés de la documentation d’Adobe Experience League. Ces questions peuvent être classées dans les sous-groupes suivants :

| Connaissances du produit | Exemples |
| --- | --- |
| Apprentissage par points | <ul><li>Qu’est-ce que l’éditeur universel ?</li><li>Comment créer un programme dans Cloud Manager ?</li></ul> |
| Ouvrir la découverte | <ul><li>Comment utiliser l’éditeur universel ?</li><li>Existe-t-il un moyen de copier du contenu d’un environnement à un autre ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi ne puis-je pas accéder à l’éditeur universel ?</li><li>Pourquoi mon pipeline échoue-t-il ?</li></ul> |

Le champ d’application actuel de l’assistant AI se concentre sur les questions de connaissance des produits Adobe Experience Manager as a Cloud Service. Cette portée inclut une prise en charge complète des principaux domaines, tels que Sites, Assets, Forms et Cloud Manager.

## Assistant AI pour AEM Forms (Forms Experience Builder) {#ai-forms-builder}

Outre l’assistant AI général pour la connaissance des produits, AEM propose un **[assistant AI pour AEM Forms (Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)** spécialisé. Cet assistant amélioré peut vous aider activement à créer et à configurer des formulaires à l’aide d’invites en langage naturel et à répondre aux questions spécifiques aux formulaires.

### Fonctionnalités essentielles

L’assistant AI pour AEM Forms fournit :

* **Création de formulaire** : créez entièrement de nouveaux formulaires à l’aide de descriptions en langage naturel
* **Importation de conception** : conversion de conceptions existantes (PDF, Figma, images) en formulaires AEM fonctionnels
* **Configuration de formulaire** : ajoutez des champs, des panneaux, des règles de validation et une logique conditionnelle
* **Gestion des mises en page** : organiser la structure des formulaires et l’optimiser pour différents appareils
* **Configuration de l’intégration** : configuration des envois de formulaire et de la gestion des données
* **Connaissance des produits** : répondez aux questions sur les fonctionnalités et les bonnes pratiques d’AEM Forms.

### Où accéder à

L’assistant AI pour AEM Forms est disponible dans :

* **Éditeur universel** : pour les formulaires Edge Delivery Services dotés de fonctionnalités d’édition visuelle
* **Éditeur de Forms adaptatif** : pour une configuration de formulaire détaillée et des fonctionnalités avancées
* **Interface utilisateur de gestion de Forms** : pour les tâches de création et de gestion de formulaires de haut niveau

### Prise en main

>[!NOTE]
>
> L’assistant AI pour AEM Forms (Forms Experience Builder) est disponible sous le programme bêta privé. Envoyez un e-mail à partir de votre adresse professionnelle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès.

Pour en savoir plus sur l’utilisation de l’assistant AI pour AEM Forms, notamment pour consulter des exemples détaillés et des bonnes pratiques, consultez la documentation sur l’[assistant AI pour AEM Forms](/help/edge/docs/forms/forms-ai-assistant.md).

### Exemples de cas d’utilisation

* **« Créez un formulaire de commentaires client avec les champs de nom, d’e-mail, d’évaluation et de commentaires »**
* **« Convertir ce formulaire de demande PDF chargé en formulaire adaptatif numérique »**
* **« Ajoutez une logique conditionnelle pour afficher les informations sur le conjoint uniquement lorsque l’état civil est « Marié » »**
* **« Configurer ce formulaire pour envoyer des données à notre système CRM »**

Cet assistant IA Forms spécialisé représente la prochaine évolution de la création de formulaires, associant la puissance de l’IA à des fonctionnalités de formulaires fiables d’AEM afin de rationaliser votre processus de création de formulaires.

## Comment concevoir des questions efficaces {#ai-craft-questions}

Pour recevoir les réponses les plus précises de l’assistant d’IA, il est important de formuler vos questions avec clarté et contexte. Suivez les conseils suivants pour vous assurer que vos requêtes sont claires et bien structurées :

* Exposez clairement votre tâche ou votre question de façon concise.
* Évitez les termes ambigus ou les syntaxes trop complexes pour améliorer la compréhension.
* Ajoutez un contexte pertinent à votre tâche ou question, car cette approche aide l’assistant d’IA à fournir des réponses plus précises et pertinentes.

### Exemples de questions non prises en charge {#ai-unsupported-questions}

| Aire | Exemples |
| --- | --- |
| Informations opérationnelles | <ul><li>Combien y a-t-il d’environnements de développement dans mon client ?</li><li>Qui a lancé le dernier pipeline de production ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi mon pipeline de production échoue-t-il ?</li></ul> |
| Tâche et automatisation | <ul><li>Configurez un pipeline de qualité du code à partir d’une branche de développement.</li></ul> |


## Utiliser l’assistant AI {#ai-use}


### Démarrer ou réinitialiser une conversation

Vous pouvez réinitialiser l’assistant d’IA et démarrer une nouvelle conversation lorsque vous souhaitez changer de sujet. Cette fonctionnalité est particulièrement utile lors de la résolution des problèmes liés aux requêtes qui échouent ou fournissent des informations incorrectes.

![bouton Démarrer la conversation](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**Pour démarrer ou réinitialiser une conversation, procédez comme suit**

1. Dans l’assistant AI, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Pour informer l’assistant AI d’une nouvelle rubrique ou d’une modification de rubrique, cliquez sur **Démarrer une nouvelle conversation**.

### Utilisation de la visibilité

L’assistant AI comprend une fonctionnalité de visibilité pour vous aider à explorer les rubriques et catégories prises en charge.

![Icône d’ampoule idéale](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**Pour utiliser la capacité de découverte, procédez comme suit**

1. Dans le coin supérieur droit de l’assistant d’IA, cliquez sur ![Icône Apprendre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Sélectionnez une catégorie pour afficher la liste des invites associées.
1. Choisissez une invite pour mieux comprendre les types de questions auxquelles l’assistant d’IA peut répondre.

### Fournir des commentaires sur l’assistant d’IA

Vos commentaires permettent d’améliorer l’assistant d’IA pour plus de performances et de précision.

Partagez vos commentaires sur votre expérience avec l’assistant d’IA au moyen des options suivantes :

![Pouces vers le haut, pouces vers le bas et icônes d’indicateur](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Icône | Description |
| --- | --- |
| ![Icône pouce vers le haut](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Cliquez pour indiquer ce qui s’est bien passé et partager des commentaires positifs. |
| ![Icône pouce vers le bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Cliquez pour fournir des suggestions d’amélioration. Ajoutez des commentaires spécifiques sur votre expérience, qui sont examinés quotidiennement. |
| ![Icône Indicateur](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Cliquez pour signaler des préoccupations ou fournir des commentaires détaillés sur votre interaction avec l’assistant d’IA. |

## Questions fréquentes sur l’assistant d’IA {#ai-faq}

Voici les réponses à certaines questions courantes sur l’assistant d’IA :

* **Les informations fournies par l’assistant d’IA sont-elles fournies en temps réel ?**\
  Non. L’assistant AI puise son contenu dans la documentation d’Adobe Experience League. Les mises à jour apportées au contenu peuvent prendre un certain temps à se refléter dans ses réponses.
* **Quelles applications Adobe l’assistant AI prend-il en charge ?**\
  Actuellement, AI Assistant prend en charge AEM as a Cloud Service, notamment Sites, Assets, Forms et Cloud Manager, spécifiquement pour les demandes d’informations sur les produits.
* **Quelles sont les fonctionnalités de l’assistant AI ?**\
  L’assistant AI est conçu pour répondre aux requêtes liées à la connaissance du produit Adobe.
* **L’assistant AI utilise-t-il des informations personnelles pour les données de formation ?**\
  Non. AI Assistant n’utilise pas d’informations personnelles à des fins de formation. Évitez de partager des informations personnelles sur vous-même ou d’autres personnes, y compris des noms ou des coordonnées, avec l’assistant d’IA.
