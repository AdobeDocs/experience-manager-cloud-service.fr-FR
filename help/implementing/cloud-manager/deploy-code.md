---
title: Déploiement de votre code
description: Découvrez comment déployer votre code à l’aide des pipelines de Cloud Manager dans AEM as a Cloud Service.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: feee55b2d1814b14121030b2ec3c0cb286e87044
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 27%

---


# Déploiement de votre code {#deploy-your-code}

Découvrez comment déployer votre code à l’aide des pipelines de Cloud Manager dans AEM as a Cloud Service.

## Déploiement de votre code avec Cloud Manager dans AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Une fois que vous avez [configuration de votre pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) y compris le référentiel, l’environnement et l’environnement de test, vous êtes prêt à déployer votre code.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez déployer le code.

1. Cliquez sur **Déployer** de l’appel à l’action sur la **Présentation** pour lancer le processus de déploiement.

   ![CTA](assets/deploy-code1.png)

1. L’écran **Exécution du pipeline** s’affiche. Cliquez sur **Compilation** pour lancer le processus.

   ![Écran Exécution du pipeline](assets/deploy-code2.png)

Le processus de création déploie votre code en trois phases.

1. [Déploiement dans l’environnement intermédiaire](#stage-deployment)
1. [Test dans l’environnement intermédiaire](#stage-testing)
1. [Déploiement dans l’environnement de production](#production-deployment)

>[!TIP]
>
>Vous pouvez passer en revue les étapes de différents processus de déploiement en affichant les journaux ou en examinant les résultats pour les critères de test.

## Phase de déploiement dans l’environnement {#stage-deployment}

Le **Déploiement dans l’environnement** phase. implique ces étapes.

* **Validation**  - Cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles. Par exemple, le test de l’existence de la branche configurée et de la disponibilité des environnements.
* **Test de création et d’unité** - Cette étape exécute un processus de génération en conteneur.
   * Consultez le document [Détails de l’environnement de génération](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) pour plus d’informations sur l’environnement de création.
* **Analyse du code** - Cette étape évalue la qualité du code de votre application.
   * Consultez le document [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) pour plus d’informations sur le processus de test.
* **Créer des images** - Ce processus est responsable de la transformation du contenu et des packages Dispatcher générés par l’étape de création en images Docker et en configurations Kubernetes.
* **Déploiement sur l’environnement intermédiaire** - L’image est déployée dans l’environnement d’évaluation en vue de la [Phase de test d’évaluation.](#stage-testing)

![Déploiement dans l’environnement intermédiaire](assets/stage-deployment.png)

## Phase de test d’évaluation {#stage-testing}

Le **Test d’évaluation** implique ces étapes.

* **Tests fonctionnels du produit** - Le pipeline Cloud Manager exécute des tests qui s’exécutent sur l’environnement intermédiaire.
   * Reportez-vous au document [Tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) pour plus d’informations.

* **Tests fonctionnels personnalisés** - Cette étape du pipeline est toujours exécutée et ne peut pas être ignorée. Si aucun fichier JAR de test n’est généré par la version, le test est transmis par défaut.
   * Reportez-vous au document [Tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) pour plus d’informations.

* **Tests de l’interface utilisateur personnalisée** - Cette étape est une fonctionnalité facultative qui exécute automatiquement des tests d’interface utilisateur créés pour des applications personnalisées.
   * Les tests d’interface utilisateur sont des tests basés sur Selenium conditionnés dans une image Docker pour permettre un large choix de langues et de structures (comme Java et Maven, Node et WebDriver.io, ou toute autre structure et technologie reposant sur Selenium).
   * Reportez-vous au document [Tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) pour plus d’informations.

* **Audit de l’expérience** - Cette étape du pipeline est toujours exécutée et ne peut pas être ignorée. Lorsqu’un pipeline de production est exécuté, une étape de contrôle de l’expérience est incluse après les tests fonctionnels personnalisés qui exécuteront les contrôles.
   * Les pages configurées sont envoyées au service et évaluées.
   * Les résultats sont informatifs et affichent les scores et le changement entre les scores actuel et précédent.
   * Ces informations sont utiles pour déterminer si une régression sera introduite avec le déploiement actuel.
   * Reportez-vous au document [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md) pour plus d’informations.

![Test dans l’environnement intermédiaire](assets/stage-testing.png)

## Phase de déploiement en production {#deployment-production}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs d’un site AEM.

Les déploiements en production suivent généralement les mêmes étapes que précédemment décrites, mais de manière progressive.

1. Déploiement des packages AEM sur l’instance de création.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish1 et le package dispatcher sur dispatcher1. Purge du cache du dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish2 et le package dispatcher sur dispatcher2. Purge du cache du dispatcher.
1. Replacement du dispatcher2 dans l’équilibreur de charge.

Ce processus se poursuit jusqu’à ce que le déploiement ait atteint toutes les instances de publication et tous les Dispatchers dans la topologie.

![Phase de déploiement en production](assets/production-deployment.png)

## Délais d’expiration {#timeouts}

Les étapes suivantes expirent s’ils sont en attente de commentaires de l’utilisateur :

| Étape | Délai dépassé |
|--- |--- |
| Test de qualité du code | 14 jours |
| Test de sécurité | 14 jours |
| Test de performance | 14 jours |
| Application à approuver | 14 jours |
| Planning du déploiement en production | 14 jours |
| Assistance de l’ingénieur du service client | 14 jours |

## Processus de déploiement {#deployment-process}

Tous les déploiements de Cloud Service suivent un processus continu pour garantir un temps d’arrêt nul. Reportez-vous au document [Fonctionnement des déploiements en continu](/help/implementing/deploying/overview.md#how-rolling-deployments-work) pour en savoir plus.