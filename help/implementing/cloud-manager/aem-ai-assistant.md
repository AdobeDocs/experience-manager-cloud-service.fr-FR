---
title: Assistant d’IA dans Adobe Experience Manager (Beta limité)
description: Utilisez l’assistant d’IA dans Adobe Experience Manager pour vous aider à trouver des réponses, résoudre les problèmes et explorer Sites, Assets, Forms et Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
source-git-commit: e454581a2e6f2b8184a54d6550daec60e58bbc6c
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# À propos de l’assistant d’IA dans Adobe Experience Manager {#aem-home}

L’assistant d’IA dans AEM (Adobe Experience Manager) offre une interface conversationnelle conçue pour rationaliser la recherche de réponses à vos requêtes liées à Adobe Experience Manager. Il vous permet d’accéder aux connaissances sur les produits, de résoudre les problèmes et d’explorer les informations disponibles dans Experience League. Au cours du programme Beta limité, l’assistant d’IA prend en charge Adobe Experience Manager as a Cloud Service, notamment Sites, Assets, Forms et Cloud Manager.

>[!IMPORTANT]
>Assurez-vous d’avoir examiné et envoyé le contrat utilisateur afin que l’Adobe puisse activer la fonction d’assistant d’IA pour que vous puissiez tester et participer au programme Beta.
>
>Pour toute question, envoyez un email à [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) à partir de votre adresse électronique associée à votre Adobe ID.

## Confidentialité, sécurité et gouvernance

L’assistant d’IA en AEM est conçu en mettant l’accent sur la confidentialité, la sécurité et la gouvernance.

Cet article décrit les fonctionnalités centrées sur la confiance que vous pouvez attendre de l’assistant d’IA :

* Aucune donnée personnelle n’est utilisée par l’assistant d’IA, y compris à des fins de formation.
* L’assistant AI n’a pas accès aux données des consommateurs.
* Une autorisation explicite est requise pour interagir avec l’assistant d’IA.
* Les invites fournies par l’utilisateur (questions, requêtes, etc.) ne sont pas partagées avec d’autres clients.


## Découvrez l’assistant d’IA pour la connaissance des produits {#ai-prod-insights}

Les connaissances sur les produits englobent les concepts et les rubriques dérivés de la documentation Adobe Experience League. Ces questions peuvent être classées dans les sous-groupes suivants :

| Connaissances produit | Exemples |
| --- | --- |
| Apprentissage pointé | <ul><li>Qu’est-ce qu’Universal Editor ?</li><li>Comment créer un programme dans Cloud Manager ?</li></ul> |
| Découverte ouverte | <ul><li>Comment utiliser Universal Editor ?</li><li>Existe-t-il un moyen de copier du contenu d’un environnement vers un autre ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi ne puis-je pas accéder à l’éditeur universel ?</li><li>Pourquoi mon pipeline échoue-t-il ?</li></ul> |

Actuellement, l’assistant d’IA se concentre sur les questions relatives aux connaissances sur les produits pour Adobe Experience Manager as a Cloud Service. Cette portée comprend une prise en charge complète des domaines clés, tels que Sites, Assets, Forms et Cloud Manager.

## Comment concevoir des questions efficaces {#ai-craft-questions}

Pour obtenir les réponses les plus précises possible de l’assistant d’IA, il est important d’adresser vos questions avec clarté et contexte. Suivez les conseils ci-dessous pour vous assurer que vos requêtes sont claires et bien structurées :

* Exprimez clairement votre tâche ou votre question de manière concise.
* Évitez les termes ambigus ou les syntaxes trop complexes pour améliorer la compréhension.
* Incluez le contexte pertinent concernant votre tâche ou votre question, car cette approche permet à l’assistant d’IA de fournir des réponses plus précises et pertinentes.

### Exemples de questions non prises en charge {#ai-unsupported-questions}

| Aire | Exemples |
| --- | --- |
| Connaissances opérationnelles | <ul><li>Combien d’environnements de développement existent dans mon client ?</li><li>Qui a démarré le dernier pipeline de production ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi mon pipeline de production échoue-t-il ?</li></ul> |
| Tâche et automatisation | <ul><li>Configurez un pipeline de qualité de code à partir d’une branche de développement pour moi.</li></ul> |


## Utilisation de l’assistant AI {#ai-use}


### Démarrer ou réinitialiser une conversation

Vous pouvez réinitialiser l’assistant d’IA et lancer une nouvelle conversation lorsque vous souhaitez modifier des rubriques. Cette fonctionnalité est particulièrement utile lors du dépannage des requêtes qui échouent ou qui fournissent des informations incorrectes.

![Bouton Démarrer la conversation](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**Pour démarrer ou réinitialiser une conversation :**

1. Sur l’assistant d’IA, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Pour informer l’assistant d’IA d’une nouvelle rubrique ou d’une modification d’une rubrique, cliquez sur **Démarrer une nouvelle conversation**.

### Utilisation de la recherche

L’assistant d’IA comprend une fonctionnalité de découverte qui vous aide à explorer les rubriques et catégories prises en charge.

![Icône de l’ampoule d’idée](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**Pour utiliser la capacité de découverte :**

1. Près du coin supérieur droit de l’assistant d’IA, cliquez sur ![Icône de formation](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Sélectionnez une catégorie pour afficher la liste des invites associées.
1. Choisissez une invite pour mieux comprendre les types de questions auxquelles l’assistant peut répondre.

### Fournir des commentaires sur l’assistant d’IA

Votre saisie contribue à améliorer l’assistant d’IA pour de meilleures performances et une plus grande précision.

Partagez vos commentaires sur votre expérience avec l’assistant d’IA au moyen des options suivantes :

![Pointe vers le haut, pouce vers le bas et icônes d’indicateur](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Icône | Description |
| --- | --- |
| ![ Icône de mise en forme ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Cliquez sur pour indiquer ce qui s’est bien passé et pour partager des commentaires positifs. |
| ![Icône de bas en bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Cliquez sur pour fournir des suggestions d’amélioration. Ajoutez des commentaires spécifiques sur votre expérience, qui sont examinés quotidiennement. |
| ![Icône Indicateur](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Cliquez sur pour signaler vos préoccupations ou fournir des commentaires détaillés sur votre interaction avec l’assistant d’IA. |

## Questions fréquentes sur l’assistant d’IA {#ai-faq}

Voici les réponses aux questions les plus courantes concernant l’assistant d’IA :

* **Les informations sont-elles fournies par l’assistant d’IA en temps réel ?**\
  Non. L’assistant d’IA source son contenu dans la documentation de Adobe Experience League. Les mises à jour du contenu peuvent prendre un certain temps pour réfléchir dans ses réponses.
* **Quelles applications Adobe l’assistant d’IA prend-il en charge ?**\
  Actuellement, l’assistant d’IA prend en charge AEM as a Cloud Service, notamment Sites, Assets, Forms et Cloud Manager, en particulier pour les demandes de renseignements sur les connaissances sur les produits.
* **Quelles sont les fonctionnalités de l’assistant d’IA ?**\
  L’assistant d’IA est conçu pour répondre à des requêtes liées aux connaissances sur les produits Adobe.
* **L’assistant d’IA utilise-t-il des informations personnelles pour les données de formation ?**\
  Non. L’assistant d’IA n’utilise pas d’informations personnelles à des fins de formation. Évitez de partager des informations personnelles sur vous-même ou sur d’autres personnes, y compris des noms ou des coordonnées, avec l’assistant d’IA.



