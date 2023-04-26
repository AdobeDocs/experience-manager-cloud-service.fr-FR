---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 7d15440159a8e24314753acd5b37fcd2c5e8ec4c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 72%

---


# Tests fonctionnels {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code."

Découvrez les trois différents types de tests fonctionnels intégrés au [processus de déploiement AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) pour garantir la qualité et la fiabilité de votre code.

## Portée

Les étapes de test fonctionnel du pipeline Cloud Manager ont pour but de s’assurer que les fonctionnalités essentielles de votre application fonctionnent comme prévu.

Cette phase de test est le dernier niveau de test automatisé avant de déployer votre code en production.

Les tests fonctionnels ne doivent pas remplacer, mais plutôt compléter et étendre d’autres stratégies de test telles que les tests d’unité, les tests d’intégration ou les tests fonctionnels effectués en dehors de l’exécution du pipeline dans Cloud Manager.

## Présentation {#overview}

Il existe trois types différents de tests fonctionnels dans AEM as a Cloud Service.

* [Tests fonctionnels du produit](#product-functional-testing)
* [Tests fonctionnels personnalisés](#custom-functional-testing)
* [Test d’interface utilisateur personnalisé](#custom-ui-testing)

Pour tous les tests fonctionnels, les résultats détaillés des tests peuvent être téléchargés en tant que fichier `.zip` en utilisant le bouton **Télécharger le journal de build** dans l’écran d’aperçu de build, dans le cadre du [processus de déploiement.](/help/implementing/cloud-manager/deploy-code.md)

Ces journaux n’incluent pas les journaux du processus d’exécution AEM. Pour accéder à ces journaux, reportez-vous au document [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) pour plus d’informations.

Les tests fonctionnels du produit et les exemples de tests fonctionnels personnalisés s’appuient sur les [Clients de test AEM.](https://github.com/adobe/aem-testing-clients)

### Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit rassemblent un ensemble de tests d’intégration HTTP (IT) stables des fonctionnalités de base d’AEM, telles que les tâches de création et de réplication. Ces tests sont gérés par Adobe et sont destinés à empêcher le déploiement de modifications du code d’application personnalisé s’il interrompt les fonctionnalités de base.

* [Pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md): Les tests fonctionnels du produit s’exécutent automatiquement chaque fois que vous déployez du nouveau code dans Cloud Manager et ne peuvent pas être ignorés.
* [Pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): Vous pouvez éventuellement sélectionner des tests fonctionnels du produit à exécuter chaque fois que vous exécutez votre pipeline hors production.

Les tests fonctionnels du produit sont conservés en tant que projet open source. Reportez-vous à la section [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub pour plus d’informations.

### Tests fonctionnels personnalisés {#custom-functional-testing}

Bien que les tests fonctionnels du produit soient définis par Adobe, vous pouvez rédiger vos propres tests de qualité pour votre propre application. Cela sera exécuté en tant que test fonctionnel personnalisé dans le cadre de la [pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ou facultatif [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) pour garantir la qualité de votre application.

Les tests fonctionnels personnalisés sont exécutés à la fois pour les déploiements de code personnalisé et les mises à niveau de notifications push, ce qui rend particulièrement cruciale la rédaction de bons tests fonctionnels qui empêchent les changements de code AEM d’enfreindre le code de votre application. L’étape des tests fonctionnels personnalisés est toujours présente et ne peut pas être ignorée.

Reportez-vous à la section [Tests fonctionnels Java](/help/implementing/cloud-manager/java-functional-testing.md) pour plus d’informations.


### Test d’interface utilisateur personnalisé {#custom-ui-testing}

Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont basés sur Selenium et placés dans une image Docker afin de permettre un large choix de langues et de cadres, tels que Java et Maven, Node et WebDriver.io, ou encore d’autres cadres et technologies basés sur Selenium.

Reportez-vous à la section [Tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) pour plus d’informations.

