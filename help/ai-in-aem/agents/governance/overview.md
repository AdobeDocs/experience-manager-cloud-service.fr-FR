---
title: Présentation de l’agent de gouvernance
description: Découvrez comment l’agent de gouvernance AEM protège l’intégrité et la conformité de la marque dans AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 9b26cd1f30ad6fa23e28c9f36fe48091e069962e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Présentation de l’agent de gouvernance {#governance-agent}

L’**agent de gouvernance** est une solution conçue pour protéger l’intégrité et la conformité de la marque dans Adobe Experience Manager. Il applique des politiques de sécurité, de réglementation et de marque pour s’assurer que chaque interaction et activation respecte les normes établies. L’agent de gouvernance est entièrement intégré à l’assistant d’IA et est conçu pour fonctionner de manière transparente dans les environnements d’entreprise en tirant parti des outils **A2A (agent à agent)** et **MCP (protocole de contrôle de modèle)**. Ces intégrations permettent à l’agent de se connecter à des orchestrateurs d’IA avancés tels que ChatGPT, Claude et d’autres systèmes d’IA externes, assurant ainsi une intelligence flexible et évolutive entre les plateformes.

Les principales fonctionnalités sont les suivantes :

* **Gouvernance des marques :** maintenez la cohérence de la marque et réduisez les révisions manuelles en automatisant les vérifications de marque sur le contenu et les ressources
* **Autorisations et Digital Rights Management (DRM) :** garantit une collaboration sécurisée et conforme en contrôlant les autorisations et les droits d’utilisation des ressources numériques.

En combinant ces fonctionnalités, l’agent de gouvernance réduit les risques et permet une diffusion rapide, sécurisée et sur la marque à grande échelle.

>[!IMPORTANT]
>
>Les réponses générées par l&#39;IA peuvent être inexactes ou trompeuses. Assurez-vous de vérifier les correctifs et les réponses suggérés.
>
>Consultez également les [Directives d’utilisation de l’IA générative de Adobe Experience Cloud](https://www.adobe.com/fr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Compétences en agent de gouvernance AEM {#skills-in-aem-governance-agent}

### Gouvernance de marque {#brand-governance}

L’agent de gouvernance peut valider le contenu par rapport aux directives de la marque afin d’assurer la cohérence entre toutes les expériences digitales. Il utilise des règles de marque préingérées, telles que le ton, les revendications, l’utilisation du logo, la typographie et l’imagerie. Il fonctionne en temps réel dans le mode chat, éditeurs et lot dans Experience Hub, ce qui le rend idéal pour le contenu généré par l’IA, les migrations de site et la création de site brève.

![Présentation de la gouvernance de marque](/help/ai-in-aem/agents/governance/assets/brand-governance.png)

**Exemples d’invites :**

* *Cette page est-elle alignée sur ma marque ?`https://www.website/en.html`*
* *Ce `https://www.website/en.html` suit-il les directives relatives aux messages de marque ?*
* *Vérifiez si `https://www.website/homepage` suit les directives de la marque*
* *Afficher mes directives de marque*

### Autorisation et Digital Rights Management {#permission-and-digital-rights-management}

#### Gestion des autorisations dans Content Hub {#permission-management-in-content-hub}

Dans Content Hub, l’agent de gouvernance s’assure que seules les bonnes personnes accèdent aux bonnes ressources au bon moment. En appliquant des contrôles granulaires basés sur les attributs et les droits d’utilisation, il protège le contenu sensible tout en permettant une collaboration sécurisée. Cela signifie des risques de conformité réduits, une intégrité de marque renforcée et des workflows plus rapides. Les équipes peuvent ainsi partager et réutiliser des ressources en toute confiance, sans se soucier des risques d’accès non autorisé ou d’utilisation abusive. Cet équilibre entre sécurité et flexibilité se traduit par une efficacité opérationnelle et une confiance accrues dans l’ensemble de l’organisation.

![Présentation de la gestion des autorisations](/help/ai-in-aem/agents/governance/assets/permission-management.png)

**Exemples d’invites :**

* *Afficher toutes les règles ABAC Content Hub existantes.*
* *Créez une règle qui donne au groupe « Marketing » l’accès à toutes les ressources.*
* *Accorder au groupe des ventes l’accès aux ressources dont le marketing:segment est égal à EMEA.*
* *Supprimer toutes les règles qui donnent accès à l&#39;agence externe*
* *Qu&#39;est-ce que l&#39;ABAC dans Content Hub et que pouvez-vous m&#39;aider à faire ?*

#### Assets Digital Rights Management {#assets-digital-rights-management}

À l’aide de l’agent, vous pouvez gérer vos droits numériques Assets dans votre écosystème de contenu. Il contrôle les autorisations et les droits d’utilisation à un niveau granulaire, en veillant à ce que les ressources soient accessibles et utilisées uniquement dans les limites de conformité définies. Vous bénéficiez ainsi d’une tranquillité d’esprit, protégez la propriété intellectuelle, réduisez les risques réglementaires et conservez l’intégrité de la marque. En automatisant l’application des droits, les équipes peuvent collaborer en toute sécurité et en toute confiance, accélérant ainsi la distribution de contenu sans compromettre la sécurité ni la conformité.

![Présentation de la gestion DRM](/help/ai-in-aem/agents/governance/assets/drm-management.png)

**Exemples d’invites :**

* *Certaines de mes ressources expirent-elles bientôt ?*
* *Retrouvez-moi toutes les ressources de vélo qui ont expiré le mois dernier.*
* *Quelles ressources ont récemment expiré ?*
* *Rechercher des ressources sans date d’expiration*
* *Afficher toutes les ressources dans /content/dam/products qui vont expirer dans les 14 prochains jours*

