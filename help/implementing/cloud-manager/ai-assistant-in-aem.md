---
title: Assistant IA dans AEM
description: Utilisez l’Assistant IA pour vous aider à trouver des réponses et à résoudre les problèmes liés aux solutions disponibles dans Adobe Experience Manager.
solution: Experience Manager
feature: Authoring, AI Assistant, AI Tools
role: Admin, Developer, User
exl-id: 81e7b1ac-50d0-4547-8622-bf145ebc3dc0
source-git-commit: 0fdc71bad1f2c4844ad47d41f47e898eac8c2373
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 78%

---

# Assistant IA dans AEM {#about-ai-assistant-in-aem}

L’assistant d’IA dans Adobe Experience Manager (AEM) offre une interface de conversation conçue pour rationaliser la recherche de réponses à vos requêtes liées à AEM. Il apporte des réponses instantanées à vos questions sur les produits AEM (*disponible pour l’ensemble des utilisateurs et utilisatrices*) et automatise la création de tickets d’assistance (*disponible pour les administrateurs et administratrices de l’assistance*).

L’assistant IA prend en charge AEM as a Cloud Service, notamment les solutions suivantes :

* Page de vue d’ensemble d’Experience Hub
* Edge Delivery Services
* Sites
* Assets
* Forms
* Dynamic Media
* Cloud Manager


Il est directement incorporé à AEM et accessible à partir de l’interface d’utilisation d’AEM Experience Hub, de Cloud Manager et de l’instance de création.

La vidéo de 3 minutes et 25 secondes qui suit fait une présentation détaillée de l’assistant IA d’AEM.

>[!VIDEO](https://video.tv.adobe.com/v/3475360/?captions=fre_fr&learn=on&enablevpops)

## Accéder à l’assistant IA dans AEM{#get-access}

Pour accéder à l’assistant IA dans AEM, les clientes et clients doivent disposer des éléments suivants :

* Autorisation d’utiliser l’assistant IA dans AEM pour la connaissance des produits. Cette autorisation vous permet de poser des questions relatives aux produits dans la conversation de l’assistant IA. Cette autorisation doit être activée.
* Autorisation d’ouvrir les tickets d’assistance, qui nécessite le rôle d’**administration de l’assistance**.

>[!NOTE]
>
>Les demandes de l’assistant IA dans AEM sont authentifiées via Adobe Identity Management Services (IMS). Pour plus d’informations, consultez la [vue d’ensemble d’Adobe Identity Management Services](https://www.adobe.com/cc-shared/assets/pdf/trust-center/ungated/whitepapers/corporate/adobe-identity-management-services-security-overview.pdf).

**Pour accéder à l’assistant IA dans AEM :**

1. Les clientes et clients doivent disposer d’un accord supplémentaire pour accéder à la plupart des fonctionnalités d’IA et d’agent dans Adobe Experience Manager. Pour plus d’informations, contactez votre représentant ou représentante Adobe.

1. Pour utiliser l’assistant IA dans AEM, l’autorisation d’accéder à la connaissance des produits par l’intermédiaire de l’assistant IA est obligatoire. Le système active cette autorisation par défaut.

   Si vous souhaitez contrôler qui peut accéder à la base de connaissance des produits, envoyez un e-mail à [aemaiassistant@adobe.com](mailto:aemaiassistant@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Adobe peut activer le contrôle d’accès au niveau de l’utilisateur ou de l’utilisatrice. Lorsque cette option est activée, votre administrateur peut accorder un accès au niveau de l’utilisateur à l’aide de [Configurer l’assistant AI dans AEM](/help/implementing/cloud-manager/ai-assistant-in-aem-admin.md).

## Portée {#scope}

Le périmètre actuel de l’assistant IA d’AEM est axé sur les questions de connaissance des produits pour AEM as a Cloud Service. Ce champ d’application inclut une prise en charge complète des domaines principaux. <!--, such as Sites, Assets, Forms, Edge Delivery Services, Dynamic Media, and Cloud Manager. -->

* **Surfaces** : disponible dans AEM Experience Hub, l’interface d’utilisation de création, Cloud Manager.
* **Fonctionnalités** : connaissance du produit et ressource principale pour le dépannage et les conseils, la création automatisée de tickets d’assistance et la recherche.
* **Valeur** : réduit le temps, accélère l’apprentissage et le délai de rentabilisation, réduit la nécessité de créer manuellement des tickets d’assistance et améliore l’efficacité de la création de tickets d’assistance.

## Confidentialité, sécurité et gouvernance{#privacy-security-governance}

L’assistant AI d’AEM est conçu pour être axé sur la confidentialité, la sécurité et la gouvernance.

Cet article décrit les fonctionnalités centrées sur la confiance que vous pouvez attendre de l’assistant IA d’AEM :

* L’assistant AI dans AEM n’utilise pas de données personnelles, y compris à des fins de formation.
* L’assistant IA d’AEM n’a pas accès aux données des clientes et clients.
* Une autorisation explicite est requise pour interagir avec l’assistant IA d’AEM.
* Les prompts fournis par les utilisateurs ou les utilisatrices (questions, requêtes, etc.) ne sont pas partagés avec d’autres clientes et clients.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->

## Découvrez l’assistant AI dans AEM pour la connaissance des produits et la création automatisée de tickets d’assistance {#ai-prod-insights}

La connaissance des produits englobe les concepts et les sujets issus de la documentation d’Adobe Experience League. Ces questions peuvent être classées dans les sous-groupes suivants :


| Connaissances des produits | Disponible pour l’ensemble des utilisateurs et des utilisatrices<br>Exemples |
| :--- | :--- |
| Apprentissage par points | <ul><li>Qu’est-ce que l’éditeur universel ?</li><li>Comment créer un programme dans Cloud Manager ?</li></ul> |
| Découverte ouverte | <ul><li>Comment utiliser l’éditeur universel ?</li><li>Existe-t-il un moyen de copier du contenu d’un environnement à un autre ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi ne puis-je pas accéder à l’éditeur universel ?</li><li>Pourquoi mon pipeline échoue-t-il ?</li></ul> |
| **Création de ticket d’assistance** | **Disponible uniquement pour les administrateurs et administratrices &#x200B;**<br>**Exemples** |
| Création automatisée de tickets d’assistance capturant l’historique et le contexte de la conversation de l’assistant IA | <ul><li>Créez un ticket d’assistance pour moi.</li></ul> |
| Récupération du statut du ticket d’assistance | <ul><li>Montre-moi tous les tickets d’assistance que j’ai ouverts.</li><li>Montre-moi le statut du ticket « E----------- ».</li></ul> |

{style="table-layout:auto"}


## Formulation de questions efficaces {#ai-craft-questions}

Pour recevoir les réponses les plus précises de la part de l’assistant AI dans AEM, il est important de formuler vos questions clairement et avec le contexte. Suivez les conseils suivants pour vous assurer que vos requêtes sont claires et bien structurées :

* Exposez clairement votre tâche ou votre question de façon concise.
* Pour une meilleure compréhension, évitez les formulations ambiguës ou les syntaxes trop complexes.
* Fournissez un contexte pertinent sur votre tâche ou votre question, car cette approche aide l’assistant IA d’AEM à fournir des réponses plus précises et plus pertinentes. Par exemple, nommez la solution AEM dans votre invite.

### Exemples de questions non prises en charge {#ai-unsupported-questions}

| Aire | Exemples |
| --- | --- |
| Informations opérationnelles | <ul><li>Combien y a-t-il d’environnements de développement dans mon instance locataire ?</li><li>Qui a lancé le dernier pipeline de production ?</li></ul> |
| Résolution des problèmes | <ul><li>Pourquoi mon pipeline de production échoue-t-il ?</li></ul> |
| Tâche et automatisation | <ul><li>Configure un pipeline de qualité du code à partir d’une branche de développement.</li></ul> |


## Utiliser l’assistant IA dans AEM {#ai-use}

<!--
 UNHIDE AFTER BETA or at GA
### Enable AI Assistant in AEM access through Admin Console 

To use AI Assistant in AEM, your organization must opt in at the Admin Console level. A product administrator creates (or chooses) a user group and grants it the new "AI Assistant" permission. Anyone added to that group instantly gains access to the Assistant across AEM. If the goal is company-wide availability, the admin simply assigns all users to that group.

![AI Assistant in AEM in the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

From an employee's perspective, the process is straightforward: identify the product administrator for Adobe Experience Manager in your organization and request to be added to the AI-enabled user group. Once you appear in that group, the Assistant icon shows up automatically the next time you sign in.

Administrators should keep normal Cloud Manager governance in mind. Hold product administrator rights in the Admin Console to create profiles, manage user groups, or edit permissions. If users also need the Assistant's built-in **Create Support Ticket** feature, add the standard **Support Admin** role (standard Admin Console role) to the same individuals or group.

![Technical support ticket creation in AI Assistant in AEM of the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

For a guided walkthrough of setting up users and groups in AEM as a Cloud Service, see [Configuring access to AEM as a Cloud Service ](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/overview). 

See also [Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md).
-->


### Démarrer une conversation avec l’assistant IA d’AEM

Vous pouvez réinitialiser l’assistant IA d’AEM et démarrer une nouvelle conversation lorsque vous souhaitez changer de sujet. Cette fonctionnalité est particulièrement utile lors de la résolution des problèmes liés aux requêtes qui échouent ou produisent des résultats incorrects.

**Pour démarrer une conversation avec l’assistant IA d’AEM :**

1. Dans le coin supérieur droit de l’interface d’utilisation d’AEM (à partir des pages Cloud Manager ou de l’instance de création des environnements AEM), cliquez sur l’icône **Assistant IA**.

   ![Icône Assistant IA de la barre d’outils](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

1. Dans la zone de texte du panneau **Assistant IA** située en bas, saisissez votre question ou votre prompt, puis appuyez sur `Enter` ou cliquez sur ![icône Envoyer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   >[!NOTE]
   >
   >Les données personnelles ne doivent pas être incluses dans vos saisies, car elles ne sont pas nécessaires pour utiliser cet outil.

   ![Zone de texte au bas du panneau de l’assistant IA](/help/implementing/cloud-manager/assets/ai-assistant-prompt-text-box.png)

1. Pour démarrer une nouvelle conversation (un nouveau sujet ou un changement de sujet), cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) > **Démarrer une nouvelle conversation**.

   ![Démarrer une nouvelle conversation dans l’assistant IA à partir de l’icône représentant des points de suspension](/help/implementing/cloud-manager/assets/ai-assistant-start-new-conversation.png)

### Découvrir les prompts par catégorie

L’assistant IA d’AEM comprend une fonctionnalité de découverte pour vous aider à explorer les rubriques et catégories prises en charge.

**Pour découvrir des prompts par catégorie :**

1. Dans le panneau de l’assistant IA, cliquez sur ![Icône Apprendre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg) pour activer le panneau de découverte de prompt.

   ![Panneau qui vous permet d’explorer les invites par catégorie dans l’assistant AI](/help/implementing/cloud-manager/assets/ai-assistant-discover-prompts.png)
   *Panneau affichant les catégories de prompt dans l’assistant IA.*

1. Sélectionnez une catégorie pour afficher la liste des prompts associés.
1. Sélectionnez un prompt pour afficher des exemples des types de questions auxquelles l’assistant IA peut répondre.

1. Pour masquer le panneau de détection de prompt, recliquez sur ![Icône Apprendre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).

### Partager vos commentaires sur l’assistant IA d’AEM

Vos commentaires aident Adobe à améliorer l’assistant IA et ainsi ses performances et sa précision.

Partagez vos commentaires sur votre expérience avec l’assistant IA d’AEM à l’aide des options suivantes :

![Icônes de pouce vers le haut/vers le bas, et de drapeau](/help/implementing/cloud-manager/assets/ai-assistant-feedback-icons.png)

| Cliquer | Description |
| --- | --- |
| ![Icône de pouce vers le haut](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Indiquez ce qui s’est bien passé et partagez des commentaires positifs. |
| ![Icône de pouce vers le bas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Fournissez des suggestions d’amélioration. Ajoutez des commentaires spécifiques sur votre expérience. Ils sont examinés quotidiennement. |
| ![Icône de drapeau](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Signalez tout problème ou fournissez des commentaires détaillés sur votre interaction avec l’assistant IA d’AEM. |

## Questions fréquentes sur l’assistant IA d’AEM {#ai-faq}

Voici les réponses à certaines questions courantes sur l’assistant IA:

* **L’assistant AI dans AEM fournit-il des informations en temps réel ?**\
  Non. L’assistant IA puise son contenu dans la documentation d’Adobe Experience League. Les mises à jour apportées au contenu prennent un certain temps à se refléter dans ses réponses.
* **Quelles applications Adobe l’assistant IA d’AEM prend-il en charge ?**\
  Actuellement, l’assistant AI prend en charge les demandes d’informations sur les produits dans AEM as a Cloud Service, tels que Sites, Assets, Dynamic Media, Cloud Manager et Forms.
* **Quelles sont les fonctionnalités de l’assistant IA d’AEM ?**\
  L’assistant IA d’AEM est conçu pour répondre aux requêtes liées à la connaissance des produits Adobe.
* **L’assistant IA d’AEM utilise-t-il des informations personnelles pour les données d’apprentissage ?**\
  Non. L’assistant IA d’AEM n’utilise pas d’informations personnelles à des fins d’entraînement. Évitez de partager des informations personnelles, y compris les noms ou coordonnées, avec l’assistant AI dans AEM.

<!--
 IS THE DOCUMENTATION BELOW STILL NEEDED? IF SO, GO AHEAD AND DELETE THE COMMENT TAGS!!

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
