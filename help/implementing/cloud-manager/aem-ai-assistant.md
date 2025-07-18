---
title: Assistant d’IA dans Adobe Experience Manager (bêta privée)
description: Utilisez l’assistant AI dans Adobe Experience Manager pour vous aider à trouver des réponses, à résoudre les problèmes et à explorer Sites, Assets, Dynamic Media, Cloud Manager et Forms.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 0afd74120380c9ae3d02db9fb684189c2f19648f
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 1%

---

# À propos de l’assistant AEM AI dans Adobe Experience Manager {#aem-home}

L’assistant d’IA dans AEM (Adobe Experience Manager) offre une interface de conversation conçue pour rationaliser la recherche de réponses à vos requêtes liées à Adobe Experience Manager. Il vous permet d’accéder aux connaissances sur les produits, de résoudre les problèmes et d’explorer les informations disponibles dans Experience League. Au cours du programme bêta privé, l’assistant AEM AI prend en charge Adobe Experience Manager as a Cloud Service, notamment Sites, Assets, Dynamic Media, Cloud Manager et Forms.

>[!IMPORTANT]
>Assurez-vous d’avoir examiné et envoyé le contrat d’utilisation afin qu’Adobe puisse activer la fonctionnalité d’assistant d’IA pour que vous puissiez tester et participer au programme bêta privé.
>
>Pour toute question, envoyez un e-mail à [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.

## Confidentialité, sécurité et gouvernance

L’assistant AEM AI a été conçu pour mettre l’accent sur la confidentialité, la sécurité et la gouvernance.

Cet article décrit les fonctionnalités centrées sur la confiance que vous pouvez attendre de l’assistant AEM AI :

* Aucune donnée personnelle n’est utilisée par l’assistant AEM AI, y compris à des fins de formation.
* L’assistant AEM AI n’a pas accès aux données des clients.
* Une autorisation explicite est requise pour interagir avec l’assistant IA d’AEM.
* Les invites fournies par l&#39;utilisateur (questions, requêtes, etc.) ne sont pas partagées avec d&#39;autres clients.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->


## Découvrez l’assistant d’IA d’AEM pour en savoir plus sur les produits {#ai-prod-insights}

La connaissance des produits englobe les concepts et les sujets dérivés de la documentation d’Adobe Experience League. Ces questions peuvent être classées dans les sous-groupes suivants :

| Connaissances du produit | Exemples |
| --- | --- |
| Apprentissage par points | <ul><li>Qu’est-ce que l’éditeur universel ?</li><li>Comment créer un programme dans Cloud Manager ?</li></ul> |
| Ouvrir la découverte | <ul><li>Comment utiliser l’éditeur universel ?</li><li>Existe-t-il un moyen de copier du contenu d’un environnement à un autre ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi ne puis-je pas accéder à l’éditeur universel ?</li><li>Pourquoi mon pipeline échoue-t-il ?</li></ul> |

Le périmètre actuel de l’assistant AEM AI consiste à répondre aux questions relatives à la connaissance des produits pour Adobe Experience Manager as a Cloud Service. Cette portée inclut une prise en charge complète des principaux domaines, tels que Sites, Assets, Forms et Cloud Manager.

## Comment concevoir des questions efficaces {#ai-craft-questions}

Pour recevoir les réponses les plus précises de l’assistant d’IA d’AEM, il est important de formuler vos questions avec clarté et contexte. Suivez les conseils suivants pour vous assurer que vos requêtes sont claires et bien structurées :

* Exposez clairement votre tâche ou votre question de façon concise.
* Évitez les termes ambigus ou les syntaxes trop complexes pour améliorer la compréhension.
* Fournissez un contexte pertinent sur votre tâche ou question, car cette approche aide l’assistant d’IA d’AEM à fournir des réponses plus précises et pertinentes.
Par exemple, dans votre invite, il est utile de nommer la solution AEM dans laquelle vous travaillez : Sites, Assets, Dynamic Media, Cloud Manager et Forms.

### Exemples de questions non prises en charge {#ai-unsupported-questions}

| Aire | Exemples |
| --- | --- |
| Informations opérationnelles | <ul><li>Combien y a-t-il d’environnements de développement dans mon client ?</li><li>Qui a lancé le dernier pipeline de production ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi mon pipeline de production échoue-t-il ?</li></ul> |
| Tâche et automatisation | <ul><li>Configurez un pipeline de qualité du code à partir d’une branche de développement.</li></ul> |


## Utilisation de l’assistant AEM AI {#ai-use}

### Activer l’accès à l’assistant AEM AI via Admin Console

Pour utiliser l’assistant AEM AI, votre entreprise doit s’inscrire au niveau Admin Console. Un administrateur de produit crée (ou choisit) un groupe d’utilisateurs et lui accorde la nouvelle autorisation « Assistant IA ». Toute personne ajoutée à ce groupe accède instantanément à l’assistant dans AEM. Si l’objectif est la disponibilité à l’échelle de l’entreprise, l’administrateur affecte simplement tous les utilisateurs à ce groupe.

![Assistant AEM AI dans Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

Du point de vue de l’employé, le processus est simple : identifiez l’administrateur ou l’administratrice de produit pour Adobe Experience Manager dans votre entreprise et demandez à être ajouté au groupe d’utilisateurs et d’utilisatrices compatible avec l’IA. Une fois que vous apparaissez dans ce groupe, l&#39;icône Assistant s&#39;affiche automatiquement la prochaine fois que vous vous connectez.

Les administrateurs doivent garder à l’esprit une gouvernance Cloud Manager normale. Vous devez détenir des droits d’administrateur de produit dans Admin Console pour créer des profils, gérer des groupes d’utilisateurs ou modifier des autorisations. Si les utilisateurs ont également besoin de la fonctionnalité intégrée **Créer un ticket d’assistance** de l’assistant, ajoutez le rôle standard **Administrateur de l’assistance** (rôle Admin Console standard) aux mêmes personnes ou groupes.

![Création d’un ticket d’assistance technique dans l’assistant AEM AI d’Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

Pour une présentation guidée de la configuration des utilisateurs et des groupes dans AEM as a Cloud Service, voir [Configuration de l’accès à AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/overview).

Voir aussi [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).


### Démarrer ou réinitialiser une conversation

Vous pouvez réinitialiser l’assistant AEM AI et démarrer une nouvelle conversation lorsque vous souhaitez changer de sujet. Cette fonctionnalité est particulièrement utile lors de la résolution des problèmes liés aux requêtes qui échouent ou fournissent des informations incorrectes.

![bouton Démarrer la conversation](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**Pour démarrer ou réinitialiser une conversation, procédez comme suit**

1. Dans l’assistant AEM AI, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Pour informer l’assistant AEM AI d’une nouvelle rubrique ou d’une modification de rubrique, cliquez sur **Démarrer une nouvelle conversation**.

### Utilisation de la visibilité

L’assistant AEM AI comprend une fonction de facilité de découverte pour vous aider à explorer les rubriques et catégories prises en charge.

![Icône d’ampoule idéale](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**Pour utiliser la capacité de découverte, procédez comme suit**

1. Dans le coin supérieur droit de l’assistant AEM AI, cliquez sur ![Icône Apprendre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Sélectionnez une catégorie pour afficher la liste des invites associées.
1. Choisissez une invite pour mieux comprendre les types de questions auxquelles l’assistant d’IA d’AEM peut répondre.

### Fournir des commentaires sur l’assistant AEM AI

Vos entrées permettent d’améliorer l’assistant d’IA d’AEM en termes de performances et de précision.

Partagez vos commentaires sur votre expérience avec l’assistant AEM AI à l’aide des options suivantes :

![Pouces vers le haut, pouces vers le bas et icônes d’indicateur](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Icône | Description |
| --- | --- |
| ![Icône pouce vers le haut](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Cliquez pour indiquer ce qui s’est bien passé et partager des commentaires positifs. |
| ![Icône pouce vers le bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Cliquez pour fournir des suggestions d’amélioration. Ajoutez des commentaires spécifiques sur votre expérience, qui sont examinés quotidiennement. |
| ![Icône Indicateur](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Cliquez pour signaler des préoccupations ou fournir des commentaires détaillés sur votre interaction avec l’assistant AEM AI. |

## Questions fréquentes sur l’assistant AEM AI {#ai-faq}

Voici les réponses à certaines questions courantes sur l’assistant d’IA :

* **Les informations fournies par l’assistant AEM AI sont-elles fournies en temps réel ?**\
  Non. L’assistant AI puise son contenu dans la documentation d’Adobe Experience League. Les mises à jour apportées au contenu peuvent prendre un certain temps à se refléter dans ses réponses.
* **Quelles applications Adobe l’assistant d’IA d’AEM prend-il en charge ?**\
  Actuellement, l’assistant AI prend en charge les demandes d’informations sur les produits dans AEM as a Cloud Service, notamment Sites, Assets, Dynamic Media, Cloud Manager et Forms.
* **Quelles sont les fonctionnalités de l’assistant AEM AI ?**\
  L’assistant AEM AI est conçu pour répondre aux requêtes liées à la connaissance du produit Adobe.
* **L’assistant IA d’AEM utilise-t-il des informations personnelles pour les données de formation ?**\
  Non. AEM AI Assistant n’utilise pas d’informations personnelles à des fins de formation. Évitez de partager des informations personnelles sur vous-même ou d’autres personnes, y compris des noms ou des coordonnées, avec l’assistant AEM AI.


## Assistant AEM Forms AI (Forms Experience Builder) {#ai-forms-builder}

Outre l’assistant IA d’AEM général pour la connaissance des produits, AEM propose un assistant IA d’AEM Forms spécialisé **[&#128279;](/help/edge/docs/forms/forms-ai-assistant.md)** (Forms Experience Builder). Cet assistant amélioré peut vous aider activement à créer et à configurer des formulaires à l’aide d’invites en langage naturel et à répondre aux questions spécifiques aux formulaires.

### Fonctionnalités essentielles

L’assistant d’IA d’AEM Forms fournit les éléments suivants :

* **Création de formulaire** : créez entièrement de nouveaux formulaires à l’aide de descriptions en langage naturel.
* **Importation de conception** : convertissez des conceptions existantes (PDF, Figma, images) en AEM Forms fonctionnel.
* **Configuration du formulaire** : ajoutez des champs, des panneaux, des règles de validation et une logique conditionnelle.
* **Gestion des mises en page** : organisez la structure des formulaires et optimisez-la pour différents appareils.
* **Configuration de l’intégration** : configurez les envois de formulaire et la gestion des données.
* **Connaissance des produits** : répondez aux questions sur les fonctionnalités et les bonnes pratiques d’AEM Forms.

### Emplacement d’accès

L’assistant AEM Forms AI est disponible dans les cas suivants :

* **Éditeur universel** : pour les formulaires Edge Delivery Services dotés de fonctionnalités d’édition visuelle.
* **Éditeur de Forms adaptatif** : pour une configuration de formulaire détaillée et des fonctionnalités avancées.
* **Interface utilisateur de gestion de Forms** : pour les tâches de création et de gestion de formulaires de haut niveau.

### Prise en main

>[!NOTE]
>
> L’assistant AEM Forms AI (Forms Experience Builder) est disponible sous le programme bêta privé. Envoyez un e-mail à partir de votre adresse professionnelle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès.

Pour en savoir plus sur l’utilisation de l’assistant AEM Forms AI , consultez la documentation de l’[assistant AEM Forms AI](/help/edge/docs/forms/forms-ai-assistant.md) .

### Exemples de cas d’utilisation

* **« Créez un formulaire de commentaires client avec les champs de nom, d’e-mail, d’évaluation et de commentaires »**
* **« Convertir ce formulaire de demande PDF chargé en formulaire adaptatif numérique »**
* **« Ajoutez une logique conditionnelle pour afficher les informations sur le conjoint uniquement lorsque l’état civil est « Marié » »**
* **« Configurer ce formulaire pour envoyer des données au système de gestion de la relation client »**

Cet assistant IA d’AEM Forms spécialisé représente la prochaine évolution de la création de formulaires, associant la puissance de l’IA à des fonctionnalités de formulaires fiables d’AEM afin de rationaliser votre processus de création de formulaires.
