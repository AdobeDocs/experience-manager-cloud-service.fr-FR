---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1323'
ht-degree: 5%

---


# Présentation {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement d’AEM as a Cloud Service. Les tests garantissent la qualité et la fiabilité de votre code."

Découvrez les points de contrôle qualité disponibles dans le processus de déploiement [d’AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) ainsi que les différents types de tests fonctionnels intégrés. Découvrez comment contribuer et optimiser leur utilisation dans le cadre d’une stratégie de test complète.

## À propos des tests fonctionnels

Le diagramme suivant présente de manière générale les pipelines disponibles dans le cadre d’une stratégie de test globale et du processus de déploiement d’[AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![Points de contrôle de qualité du déploiement d’AEM Cloud Service](assets/functional-testing/quality-gates-compact.svg)

## Objectif des tests fonctionnels

Les pipelines de déploiement d’AEM Cloud Service ont pour objectif de faciliter des déploiements robustes et sécurisés à différentes étapes du cycle de vie du développement et des versions du produit AEM. Ces pipelines incorporent plusieurs points de contrôle qualité à différents niveaux pour garantir l’intégrité et la sécurité des déploiements pour vos modifications d’application AEM et les mises à jour de produits AEM.

Adobe fournit plusieurs points de contrôle qualité intégrés, tandis que d’autres nécessitent votre intervention pour l’implémentation et la configuration. Ces points de contrôle qualité sont polyvalents, s’appliquent à diverses étapes du cycle de vie et s’intègrent directement à votre configuration de développement et à vos processus CI/CD.

Les points de contrôle qualité intégrés valident principalement les fonctionnalités du produit AEM dans le cadre de votre application AEM. En revanche, les points de contrôle qualité personnalisés que vous configurez sont conçus pour vérifier que les fonctionnalités critiques de votre application et les interactions utilisateur s’exécutent comme prévu. Ensemble, ces deux ensembles de points de contrôle qualité fonctionnent pour garantir des déploiements automatisés robustes et sécurisés pour vos modifications de code et mises à jour de produits AEM.

Il est important de noter que ces points de contrôle qualité ne sont pas destinés à être un cadre de test complet pour l’ensemble de votre stratégie de test. Le produit AEM est soumis à des tests approfondis avant d’entrer dans le processus de déploiement du service cloud d’AEM. De même, votre application doit déjà être de haute qualité avant d’atteindre la phase de déploiement. Cette approche permet de s’assurer que les points de contrôle qualité se concentrent sur leur objectif principal, à savoir la sauvegarde du processus de déploiement, plutôt que de se substituer à un régime de test complet.

## Points de contrôle qualité dans les tests

Le diagramme suivant fournit une vue détaillée des points de contrôle qualité disponibles et de leur utilisation dans la stratégie de test globale et le processus de déploiement d’[AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![Points de contrôle de qualité du déploiement d’AEM Cloud Service](assets/functional-testing/quality-gates-overview.svg)

### Récapitulatif des points de contrôle qualité fournis par le client

|                               | Tests unitaires | Tests fonctionnels personnalisés<br/> | Tests personnalisés <br/> l’interface utilisateur | Validations <br/> client | Manuelle<br/> Test |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Pipeline de production** | Oui<br/>blocage<br/> | Délai <br/> blocage <br/> 60 millions | Délai d<br/>expiration de blocage <br/> 30 millions | Non | Non |
| **Pipeline hors production** | Oui<br/>blocage<br/> | Délai d’expiration <br/>’opt-in<br/>blocage de 60 millions | Délai d’expiration de 30 millions <br/> <br/>’opt-in/blocage | Non | Non |
| **Validation interne d’Adobe** | Oui<br/>blocage<br/> | Délai <br/> blocage <br/> 60 millions | Délai d<br/>expiration de blocage <br/> 30 millions | Non | Non |
| **Client CI/CD** | Oui | Oui | Oui | Oui | Oui |
| **développeur local du client** | Oui | Oui | Oui | Oui | Oui |

### Test unitaire

Nous vous recommandons de fournir les tests unitaires pour votre application AEM, qui sont la base de chaque stratégie de test. Ils sont destinés à fonctionner rapidement et souvent et à donner des commentaires précoces et rapides. Ils sont étroitement intégrés aux workflows de développement, à votre propre CI/CD et aux pipelines de déploiement de Cloud Service AEM.

Ils sont implémentés à l’aide de JUnit et exécutés avec Maven. Voir le [module principal de l’archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/using#unit-tests) pour un exemple de test unitaire pour AEM et la prise en main.

### Qualité du code

Ce point de contrôle qualité est configuré, prêt à l’emploi, et exécute une analyse de code statique sur le code de votre application AEM.

Voir [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) et [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour plus d’informations.

### Tests de produits

Les tests fonctionnels du produit sont des tests d’intégration HTTP (IT) stables pour les fonctionnalités de base d’AEM, y compris les tâches de création et de réplication. Adobe les fournit et les maintient prêts à l’emploi. Ils sont destinés à empêcher le déploiement des modifications apportées au code d’application personnalisé s’il interrompt les fonctionnalités de base du produit AEM.

Ils utilisent JUnit pour l’implémentation, s’exécutent avec Maven et s’appuient sur les [clients de test AEM officiels](https://github.com/adobe/aem-testing-clients). La suite de tests de produit est conservée en tant que
un [projet open source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) suit les bonnes pratiques et peut être considéré comme un bon point de départ pour la mise en œuvre de vos tests.

### Tests fonctionnels personnalisés

Tout comme les tests de produit, les tests fonctionnels du client sont des tests d’intégration HTTP implémentés avec JUnit, exécutés à l’aide de Maven et reposant sur les [clients de test AEM officiels](https://github.com/adobe/aem-testing-clients).

>[!NOTE]
>
>Les tests fonctionnels personnalisés s’exécutent dans les pipelines de production et hors production (opt-in) utilisés pour les déploiements de modifications d’applications AEM et les mises à jour des notifications push de produits AEM. Ils jouent un rôle essentiel pour assurer le bon fonctionnement de votre application et améliorer la sécurité des rejets. Les tests fonctionnels du client sont également exécutés dans les pipelines de validation de version préliminaire internes pour chaque client, ce qui permet de fournir un retour d’informations précoce.

Pour maintenir l’efficacité des exécutions de pipeline, Adobe conseille de se concentrer sur les fonctionnalités clés et les flux d’interaction des utilisateurs principaux, en visant une exécution de test fonctionnel d’environ 15 minutes ou moins. Les suites de tests fonctionnelles complètes qui dépassent ce temps doivent être exécutées dans le cadre des pipelines de validation client généraux pendant le processus de développement.

Voir [tests de produits open source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) ou le module [it.tests de l’archétype de projets AEM](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) pour obtenir des exemples.

Pour plus d’informations, consultez [Tests fonctionnels Java](/help/implementing/cloud-manager/java-functional-testing.md).

### Tests d’interface utilisateur personnalisés

Afin d’optimiser le contrôle des risques pour votre développement spécifique au client, Adobe vous incite à capturer des tests d’interface utilisateur critiques dans AEM as a Cloud Service. Limitez-les, mais concentrez-vous sur l’optimisation de leur impact sur l’expérience client.

Les tests sont empaquetés dans une image Docker conçue pour être aussi volatile que possible (avec la prise en charge de Cypress, Playwright, Selenium, Java et JavaScript). Ils suivent les mêmes caractéristiques et objectifs que les tests fonctionnels personnalisés.

>[!NOTE]
>
>Les tests d’interface utilisateur personnalisés sont exécutés dans les pipelines de production et hors production (opt-in) utilisés pour les déploiements de modifications d’applications AEM et les mises à jour des notifications push de produits AEM. Ils sont essentiels pour assurer le bon fonctionnement de votre application et améliorer la sécurité des rejets. Les tests de l’interface utilisateur client sont également exécutés dans les pipelines de validation de version préliminaire internes pour chaque client, ce qui permet de fournir des commentaires précoces.
>
>Les conteneurs autres que Selenium doivent exécuter des tests à l’aide d’un proxy HTTP basé sur les variables d’environnement dans la section [&#x200B; Test de l’interface utilisateur &#x200B;](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

Pour que les exécutions de pipeline restent efficaces, Adobe recommande de se concentrer sur les fonctionnalités clés et les principaux flux d’interaction utilisateur. Les suites de tests complètes de l’interface utilisateur qui dépassent ce niveau de qualité doivent être exécutées dans le cadre des pipelines de validation généraux du client. Intégrez-les au processus de développement du client.

Voir [exemples de tests open source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) ou le module [ui.tests de l’archétype de projets AEM](/help/implementing/cloud-manager/ui-testing.md) pour obtenir des exemples.

Pour plus d’informations, consultez [Tests personnalisés de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Audit d’expérience

Le point de contrôle qualité de l’audit de l’expérience effectue des audits [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/) par rapport à la page web du client.

Ce point de contrôle qualité est fourni par AEM prêt à l’emploi, mais ne bloque pas les pipelines de déploiement. Par défaut, un audit est effectué sur la page racine (`/`) de l’instance de publication. Vous pouvez contribuer en configurant jusqu’à 25 chemins personnalisés pris en compte pour les audits.

Voir [&#x200B; Tests de contrôle de l’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md) pour plus d’informations.

### Validations client

Le point de contrôle qualité des validations client est un espace réservé à la stratégie et aux efforts de test propres au client, exécutés avant que les modifications de l’application du client n’atteignent les pipelines de déploiement dans le cloud d’AEM.

Vous pouvez y choisir les outils et les structures de votre choix. Contrairement aux tests de fonction client et aux tests d’interface utilisateur personnalisés, il n’existe aucune limite liée à AEM as a Cloud Service. Par conséquent, Adobe vous recommande d’effectuer ici des tests fonctionnels et d’interface utilisateur à long terme.

Vous pouvez choisir n’importe quel outil et framework, mais Adobe suggère d’aligner les tests d’intégration et d’interface utilisateur HTTP sur les outils et frameworks utilisés dans les points de contrôle de qualité de test fonctionnels et d’interface utilisateur personnalisés. En outre, Adobe recommande d’incorporer [&#x200B; Environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) dans votre stratégie de test locale afin de refléter fidèlement les environnements cloud AEM.

### Test manuel

Le point de contrôle qualité des tests manuels est un espace réservé pour les clients qui effectuent des tests manuels. Étant donné que les pipelines cloud d’AEM ne prennent pas en charge les tests manuels, ils doivent être inclus dans votre stratégie de test locale.

Pour les tests manuels, il peut s’avérer utile de l’intégrer à un environnement de développement AEM Cloud Service supplémentaire.
