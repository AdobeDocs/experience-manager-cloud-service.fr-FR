---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 05531a5c1eca996bd3652d6ce6233b7a960d0bc9
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 7%

---


# Présentation {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code."

Découvrez les points de contrôle qualité disponibles dans le [processus de déploiement AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) et les différents types de tests fonctionnels intégrés. Découvrez comment contribuer et optimiser leur utilisation dans le cadre d’une stratégie de test exhaustive.

## A propos des tests fonctionnels

Le diagramme suivant présente un aperçu général des pipelines disponibles dans le cadre d’une stratégie de test globale et du [processus de déploiement AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![ Points de contrôle qualité du déploiement AEM Cloud Service](assets/functional-testing/quality-gates-compact.svg)

## Objectif des tests fonctionnels

Les pipelines de déploiement d’AEM Cloud Service ont pour objectif de faciliter des déploiements robustes et sécurisés à différentes étapes de votre développement et d’AEM cycle de vie des versions du produit. Ces pipelines intègrent plusieurs points de contrôle de qualité à différents niveaux afin de garantir l’intégrité et la sécurité des déploiements pour vos modifications d’applications AEM et pour AEM mises à jour de produits.

Adobe fournit plusieurs points de contrôle qualité intégrés, tandis que d’autres nécessitent votre intervention pour la mise en oeuvre et la configuration. Ces points de contrôle qualité sont polyvalents, s’appliquent à différentes étapes du cycle de vie et s’intègrent directement à votre configuration de développement et à vos processus CI/CD.

Les points de contrôle qualité intégrés valident principalement les fonctionnalités du produit AEM dans le contexte de votre application AEM. En revanche, les points de contrôle de qualité personnalisés que vous configurez sont conçus pour vérifier que les fonctionnalités critiques de votre application et les interactions utilisateur fonctionnent comme prévu. Collectivement, ces deux ensembles de points de contrôle de qualité fonctionnent ensemble pour garantir des déploiements automatisés robustes et sécurisés pour vos modifications de code et pour AEM mises à jour de produit.

Il est important de noter que ces points de contrôle qualité ne sont pas destinés à constituer un cadre de test complet pour l’ensemble de votre stratégie de test. Le produit AEM est soumis à des tests approfondis avant d’entrer dans le processus de déploiement du service cloud AEM. De même, votre application doit déjà être de haute qualité avant d’atteindre la phase de déploiement. Cette approche permet de s’assurer que les points de contrôle de qualité se concentrent sur leur principal objectif de protection du processus de déploiement, plutôt que de se substituer à un régime de test complet.

## Points de contrôle de qualité dans les tests

Le diagramme suivant fournit une vue détaillée des points de contrôle qualité disponibles et de leur utilisation dans la stratégie de test globale et le [processus de déploiement AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![ Points de contrôle qualité du déploiement AEM Cloud Service](assets/functional-testing/quality-gates-overview.svg)

### Points de contrôle qualité fournis par le client récapitulatif

|                               | Tests unitaires | Tests fonctionnels personnalisés<br/> | Tests de l’interface utilisateur personnalisés<br/> | Validations du client<br/> | Test manuel<br/> |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Pipeline de production** | Oui<br/>Blocking<br/> | Oui<br/>Blocking<br/>60m Timeout | Oui<br/>Blocking<br/>Délai d’expiration de 30 m | Non | Non |
| **Pipeline hors production** | Oui<br/>Blocking<br/> | Opt-in<br/>Blocking<br/>Délai d’expiration de 60 m | Opt-in<br/>Blocking<br/>Délai d’expiration de 30 m | Non | Non |
| **Adobe la validation interne** | Oui<br/>Blocking<br/> | Oui<br/>Blocking<br/>60m Timeout | Oui<br/>Blocking<br/>Délai d’expiration de 30 m | Non | Non |
| **Customer CI/CD** | Oui | Oui | Oui | Oui | Oui |
| **Développeur local du client** | Oui | Oui | Oui | Oui | Oui |

### Test unitaire

Nous vous recommandons de fournir les tests unitaires pour votre application AEM, qui constituent la base de chaque stratégie de test. Ils sont conçus pour fonctionner rapidement et souvent et donner des retours rapides et précoces. Ils sont étroitement intégrés aux workflows des développeurs, à vos propres CI/CD et aux pipelines de déploiement du service cloud d’AEM.

Ils sont implémentés à l’aide de JUnit et exécutés avec Maven. Consultez le module [core de l’archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/using#unit-tests) pour obtenir un exemple de test unitaire pour AEM et pour commencer.

### Qualité du code

Ce point de contrôle qualité est configuré prêt à l’emploi et exécute une analyse de code statique sur votre code d’application AEM.

Voir [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) et [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour plus d’informations.

### Tests de produit

Les tests fonctionnels du produit sont des tests d’intégration HTTP stables (IT) pour les fonctionnalités de base de l’AEM, y compris les tâches de création et de réplication. Adobe les fournit et les conserve prêts à l’emploi. Elles sont destinées à empêcher le déploiement des modifications apportées au code d’application personnalisé si celui-ci rompt les fonctionnalités de base du produit AEM.

Ils utilisent JUnit pour la mise en oeuvre, exécutent avec Maven et dépendent des [clients de test d’AEM ](https://github.com/adobe/aem-testing-clients) officiels. La suite de tests de produit est conservée en tant que
Un [projet open source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) suit les bonnes pratiques et peut être considéré comme un bon point de départ pour la mise en oeuvre de vos tests.

### Tests fonctionnels personnalisés

Tout comme les tests de produit, les tests fonctionnels du client sont les tests d’intégration HTTP (IT) implémentés avec JUnit, exécutés à l’aide de Maven et conçus sur les [clients de test d’AEM ](https://github.com/adobe/aem-testing-clients) officiels.

>[!NOTE]
>
>Les tests fonctionnels personnalisés s’exécutent sur les pipelines de production et hors production (opt-in) utilisés pour AEM les déploiements de changement d’application et AEM les mises à jour push de produit. Ils jouent un rôle essentiel pour assurer le bon fonctionnement de votre application et pour améliorer la sécurité de la version. Les tests fonctionnels du client sont également exécutés dans des pipelines internes de validation de version préliminaire pour chaque client, ce qui permet de fournir des commentaires anticipés.

Pour garantir des exécutions de pipeline efficaces, Adobe conseille de se concentrer sur les fonctionnalités clés et les flux d’interaction utilisateur principaux, en vue d’une exécution de test fonctionnel d’environ 15 minutes ou moins. Les suites de tests fonctionnels complètes qui dépassent ce délai doivent être exécutées dans le cadre des pipelines de validation client généraux pendant le processus de développement.

Voir [tests de produit Open Source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) ou le module [it.tests de l’archétype de projets AEM](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) pour consulter des exemples.

Pour plus d’informations, consultez [Tests fonctionnels Java](/help/implementing/cloud-manager/java-functional-testing.md).

### Tests de l’interface utilisateur personnalisée

Pour optimiser le contrôle des risques pour votre développement spécifique au client, Adobe vous encourage à capturer des tests d’interface utilisateur critiques dans AEM as a Cloud Service. Limitez-les, mais ciblez-les sur l’optimisation de leur impact sur l’expérience client.

Les tests sont conditionnés dans une image Docker, conçue pour être aussi volatile que possible (avec prise en charge de Cypress, Playwright, Selenium, Java et JavaScript). Ils suivent les mêmes caractéristiques et objectifs que les tests fonctionnels personnalisés.

>[!NOTE]
>
>Les tests d’interface utilisateur personnalisés sont exécutés dans les pipelines de production et hors production (opt-in) utilisés pour AEM déploiement des modifications d’application et AEM les mises à jour push de produit. Ils sont essentiels pour assurer le bon fonctionnement de votre application et améliorer la sécurité de la version. Les tests de l’interface utilisateur client sont également exécutés dans des pipelines internes de validation de version préliminaire pour chaque client, ce qui permet de fournir des commentaires anticipés.
>
>Les conteneurs non Selenium doivent exécuter des tests à l’aide d’un proxy HTTP basé sur les variables d’environnement dans la [section de test de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

Pour que les exécutions de pipeline restent efficaces, Adobe recommande de se concentrer sur les fonctionnalités clés et les principaux flux d’interaction utilisateur. Les suites de tests d’interface utilisateur complètes qui dépassent ce point de contrôle qualité doivent être exécutées dans le cadre des pipelines de validation client généraux. Intégrez-les au processus de développement du client.

Pour obtenir des exemples, reportez-vous à la section [Exemple de test Open Source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) ou au module [ui.tests de l’AEM’archétype Projets](/help/implementing/cloud-manager/ui-testing.md) .

Pour plus d’informations, consultez [Tests personnalisés de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Audit d’expérience

Le point de contrôle de la qualité de l’expérience effectue des audits [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/) sur la page web du client.

Ce point de contrôle qualité est fourni par AEM prêt à l’emploi, mais ne bloque pas les pipelines de déploiement. Par défaut, un audit de la page racine (`/`) de l’instance de publication est effectué. Vous pouvez contribuer en configurant jusqu’à 25 chemins personnalisés pris en compte pour les audits.

Pour plus d’informations, voir [Test d’audit d’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md) .

### Validations client

Le point de contrôle qualité des validations client est un espace réservé à la stratégie et aux efforts de test du client, exécuté avant que les modifications de l’application du client n’atteignent les pipelines de déploiement cloud AEM.

Vous pouvez y choisir les outils et les structures que vous préférez. Contrairement aux tests de fonction client et aux tests d’interface utilisateur personnalisés, il n’existe aucune limite liée à AEM as a Cloud Service. Par conséquent, Adobe vous recommande d’effectuer ici des tests fonctionnels et d’interface utilisateur de longue durée.

Bien que vous puissiez choisir n’importe quel outil et structure, Adobe vous suggère d’aligner les tests d’intégration et d’interface utilisateur basés sur HTTP avec les outils et les structures utilisés aux points de contrôle de qualité des tests fonctionnels et d’interface utilisateur personnalisés. En outre, Adobe recommande d’incorporer [des environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) dans votre stratégie de test locale pour refléter AEM les environnements cloud de près.

### Test manuel

Le point de contrôle qualité des tests manuels est un espace réservé pour les clients qui effectuent des tests manuels. Comme les pipelines de cloud AEM ne prennent pas en charge les tests manuels, ils doivent être inclus dans votre stratégie de test locale.

Pour les tests manuels, il peut s’avérer utile de l’intégrer à un environnement de développement AEM Cloud Service supplémentaire.
