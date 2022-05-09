---
title: Déploiement de votre code
description: Découvrez comment déployer votre code à l’aide des pipelines de Cloud Manager dans AEM as a Cloud Service.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: c6e930f62cc5039e11f2067ea31882c72be18774
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 16%

---


# Déploiement de votre code {#deploy-your-code}

Découvrez comment déployer votre code vers Production à l’aide des pipelines Cloud Manager dans AEM as a Cloud Service.

![Diagramme de pipeline de production](./assets/configure-pipeline/production-pipeline-diagram.png)

Le déploiement du code de manière transparente sur l’environnement intermédiaire, puis jusqu’à la production, est effectué via un pipeline de production. L’exécution du pipeline de production est divisée en deux phases logiques.

1. Déploiement dans un environnement d’évaluation
   * Le code est créé et déployé dans l’environnement d’évaluation pour les tests fonctionnels automatisés, les tests de l’interface utilisateur, le contrôle de l’expérience et les tests d’acceptation utilisateur (UAT).
1. Déploiement dans l’environnement de production
   * Une fois que la version est validée à l’étape de l’évaluation et approuvée pour la promotion en production, le même artefact de version est déployé dans l’environnement de production.

_Seul le type de pipeline Full Stack Code prend en charge l’analyse de code, les tests de fonction, les tests d’interface utilisateur et l’audit d’expérience._

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

## Réexécution d’un déploiement en production {#Reexecute-Deployment}

La réexécution de l’étape de déploiement en production est prise en charge pour les exécutions où l’étape de déploiement en production est terminée. Le type d’achèvement n’est pas important : le déploiement peut être annulé ou impossible. Cela dit, le cas d’utilisation Principal doit être celui où l’étape de déploiement en production a échoué pour des raisons transitoires. La réexécution crée une nouvelle exécution à l’aide du même pipeline. Cette nouvelle exécution se compose de trois étapes :

1. L’étape de validation : il s’agit essentiellement de la même validation qui se produit lors de l’exécution normale d’un pipeline.
1. L’étape de création : dans le contexte d’une réexécution, l’étape de création consiste à copier des artefacts, sans réellement exécuter un nouveau processus de création.
1. L’étape de déploiement en production : utilise la même configuration et les mêmes options que l’étape de déploiement en production dans une exécution normale de pipeline.

L’étape de création peut être légèrement étiquetée différemment dans l’interface utilisateur afin de refléter le fait qu’elle copie des artefacts, et non la reconstruction.

![Redéployer](assets/Re-deploy.png)

Restrictions :

* La réexécution de l’étape de déploiement en production n’est disponible que lors de la dernière exécution.
* La réexécution n’est pas disponible pour les exécutions de mise à jour push. Si la dernière exécution est une exécution de mise à jour push, la réexécution n’est pas possible.
* Si la dernière exécution est une exécution de mise à jour push, la réexécution n’est pas possible.
* Si la dernière exécution a échoué à un moment donné avant l’étape de déploiement en production, la réexécution n’est pas possible.

### Réexécuter l’API {#Reexecute-API}

### Identifier une exécution de réexécution

Pour déterminer si une exécution est une exécution de nouvelle exécution, le champ déclencheur peut être examiné. Sa valeur sera *RE_EXECUTE*.

### Déclenchement d&#39;une nouvelle exécution

Pour déclencher une réexécution, une demande de PUT doit être envoyée au lien HAL &lt;(<http://ns.adobe.com/adobecloud/rel/pipeline/reExecute>)> à l’état de l’étape de déploiement en production. Si ce lien est présent, l&#39;exécution peut être redémarrée à partir de cette étape. En cas d’absence, l’exécution ne peut pas être redémarrée à partir de cette étape. Dans la version initiale, ce lien ne sera jamais présent que lors de l’étape de déploiement en production, mais les prochaines versions peuvent prendre en charge le démarrage du pipeline à partir d’autres étapes. Exemple :

```Javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```


Syntaxe du lien HAL _href_  La valeur ci-dessus n’est pas destinée à être utilisée comme point de référence. La valeur réelle doit toujours être lue à partir du lien HAL et non générée.

Envoi d’un *PUT* une requête vers ce point de terminaison entraîne la génération d’une *201* en cas de réussite, le corps de la réponse est la représentation de la nouvelle exécution. Cela revient à lancer une exécution régulière via l’API.
