---
title: Déploiement de votre code - Cloud Services
description: Déploiement de votre code - Cloud Services
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: 64023bbdccd8d173b15e3984d0af5bb59a2c1447
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 93%

---

# Déploiement de votre code {#deploy-your-code}

## Déploiement du code avec Cloud Manager dans AEM en tant que Cloud Service {#deploying-code-with-cloud-manager}

Une fois que vous avez configuré votre pipeline de production (référentiel, environnement et environnement de test), vous êtes prêt à déployer votre code.

1. Cliquez sur **Déployer** dans Cloud Manager pour lancer le processus de déploiement.

   ![](assets/deploy-code1.png)


1. L’écran **Exécution du pipeline** s’affiche.

   Cliquez sur **Générer** pour lancer le processus.

   ![](assets/deploy-code2.png)

1. Le processus de création complet déploie le code.

   Les étapes suivantes sont impliquées dans le processus de création :

   1. Déploiement dans l’environnement intermédiaire
   1. Test dans l’environnement intermédiaire
   1. Déploiement dans l’environnement de production

   >[!NOTE]
   >
   >En outre, vous pouvez examiner les étapes de divers processus de déploiement en affichant les journaux ou en examinant les résultats pour les critères de test.

   Le **déploiement en environnement intermédiaire** comprend les étapes suivantes :

   * Validation : cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles ; par exemple, la branche configurée existe, les environnements sont disponibles, etc.
   * Test de création et d’unité : cette étape exécute un processus de création en conteneur. Voir [Détails d’environnement de génération](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md) pour plus d’informations sur l’environnement de génération.
   * Analyse du code : cette étape évalue la qualité du code de votre application. Voir [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) pour plus d’informations sur le processus de test.
   * Compiler des images : cette étape comprend un fichier journal du processus utilisé pour compiler des images. Ce processus est responsable de la transformation du contenu et des modules du Dispatcher générés par l’étape de compilation en images Docker et en configuration Kubernetes.
   * Déploiement dans l’environnement d’évaluation.

      ![](assets/stage-deployment.png)
   Le **test dans l’environnement intermédiaire** comprend les étapes suivantes :

   * **Tests fonctionnels du produit** : les exécutions du pipeline Cloud Manager prennent en charge l’exécution de tests dans l’environnement d’évaluation.
Pour plus d’informations, voir [Tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing).

   * **Tests fonctionnels personnalisés** : cette étape du pipeline est toujours présente et ne peut pas être ignorée. Cependant, si aucun fichier JAR de test n’est généré par la compilation, le test réussit par défaut.\
      Pour plus d’informations, voir [Tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing).

   * **Tests d’interface utilisateur personnalisés** : cette étape est une fonctionnalité facultative qui permet à nos clients de créer et d’exécuter automatiquement des tests d’interface utilisateur pour leurs applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium).
Pour plus d’informations, consultez [Tests d’interface utilisateur personnalisés](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/functional-testing.html?lang=fr#using-cloud-manager).


   * **Audit de l’expérience** : cette étape du pipeline est toujours présente et ne peut pas être ignorée. Lorsqu’un pipeline de production est exécuté, une étape de contrôle de l’expérience est incluse après les tests fonctionnels personnalisés qui exécuteront les contrôles. Les pages configurées sont envoyées au service et évaluées. Les résultats sont informatifs et permettent à l’utilisateur de voir les scores et les différences existant entre les scores précédents et actuels. Ces connaissances sont utiles pour déterminer si une régression sera introduite avec le déploiement actuel.
Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

      ![](assets/stage-testing.png)





## Processus de déploiement {#deployment-process}

Tous les déploiements de Cloud Service suivent un processus continu pour garantir un temps d’arrêt nul. Pour en savoir plus, voir [Fonctionnement des déploiements en continu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#how-rolling-deployments-work) .

### Phase de déploiement en production {#deployment-production-phase}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs d’AEM Site.

Les déploiements en production suivent généralement les mêmes étapes que ci-dessus, mais par roulements :

1. Déploiement des packages AEM sur author.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish1 et le package dispatcher sur dispatcher1. Purge du cache du dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish2 et le package dispatcher sur dispatcher2. Purge du cache du dispatcher.
1. Replacement du dispatcher2 dans l’équilibreur de charge.
Ce processus se poursuit jusqu’à ce que le déploiement ait atteint toutes les instances de publication et tous les Dispatchers dans la topologie.
