---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 100%

---


# Tests fonctionnels {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement AEM as a Cloud Service pour garantir la qualité et la fiabilité de votre code."

Découvrez les trois différents types de tests fonctionnels intégrés au [processus de déploiement AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) pour garantir la qualité et la fiabilité de votre code.

## Portée

Les étapes de test fonctionnel du pipeline Cloud Manager ont pour but de s’assurer que les fonctionnalités essentielles de votre application fonctionnent comme prévu.

Cette phase de test est le dernier niveau de test automatisé avant de déployer votre code en production.

Les tests fonctionnels ne doivent pas remplacer, mais plutôt compléter et étendre d’autres stratégies de test telles que les tests unitaires,
les tests d’intégration ou les tests fonctionnels effectués en dehors de l’exécution du pipeline dans Cloud Manager.

## Vue d’ensemble {#overview}

Il existe trois types différents de tests fonctionnels dans AEM as a Cloud Service.

* [Tests fonctionnels du produit](#product-functional-testing)
* [Tests fonctionnels personnalisés](#custom-functional-testing)
* [Test d’interface utilisateur personnalisé](#custom-ui-testing)

Pour tous les tests fonctionnels, les résultats détaillés des tests peuvent être téléchargés en tant que fichier `.zip` en utilisant le bouton **Télécharger le journal de build** dans l’écran d’aperçu de build, dans le cadre du [processus de déploiement](/help/implementing/cloud-manager/deploy-code.md).

Ces journaux n’incluent pas les journaux du processus d’exécution AEM. Pour accéder à ces journaux, voir [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) pour plus d’informations.

Les tests fonctionnels du produit et les exemples de tests fonctionnels personnalisés s’appuient sur les [Clients de test AEM.](https://github.com/adobe/aem-testing-clients)

### Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit rassemblent un ensemble de tests d’intégration HTTP (IT) stables des fonctionnalités de base d’AEM, telles que les tâches de création et de réplication. Ces tests sont gérés par Adobe et sont destinés à empêcher le déploiement de modifications du code d’application personnalisé s’il interrompt les fonctionnalités de base.

* [Pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) : les tests fonctionnels de produit s’exécutent automatiquement lorsque vous déployez un nouveau code dans Cloud Manager et vous ne pouvez pas les ignorer.
* [Pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) : vous pouvez éventuellement sélectionner des tests fonctionnels de produit qui s’exécutent chaque fois que vous exécutez votre pipeline hors production.

Les tests fonctionnels du produit sont conservés en tant que projet open source. Pour plus d’informations, consultez [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub.

### Tests fonctionnels personnalisés {#custom-functional-testing}

Bien que les tests fonctionnels du produit soient définis par Adobe, vous pouvez rédiger vos propres tests de qualité pour votre propre application. Cela est exécuté en tant que test fonctionnel personnalisé dans le cadre du [pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ou éventuellement du [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) pour garantir la qualité de votre application.

Les tests fonctionnels personnalisés sont exécutés à la fois pour les déploiements de code personnalisé et les mises à niveau de notifications push, ce qui rend particulièrement cruciale la rédaction de bons tests fonctionnels qui empêchent les changements de code AEM d’enfreindre le code de votre application. L’étape des tests fonctionnels personnalisés est toujours présente et ne peut pas être ignorée.

Pour plus d’informations, consultez [Tests fonctionnels Java](/help/implementing/cloud-manager/java-functional-testing.md).


### Test d’interface utilisateur personnalisé {#custom-ui-testing}

Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont basés sur Selenium et placés dans une image Docker pour permettre un large choix de langues et de cadres, tels que Java et Maven, Node et WebDriver.io, ou encore d’autres cadres et technologies basés sur Selenium.

Pour plus d’informations, consultez [Tests personnalisés de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

