---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 181a0fd3097e1af2c432afbd8d2a170d792918be
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 10%

---


# Présentation {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code."

En savoir plus sur les points de contrôle de qualité disponibles dans la section [AEM processus de déploiement as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md), les différents types de tests fonctionnels intégrés, comment contribuer et comment les utiliser au mieux dans le cadre d’une stratégie de test globale.

## Vue d’ensemble

Le diagramme suivant présente un aperçu général des pipelines disponibles dans le cadre d’une stratégie de test globale et de la [AEM processus de déploiement as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![Points de contrôle qualité du déploiement AEM Cloud Service](assets/functional-testing/quality-gates-compact.svg)

## Objectif

Les pipelines de déploiement d’AEM Cloud Service ont pour objectif de faciliter des déploiements robustes et sécurisés à différentes étapes de votre développement et d’AEM cycle de vie des versions du produit. Ces pipelines intègrent plusieurs points de contrôle de qualité à différents niveaux afin de garantir l’intégrité et la sécurité des déploiements pour vos modifications d’applications AEM et pour AEM mises à jour de produits.

Adobe fournit plusieurs points de contrôle qualité intégrés, tandis que d’autres nécessitent votre intervention pour la mise en oeuvre et la configuration. Ces points de contrôle de qualité sont polyvalents, certains étant applicables à différentes étapes du cycle de vie et même intégrables à votre propre configuration de développement et à vos propres processus CI/CD.

Les points de contrôle qualité intégrés valident principalement les fonctionnalités du produit AEM dans le contexte de votre application AEM. En revanche, les points de contrôle de qualité personnalisés que vous configurez sont conçus pour vérifier que les fonctionnalités critiques de votre application et les interactions utilisateur fonctionnent comme prévu. Collectivement, ces deux ensembles de points de contrôle de qualité fonctionnent ensemble pour garantir des déploiements automatisés robustes et sécurisés pour vos modifications de code et pour AEM mises à jour de produit.

Il est important de noter que ces points de contrôle qualité ne sont pas destinés à constituer un cadre de test complet pour l’ensemble de votre stratégie de test. Le produit AEM est soumis à des tests approfondis avant d’entrer dans le processus de déploiement du service cloud AEM. De même, votre application doit déjà être de haute qualité avant d’atteindre la phase de déploiement. Cette approche permet de s’assurer que les points de contrôle de qualité se concentrent sur leur principal objectif de protection du processus de déploiement, plutôt que de se substituer à un régime de test complet.

## Points de contrôle de qualité

Le diagramme suivant présente une vue détaillée des points de contrôle de qualité disponibles et de leur utilisation dans la stratégie de test globale et la [AEM processus de déploiement as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md).

![Points de contrôle qualité du déploiement AEM Cloud Service](assets/functional-testing/quality-gates-overview.svg)

### Points de contrôle de qualité fournis par le client

|                               | Tests unitaires | Personnalisé<br/> Tests fonctionnels | Personnalisé<br/> Tests de l’interface utilisateur | Client<br/> Validations | Manuel<br/> Tests |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Pipeline de production** | Oui<br/>Blocage<br/> | Oui<br/>Blocage<br/>Délai d’expiration de 60 m | Oui<br/>Blocage<br/>Délai d’expiration de 60 m | Non | Non |
| **Pipeline hors production** | Oui<br/>Blocage<br/> | Opt-in<br/>Blocage<br/>Délai d’expiration de 60 m | Opt-in<br/>Blocage<br/>Délai d’expiration de 60 m | Non | Non |
| **Validation interne de l’Adobe** | Oui<br/>Blocage<br/> | Oui<br/>Blocage<br/>Délai d’expiration de 60 m | Oui<br/>Blocage<br/>Délai d’expiration de 60 m | Non | Non |
| **Client CI/CD** | Oui | Oui | Oui | Oui | Oui |
| **Développeur local du client** | Oui | Oui | Oui | Oui | Oui |

### Test unitaire

Nous vous recommandons de fournir les tests unitaires pour votre application AEM, qui constituent la base de chaque stratégie de test. Ils sont conçus pour fonctionner rapidement et souvent et donner des retours rapides et précoces. Ils sont étroitement intégrés aux workflows des développeurs, à vos propres CI/CD et aux pipelines de déploiement du service cloud d’AEM.

Ils sont implémentés à l’aide de JUnit et exécutés avec Maven. Reportez-vous à
[Module principal de l’archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/core.html#unit-tests)
pour un exemple de test unitaire pour AEM et prise en main.

### Qualité du code

Ce point de contrôle qualité est configuré prêt à l’emploi et exécute une analyse de code statique sur votre code d’application AEM.

Voir [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) et
[Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour plus d’informations.

### Tests de produit

Les tests fonctionnels du produit rassemblent un ensemble de tests d’intégration HTTP (IT) stables des fonctionnalités de base d’AEM, telles que les tâches de création et de réplication. Adobe les fournit et les conserve prêts à l’emploi. Elles sont destinées à empêcher le déploiement des modifications apportées au code d’application personnalisé si celui-ci rompt les fonctionnalités de base du produit AEM.

Ils sont implémentés à l’aide de Junit, sont exécutés à l’aide de Maven et utilisent les [AEM des clients de test](https://github.com/adobe/aem-testing-clients).
La suite de tests de produit est conservée sous la forme d’une [projet open source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke), suit les bonnes pratiques et peut être considéré comme un bon point de départ pour la mise en oeuvre de vos tests.

### Tests fonctionnels personnalisés

Comme les tests de produit, les tests fonctionnels du client sont des tests d’intégration HTTP (IT) et sont bien implémentés à l’aide de Junit, sont exécutés à l’aide de Maven et conçus sur la base des tests officiels. [AEM des clients de test](https://github.com/adobe/aem-testing-clients).

>[!NOTE]
>
>Les tests fonctionnels personnalisés sont exécutés dans les pipelines de production et de non-production (opt-in), qui sont utilisés par les déploiements de modifications d’application AEM et AEM les mises à jour push de produit. Ils constituent donc une contribution essentielle au bon fonctionnement de votre application et à l’augmentation de la sécurité des versions.
>Les tests fonctionnels du client sont également exécutés dans des pipelines internes de validation de version préliminaire pour chaque client, ce qui permet de fournir des commentaires anticipés.

Afin de préserver l’efficacité des exécutions de pipeline, nous vous recommandons de vous concentrer sur les fonctionnalités clés et les principaux flux d’interaction utilisateur.
Un temps d’exécution de ~15 minutes ou moins pour les tests fonctionnels est recommandé. Les suites de tests fonctionnels complètes qui ne correspondent pas à ce point de contrôle qualité sont recommandées pour être exécutées dans le cadre des pipelines de validation des clients généraux pendant le flux de développement du client.

Reportez-vous à [tests de produits Open Source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) ou le
[Module it.tests de l’archétype des projets AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/ittests.html)
pour obtenir des exemples.

Pour plus d’informations, consultez [Tests fonctionnels Java](/help/implementing/cloud-manager/java-functional-testing.md).

### Tests de l’interface utilisateur personnalisée

Pour optimiser le contrôle des risques pour votre développement spécifique au client, Adobe vous encourage vivement à capturer des tests d’interface utilisateur critiques dans AEM CS. Elles sont destinées à être limitées en nombre, mais avec le plus grand impact sur votre expérience client.

Les tests sont conditionnés dans une image Docker, conçue pour être aussi volatile que possible (avec prise en charge de Cypress, Selenium, Java, Javascript, etc.). Ils suivent les mêmes caractéristiques et objectifs que les tests fonctionnels personnalisés.

>[!NOTE]
>
>Les tests d’interface utilisateur personnalisés sont exécutés dans les pipelines de production et de non-production (opt-in), qui sont utilisés par vos déploiements de modifications d’application AEM et AEM les mises à jour push de produit. Ils constituent donc une contribution essentielle au bon fonctionnement de votre application et à l’augmentation de la sécurité des versions.
>Les tests de l’interface utilisateur client sont également exécutés dans des pipelines internes de validation de version préliminaire pour chaque client, ce qui permet de fournir des commentaires anticipés.

Afin de préserver l’efficacité des exécutions de pipeline, nous vous recommandons de vous concentrer sur les fonctionnalités clés et les principaux flux d’interaction utilisateur.
Il est recommandé d’exécuter les suites de tests d’interface utilisateur complètes qui ne correspondent pas à ce point de contrôle qualité dans le cadre des pipelines de validation client généraux au cours du flux de développement du client.

Reportez-vous à [exemples de tests open-source](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) ou le
[Module ui.tests de l’archétype des projets AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uitests.html)
pour obtenir des exemples.

Pour plus d’informations, consultez [Tests personnalisés de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Contrôle de l’expérience

Le point de contrôle de la qualité de l’expérience est performant [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/)
audits sur la page web du client.

Ce point de contrôle qualité est fourni par AEM prêt à l’emploi, mais ne bloque pas les pipelines de déploiement. Par défaut, un audit par rapport à la page racine (`/`) de l’instance de publication. Vous pouvez contribuer en configurant jusqu’à 25 chemins personnalisés pris en compte pour les audits.

Voir [Tests de contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)
pour plus d’informations.

### Validation des clients

Le point de contrôle qualité des validations client est un espace réservé à la stratégie et aux efforts de test du client, exécuté avant que les modifications de l’application du client n’atteignent les pipelines de déploiement cloud AEM.

Ici, vous pouvez, bien sûr, choisir les outils et structures que vous préférez. Contrairement aux tests de fonction client et aux tests d’interface utilisateur personnalisés, il n’existe aucune limite as a Cloud Service, et nous vous recommandons donc d’effectuer ici des tests fonctionnels et d’interface utilisateur à long terme.

Bien que vous soyez libre de choisir n’importe quel outil et structure, nous vous recommandons d’aligner les tests d’intégration HTTP et les tests d’interface utilisateur avec les outils et les structures disponibles dans les tests fonctionnels personnalisés et les points de contrôle de qualité de l’interface utilisateur personnalisée.
Nous recommandons d’intégrer
[Environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)
dans votre stratégie de test locale pour tester le plus près possible des environnements cloud AEM.

### Test manuel

Le point de contrôle qualité des tests manuels est un espace réservé pour les clients qui effectuent des tests manuels. AEM pipelines de cloud ne prennent pas en charge les tests manuels. Par conséquent, cela doit se produire dans le cadre de votre propre stratégie de test locale.

Pour les tests manuels, il peut s’avérer utile de l’intégrer à un environnement de développement AEM Cloud Service supplémentaire.
