---
title: Assistant AI dans AEM
description: Utilisez l’assistant AI pour vous aider à trouver des réponses et à résoudre les problèmes liés aux solutions disponibles dans Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive"
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 99f4e5731d5631981986a783534c820ad8f7088a
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---

# Assistant AI dans AEM {#aem-home}

L’assistant d’IA d’AEM (Adobe Experience Manager) offre une interface de conversation conçue pour rationaliser la recherche de réponses à vos requêtes liées à Adobe Experience Manager. Il vous permet d’obtenir des réponses instantanées à vos questions sur les produits AEM (*disponible pour tous les utilisateurs*) et d’automatiser la création de tickets d’assistance (*disponible pour les administrateurs de l’assistance*).

L’assistant AI prend en charge AEM as a Cloud Service, notamment les solutions suivantes :

* Page d’aperçu d’Experience Hub
* Edge Delivery Services
* Sites
* Assets
* Forms
* Dynamic Media
* Cloud Manager


Il est directement incorporé à AEM et accessible à partir de l’interface utilisateur d’AEM Experience Hub, de Cloud Manager et de l’instance de création.

La vidéo de 3 minutes et 39 secondes qui suit présente une présentation détaillée de l’assistant d’IA dans AEM.

>[!VIDEO](https://video.tv.adobe.com/v/3470354?learn=on)

## Accès à l’assistant AI dans AEM{#get-access}

1. [Les clients doivent signer l’avenant IA dédiée à la génération avec Adobe](https://fieldreadiness-adobe.highspot.com/items/665f831c9f831b011aeda057#1).

   Le Rider GenAI est un accord légal entre un client et Adobe, qui est nécessaire pour utiliser la plupart des fonctionnalités d’IA et d’agence. Pour en savoir plus, contactez l’assistance clientèle d’Adobe.

1. L’administrateur AEM configure l’assistant AI à utiliser dans son organisation. Voir [Configuration de l’assistant AI dans AEM](/help/implementing/cloud-manager/aem-ai-assistant-admin.md).

<!--
>[!IMPORTANT]
>Be sure you have reviewed and submitted the user agreement so Adobe can enable the AI Assistant feature for you to test out and participate in the private beta program.
>
>For any questions, send an email to [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) from your email address associated with your Adobe ID. -->

## Portée {#scope}

Le périmètre actuel de l’assistant AI dans AEM se concentre sur les questions de connaissance des produits pour AEMr. as a Cloud Service. Ce champ d’application inclut une prise en charge complète des domaines clés. <!--, such as Sites, Assets, Forms, Edge Delivery Services, Dynamic Media, and Cloud Manager. -->

* **Surfaces** : disponible dans AEM Experience Hub, l’interface utilisateur de création, Cloud Manager.
* **Fonctionnalités** : connaissance du produit et première étape pour le dépannage et les conseils, la création automatisée de tickets d’assistance et la recherche.
* **Valeur** : permet de gagner du temps, d’accélérer l’apprentissage et la valorisation, de réduire la nécessité de créer manuellement des tickets d’assistance et d’améliorer l’efficacité de la création de tickets d’assistance.

## Confidentialité, sécurité et gouvernance{#privacy-security-governance}

L’assistant d’IA d’AEM est conçu et met l’accent sur la confidentialité, la sécurité et la gouvernance.

Cet article décrit les fonctionnalités centrées sur la confiance que vous pouvez attendre de l’assistant AI dans AEM :

* Aucune donnée personnelle n’est utilisée par l’assistant AI dans AEM, y compris à des fins de formation.
* L’assistant AI dans AEM n’a pas accès aux données des clients.
* Une autorisation explicite est requise pour interagir avec l’assistant AI dans AEM.
* Les invites fournies par l&#39;utilisateur (questions, requêtes, etc.) ne sont pas partagées avec d&#39;autres clients.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->

## Découvrez l’assistant AI dans AEM pour la connaissance des produits et la création automatisée de tickets d’assistance {#ai-prod-insights}

La connaissance des produits englobe les concepts et les sujets dérivés de la documentation d’Adobe Experience League. Ces questions peuvent être classées dans les sous-groupes suivants :


| Connaissances du produit | Disponible pour tous les utilisateurs<br>Exemples |
| :--- | :--- |
| Apprentissage par points | <ul><li>Qu’est-ce que l’éditeur universel ?</li><li>Comment créer un programme dans Cloud Manager ?</li></ul> |
| Ouvrir la découverte | <ul><li>Comment utiliser l’éditeur universel ?</li><li>Existe-t-il un moyen de copier du contenu d’un environnement à un autre ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi ne puis-je pas accéder à l’éditeur universel ?</li><li>Pourquoi mon pipeline échoue-t-il ?</li></ul> |
| **Création de ticket d’assistance** | **Disponible uniquement pour les administrateurs &#x200B;**<br>**exemples** |
| Création automatisée de tickets d’assistance capturant l’historique et le contexte de la conversation de l’assistant AI | <ul><li>Créez un ticket d’assistance pour moi.</li></ul> |
| Récupération du statut du ticket d’assistance | <ul><li>Montrez-moi tous les tickets d&#39;assistance que j&#39;ai ouverts.</li><li>Me montrer le statut du ticket « E----------- »</li></ul> |

{style="table-layout:auto"}


## Comment concevoir des questions efficaces {#ai-craft-questions}

Pour recevoir les réponses les plus précises de la part de l’assistant d’IA dans AEM, il est important de formuler vos questions avec clarté et contexte. Suivez les conseils suivants pour vous assurer que vos requêtes sont claires et bien structurées :

* Exposez clairement votre tâche ou votre question de façon concise.
* Évitez les termes ambigus ou les syntaxes trop complexes pour améliorer la compréhension.
* Fournissez un contexte pertinent sur votre tâche ou votre question, car cette approche aide l’assistant d’IA d’AEM à fournir des réponses plus précises et plus pertinentes.
Par exemple, dans votre invite, il est utile de nommer la solution AEM dans laquelle vous travaillez : Sites, Assets, Dynamic Media, Edge Delivery Services, Cloud Manager ou Forms.

### Exemples de questions non prises en charge {#ai-unsupported-questions}

| Aire | Exemples |
| --- | --- |
| Informations opérationnelles | <ul><li>Combien y a-t-il d’environnements de développement dans mon client ?</li><li>Qui a lancé le dernier pipeline de production ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi mon pipeline de production échoue-t-il ?</li></ul> |
| Tâche et automatisation | <ul><li>Configurez un pipeline de qualité du code à partir d’une branche de développement.</li></ul> |


## Utilisation de l’assistant AI dans AEM {#ai-use}

<!-- UNHIDE AFTER BETA or at GA
### Enable AI Assistant in AEM access through Admin Console 

To use the AI Assistant in AEM, your organization must opt in at the Admin Console level. A product administrator creates (or chooses) a user group and grants it the new "AI Assistant" permission. Anyone added to that group instantly gains access to the Assistant across AEM. If the goal is company-wide availability, the admin simply assigns all users to that group.

![AI Assistant in AEM in the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

From an employee's perspective, the process is straightforward: identify the product administrator for Adobe Experience Manager in your organization and request to be added to the AI-enabled user group. Once you appear in that group, the Assistant icon shows up automatically the next time you sign in.

Administrators should keep normal Cloud Manager governance in mind. Hold product administrator rights in the Admin Console to create profiles, manage user groups, or edit permissions. If users also need the Assistant's built-in **Create Support Ticket** feature, add the standard **Support Admin** role (standard Admin Console role) to the same individuals or group.

![Technical support ticket creation in the AI Assistant in AEM of the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

For a guided walkthrough of setting up users and groups in AEM as a Cloud Service, see [Configuring access to AEM as a Cloud Service ](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/overview). 

See also [Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md). -->


### Démarrer ou réinitialiser un assistant d’IA dans une conversation AEM

Vous pouvez réinitialiser l’assistant d’IA dans AEM et démarrer une nouvelle conversation lorsque vous souhaitez changer de sujet. Cette fonctionnalité est particulièrement utile lors de la résolution des problèmes liés aux requêtes qui échouent ou fournissent des informations incorrectes.

![bouton Démarrer la conversation](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**Pour démarrer ou réinitialiser une conversation, procédez comme suit**

1. Dans l’assistant AI d’AEM, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Pour informer l’assistant AI d’une nouvelle rubrique ou d’une modification de rubrique, cliquez sur **Démarrer une nouvelle conversation**.

### Utilisation de la visibilité

L’assistant AI d’AEM comprend une fonction de capacité de découverte pour vous aider à explorer les rubriques et catégories prises en charge.

![Icône d’ampoule idéale](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**Pour utiliser la capacité de découverte, procédez comme suit**

1. Dans le coin supérieur droit de l’assistant d’IA, cliquez sur ![Icône Apprendre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Sélectionnez une catégorie pour afficher la liste des invites associées.
1. Choisissez une invite pour mieux comprendre les types de questions auxquelles l’assistant d’IA dans AEM peut répondre.

### Fournir des commentaires sur l’assistant d’IA dans AEM

Vos entrées permettent d’améliorer l’assistant d’IA dans AEM pour des performances optimales et une meilleure précision.

Partagez vos commentaires sur votre expérience avec l’assistant AI dans AEM à l’aide des options suivantes :

![Pouces vers le haut, pouces vers le bas et icônes d’indicateur](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Icône | Description |
| --- | --- |
| ![Icône pouce vers le haut](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Cliquez pour indiquer ce qui s’est bien passé et partager des commentaires positifs. |
| ![Icône pouce vers le bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Cliquez pour fournir des suggestions d’amélioration. Ajoutez des commentaires spécifiques sur votre expérience, qui sont examinés quotidiennement. |
| ![Icône Indicateur](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Cliquez pour signaler des préoccupations ou fournir des commentaires détaillés sur votre interaction avec l’assistant d’IA dans AEM. |

## Questions fréquentes sur l’assistant AI dans AEM {#ai-faq}

Voici les réponses à certaines questions courantes sur l’assistant d’IA :

* **Les informations fournies par l’assistant AI dans AEM sont-elles fournies en temps réel ?**\
  Non. L’assistant AI puise son contenu dans la documentation d’Adobe Experience League. Les mises à jour apportées au contenu peuvent prendre un certain temps à se refléter dans ses réponses.
* **Quelles applications Adobe l’assistant AI dans AEM prend-il en charge ?**\
  Actuellement, l’assistant AI prend en charge les demandes d’informations sur les produits dans AEM as a Cloud Service, notamment Sites, Assets, Dynamic Media, Cloud Manager et Forms.
* **Quelles sont les fonctionnalités de l’assistant AI dans AEM ?**\
  L’assistant AI d’AEM est conçu pour répondre aux requêtes liées à la connaissance du produit Adobe.
* **L’assistant AI d’AEM utilise-t-il des informations personnelles pour les données d’identification ?**\
  Non. AI Assistant dans AEM n’utilise pas d’informations personnelles à des fins de formation. Évitez de partager des informations personnelles vous concernant ou concernant d’autres personnes, y compris des noms ou des coordonnées, avec l’assistant AI dans AEM.

<!-- IS THE DOCUMENTATION BELOW STILL NEEDED? IF SO, GO AHEAD AND DELETE THE COMMENT TAGS!!

## AEM Forms AI Assistant (Forms Experience Builder) {#ai-forms-builder}

In addition to the general AI Assistant in AEM for product knowledge, AEM offers a specialized **[AEM Forms AI Assistant (Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)**. This enhanced assistant can actively help you create and configure forms through natural language prompts and answer questions specific to forms.

### Key capabilities

The AEM Forms AI Assistant provides:

* **Form Creation**: Create new forms from scratch using natural language descriptions.
* **Design Import**: Convert existing designs (PDF, Figma, images) into functional AEM Forms. 
* **Form Configuration**: Add fields, panels, validation rules, and conditional logic.
* **Layout Management**: Organize form structure and optimize for different devices.
* **Integration Setup**: Configure form submissions and data handling.
* **Product Knowledge**: Answer questions about AEM Forms features and best practices.

### Where to access

The AEM Forms AI Assistant is available in the following:

* **Universal Editor**: For Edge Delivery Services forms with visual editing capabilities.
* **Adaptive Forms Editor**: For detailed form configuration and advanced features.
* **Forms Management UI**: For high-level form creation and management tasks.

### Getting started

>[!NOTE]
>
> The AEM Forms AI Assistant (Forms Experience Builder) is available under the private beta program. Send an email from your work address to [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) to request access.

To learn more about using the AEM Forms AI Assistant , see the [AEM Forms AI Assistant](/help/edge/docs/forms/forms-ai-assistant.md) documentation.

### Example Use Cases

* **"Create a customer feedback form with name, email, rating, and comments fields"**
* **"Convert this uploaded PDF application form into a digital adaptive form"**  
* **"Add conditional logic to show spouse information only when marital status is 'Married'"**
* **"Configure this form to submit data to the Customer Relationship Management system"**

This specialized AEM Forms AI Assistant represents the next evolution in form building, combining the power of AI with AEM's robust forms capabilities to streamline your form creation workflow.
-->
