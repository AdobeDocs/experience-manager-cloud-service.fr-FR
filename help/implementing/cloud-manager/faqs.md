---
title: Questions fréquentes relatives à Cloud Manager
description: Trouvez des réponses aux questions les plus fréquentes sur Cloud Manager dans AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 498a58c89910f41e6b86c5429629ec9282028987
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 81%

---


# FAQ relatives à Cloud Manager {#cloud-manager-faqs}

Ce document répond aux questions les plus fréquentes sur Cloud Manager dans AEM as a Cloud Service.

## Est-il possible d’utiliser Java™ 11 avec les versions de Cloud Manager ? {#java-11-cloud-manager}

Oui. Ajoutez `maven-toolchains-plugin` avec les paramètres appropriés pour Java™ 11.

Le processus est documenté - voir la section [Assistant de création de projet](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).

Par exemple, consultez l’exemple de code de projet [lWKND](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Ma version échoue et affiche une erreur concernant maven-scr-plugin, après le passage de Java™ 8 à Java™ 11. Que puis-je faire ? {#build-fails-maven-scr-plugin}

Votre version d’AEM Cloud Manager peut échouer lorsque vous tentez de passer de Java™ 8 à 11. Si vous rencontrez l’erreur ci-dessous, vous devez supprimer `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 > [Help 1]
```

Pour plus d’informations sur la façon de supprimer ce plug-in, voir la section [Des annotations SCR aux annotations OSGI](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Ma version échoue et affiche une erreur concernant RequireJavaVersion, après le passage de Java™ 8 à Java™ 11. Que puis-je faire ? {#build-fails-requirejavaversion}

Pour les builds Cloud Manager, le `maven-enforcer-plugin` peut échouer avec cette erreur.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

Cette erreur est un problème connu en raison duquel Cloud Manager utilise une autre version de Java™ pour exécuter la commande Maven au lieu de compiler le code. Omettez simplement `requireJavaVersion` de vos configurations `maven-enforcer-plugin`.

## La vérification de la qualité du code a échoué et le déploiement est bloqué. Y a-t-il un moyen de contourner cette vérification ? {#deployment-stuck}

Oui. Tous les échecs de vérification de la qualité du code, à l’exception de la cote de sécurité, ne sont pas des mesures critiques. Par conséquent, ils peuvent être contournés dans le cadre d’un pipeline de déploiement en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur ayant un rôle [Responsable de déploiement, Responsable de projet ou Propriétaire de l’entreprise](/help/onboarding/aem-cs-team-product-profiles.md#cloud-manager-product-profiles) peut contourner les problèmes. Dans ce cas, le pipeline continue ou ils peuvent accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.

Voir les documents [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md#three-tiered-gate) et [Configurer des pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#non-production-pipelines) pour plus d’informations.

## Puis-je utiliser SNAPSHOT pour la version du projet Maven ? {#use-snapshot}

Oui. Pour les déploiements de développeurs, les fichiers `pom.xml` de la branche Git doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`.

Cette valeur permet d’installer les déploiements suivants quand la version n’a pas été modifiée. Pour les déploiements de développeurs, aucune version automatique n’est ajoutée ou générée pour la build maven.

Vous pouvez également définir la version sur `-SNAPSHOT` pour les builds ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée pour vous une balise dans git. Cette balise peut être référencée ultérieurement, le cas échéant.

Pour plus d’informations sur la gestion des versions, voir [ Gestion des versions de projet Maven ](/help/implementing/cloud-manager/managing-code/project-version-handling.md).

## Comment le contrôle de version des packages et des lots fonctionne-t-il pour les déploiements d’évaluation et de production ? {#snapshot-version}

En cas de déploiements d’évaluation et de production, une version automatique est générée - voir la section [Gestion des versions du projet Maven](/help/implementing/cloud-manager/managing-code/project-version-handling.md).

Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven en trois parties, telle que `1.0.0`. Passez à la version supérieure à chaque déploiement en production.

Cloud Manager ajoute automatiquement sa version aux builds d’évaluation et de production et crée même une branche Git. Aucune configuration spécifique n’est nécessaire. Si vous ne définissez pas de version Maven comme décrit précédemment, le déploiement s’effectue quand même et une version est automatiquement définie.

## Ma build Maven échoue lors des déploiements de Cloud Manager, mais elle est pourtant créée localement sans la moindre erreur. Qu’est-ce qui ne va pas ? {#maven-build-fail}

Consultez cette [ressource git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus d’informations.

## Que faire si le déploiement de Cloud Manager échoue lors de l’étape de déploiement dans AEM as a Cloud Service ? {#cloud-manager-deployment-cloud-service}

La raison la plus courante de l’échec des déploiements résulte d’autorisations insuffisantes pour l’utilisateur `sling-distribution-importer`. Dans ce cas, l’étape de déploiement échoue lors d’un déploiement de Cloud Manager et des erreurs telles que les suivantes sont générées.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

L’utilisateur ou l’utilisatrice `sling-distribution-importer` a besoin d’autorisations supplémentaires pour les chemins de contenu définis dans `ui.content package`. Cette règle signifie généralement qu’il faut ajouter des autorisations pour `/conf` et `/var`.

La solution consiste à ajouter un script de [configuration RepositoryInitializer OSGi](/help/implementing/deploying/overview.md#repoint) à votre package de déploiement d’applications afin d’ajouter des listes de contrôle d’accès pour l’utilisateur `sling-distribution-importer`.

Dans l’exemple d’erreur précédent, le package `myapp-base.ui.content-*.zip` inclut le contenu situé sous `/conf` et `/var/workflow`. Pour que le déploiement réussisse, les autorisations pour `sling-distribution-importer` sous ces chemins d’accès sont nécessaires.

Voici un exemple [`org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config`](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) de configuration OSGi qui permet d’ajouter des autorisations supplémentaires pour l’utilisateur ou l’utilisatrice `sling-distribution-importer`. Cette configuration ajoute des autorisations sous `/var`. Une telle configuration doit être ajoutée au package d’application sous `/apps/myapp/config` (où `myapp` correspond au dossier dans lequel le code de votre application est stocké).

## Mon déploiement de Cloud Manager échoue à l’étape de déploiement dans AEM as a Cloud Service et j’ai déjà ajouté une configuration OSGi RepositoryInitializer. Que puis-je faire d’autre ? {#build-failures}

Si l’[ajout d’une configuration OSGi RepositoryInitializer](#cloud-manager-deployment-cloud-service) n’a pas résolu l’erreur, elle peut être due à l’un des autres problèmes suivants.

* Le déploiement peut échouer en raison d’une mauvaise configuration OSGi qui rompt un service prêt à l’emploi.
   * Vérifiez les journaux pendant le déploiement pour voir s’il existe des erreurs évidentes.

* Le déploiement peut échouer en raison de configurations incorrectes du Dispatcher ou d’Apache.
   * Veillez à tester Apache et le Dispatcher localement à l’aide de l’image Docker incluse dans le SDK.
   * Voir la section [Dispatcher en mode cloud](/help/implementing/dispatcher/disp-overview.md#content-delivery) pour savoir comment configurer le conteneur Docker du Dispatcher pour des tests locaux faciles.

* Le déploiement peut échouer en raison d’une autre défaillance lors de la réplication des modules de contenu (distribution Sling) entre les instances d’auteur et de publication.
   * Suivez ces étapes pour simuler le problème sur une configuration locale.
      1. Installez localement une instance de création et une instance de publication à l’aide des derniers fichiers jar AEM SDK.
      1. Connectez-vous à l’instance de création.
      1. Accédez à **Outils** -> **Déploiement** -> **Distribution**.
      1. Distribuez les modules de contenu faisant partie de la base de code et vérifiez si la file d’attente est bloquée avec une erreur.

## Je ne parviens pas à définir une variable à l’aide d’une commande aio. Que puis-je faire ? {#set-variable}

Il se peut que vous receviez une erreur `403` de ce type lorsque vous tentez de répertorier ou de définir les variables de pipeline à l’aide de commandes `aio`.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

Dans ce cas, la personne exécutant ces commandes doit être ajoutée au rôle **Responsable de déploiement** dans Admin Console.

Consultez [Autorisations d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) pour plus d’informations.
