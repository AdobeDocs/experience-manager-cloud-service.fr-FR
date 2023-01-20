---
title: Déploiement de votre code
description: Découvrez comment déployer votre code à l’aide des pipelines de Cloud Manager dans AEM as a Cloud Service.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: 14395cf97b23896e929e215e7e0b9e33620637eb
workflow-type: ht
source-wordcount: '1221'
ht-degree: 100%

---


# Déploiement de votre code {#deploy-your-code}

Découvrez comment déployer votre code vers la Production à l’aide des pipelines Cloud Manager dans AEM as a Cloud Service.

![Diagramme de pipeline de production](./assets/configure-pipeline/production-pipeline-diagram.png)

Le déploiement du code de manière transparente sur l’environnement d’évaluation, puis jusqu’à la production, est effectué via un pipeline de production. L’exécution du pipeline de production est divisée en deux phases logiques.

1. Déploiement dans un environnement d’évaluation
   * Le code est créé et déployé dans l’environnement d’évaluation pour les tests fonctionnels automatisés, les tests de l’interface utilisateur, le contrôle de l’expérience et les tests d’acceptation utilisateur (UAT).
1. Déploiement dans un environnement de production
   * Une fois que la version est validée à l’étape d’évaluation et approuvée pour le passage en production, le même artefact de build est déployé dans l’environnement de production.

_Seul le type de pipeline Code full stack prend en charge l’analyse de code, les tests de fonction, les tests d’interface utilisateur et le contrôle de l’expérience._

## Déploiement de code avec Cloud Manager dans AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Une fois que vous avez [configuré votre pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md), y compris le référentiel, l’environnement et l’environnement de test, vous êtes prêt à déployer votre code.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez déployer du code.

1. Cliquez sur **Déployer** dans l’appel à l’action de l’écran **Présentation** pour lancer le processus de déploiement.

   ![CTA](assets/deploy-code1.png)

1. L’écran **Exécution du pipeline** s’affiche. Cliquez sur **Générer** pour lancer le processus.

   ![Écran Exécution du pipeline](assets/deploy-code2.png)

Le processus de build déploie votre code en trois phases.

1. [Déploiement dans l’environnement d’évaluation](#stage-deployment)
1. [Test dans l’environnement intermédiaire](#stage-testing)
1. [Déploiement dans l’environnement de production](#production-deployment)

>[!TIP]
>
>Vous pouvez examiner les étapes de divers processus de déploiement en affichant les journaux ou en examinant les résultats pour les critères de test.

## Phase de déploiement dans l’environnement {#stage-deployment}

La phase de **Déploiement dans l’environnement** comprend ces étapes.

* **Validation** - Cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles, par exemple, en s’assurant de l’existence de la branche configurée et de la disponibilité des environnements.
* **Test unitaire et version** - Cette étape exécute un processus de création en conteneur.
   * Consultez le document [Détails d’environnement de génération](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) pour plus d’informations sur l’environnement de génération.
* **Analyse du code** - Cette étape évalue la qualité du code de votre application.
   * Consultez le document [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) pour plus d’informations sur le processus de test.
* **Images de build** - Ce processus est responsable de la transformation du contenu et des modules du Dispatcher générés par l’étape de build en images Docker et en configuration Kubernetes.
* **Déploiement sur l’environnement d’évaluation** - L’image est déployée dans l’environnement d’évaluation en vue de la [phase de test d’évaluation.](#stage-testing)

![Déploiement dans l’environnement d’évaluation](assets/stage-deployment.png)

## Phase de test d’évaluation {#stage-testing}

La phase de **test d’évaluation** comprend ces étapes.

* **Tests fonctionnels du produit** - Le pipeline Cloud Manager exécute des tests qui s’exécutent sur l’environnement d’évaluation.
   * Reportez-vous au document [Tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) pour plus d’informations.

* **Tests fonctionnels personnalisés** - Cette étape du pipeline est toujours exécutée et ne peut pas être ignorée. Cependant, si aucun fichier JAR de test n’est généré par le build, le test réussit par défaut.
   * Reportez-vous au document [Tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) pour plus d’informations.

* **Test d’interface utilisateur personnalisé** - Cette étape est une fonctionnalité facultative qui exécute automatiquement des tests d’interface utilisateur créés pour des applications personnalisées.
   * Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker pour permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basés sur Selenium).
   * Reportez-vous au document [Test d’interface utilisateur personnalisé](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) pour plus d’informations.

* **Contrôle de l’expérience** - Cette étape du pipeline est toujours exécutée et ne peut pas être ignorée. Lorsqu’un pipeline de production est exécuté, une étape de contrôle de l’expérience est incluse après les tests fonctionnels personnalisés qui exécuteront les contrôles.
   * Les pages configurées sont envoyées au service et évaluées.
   * Les résultats sont informatifs et affichent les scores et le changement entre les scores actuels et précédents.
   * Ces informations sont utiles pour déterminer si une régression sera introduite avec le déploiement actuel.
   * Pour plus d’informations, consultez la section [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

![Test dans l’environnement d’évaluation](assets/stage-testing.png)

## Phase de déploiement en production {#deployment-production}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs d’un site AEM.

Les déploiements en production suivent généralement les mêmes étapes décrites précédemment, mais par roulements.

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

Tous les déploiements de Cloud Service suivent un processus continu pour garantir un temps d’arrêt nul. Reportez-vous au document [Fonctionnement des déploiements par roulement](/help/implementing/deploying/overview.md#how-rolling-deployments-work) pour en savoir plus.

>[!NOTE]
>
>Le cache du Dispatcher est effacé à chaque déploiement. Il est ensuite préchauffé avant que les nouveaux nœuds de publication n’acceptent le trafic.

## Réexécution d’un déploiement en production {#Reexecute-Deployment}

La réexécution de l’étape de déploiement en production est prise en charge pour les exécutions où l’étape de déploiement en production est terminée. Le statut de cet d’achèvement n’est pas important : le déploiement peut avoir été annulé ou être impossible. Cela dit, le cas d’utilisation principal devrait correspondre à un cas où l’étape de déploiement en production a échoué pour des raisons transitoires. La réexécution crée une nouvelle exécution à l’aide du même pipeline. Cette nouvelle exécution se compose de trois étapes :

1. L’étape de validation : il s’agit essentiellement de la même validation qui se produit lors de l’exécution normale d’un pipeline.
1. L’étape de création : dans le contexte d’une réexécution, l’étape de création consiste à copier des artefacts, sans réellement exécuter un nouveau processus de création.
1. L’étape de déploiement en production : utilise la même configuration et les mêmes options que l’étape de déploiement en production dans une exécution normale de pipeline.

L’étape de création peut être légèrement étiquetée différemment dans l’interface utilisateur afin de refléter le fait qu’elle copie des artefacts, sans réelle re-création.

![Redéploiement](assets/Re-deploy.png)

Restrictions :

* La réexécution de l’étape de déploiement en production n’est disponible que lors de la dernière exécution.
* La réexécution n’est pas disponible pour les exécutions de mise à jour push. Si la dernière exécution est une exécution de mise à jour push, la réexécution n’est pas possible.
* Si la dernière exécution est une exécution de mise à jour push, la réexécution n’est pas possible.
* Si la dernière exécution a échoué à un moment donné avant l’étape de déploiement en production, la réexécution n’est pas possible.

### Réexécution de l’API {#Reexecute-API}

### Identification d’une exécution de type réexécution

Pour déterminer si une exécution est une réexécution, vous pouvez examiner le champ déclencheur. Sa valeur sera alors *RE_EXECUTE*.

### Déclenchement d’une nouvelle exécution

Pour déclencher une réexécution, une demande de PUT doit être envoyée au lien HAL &lt;(<https://ns.adobe.com/adobecloud/rel/pipeline/reExecute>)> au moment de l’étape de déploiement en production. Si ce lien est présent, l’exécution peut être redémarrée à partir de cette étape. En cas d’absence, l’exécution ne peut pas être redémarrée à partir de cette étape. Dans la version initiale, ce lien ne sera jamais présent que lors de l’étape de déploiement en production, mais les prochaines versions peuvent prendre en charge le démarrage du pipeline à partir d’autres étapes. Exemple :

```Javascript
 {
  "_links": {
    "https://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
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


La syntaxe de la valeur _href_ du lien HAL ci-dessus n’est pas destinée à être utilisée comme point de référence. La valeur réelle doit toujours être lue à partir du lien HAL, et non générée.

L’envoi d’une requête *PUT* vers ce point d’entrée entraîne la génération d’une réponse *201* en cas de réussite, le corps de la réponse est la représentation de la nouvelle exécution. Cela revient à lancer une exécution régulière via l’API.
