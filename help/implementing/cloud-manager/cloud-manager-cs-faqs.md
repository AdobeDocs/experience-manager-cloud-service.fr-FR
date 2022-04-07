---
title: FAQ sur Cloud Manager
description: Trouvez des réponses aux questions les plus fréquemment posées sur Cloud Manager dans AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 5f4bbedaa5c4630d6f955bb0986e8b32444d6aa3
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 24%

---


# FAQ relatives à Cloud Manager {#cloud-manager-faqs}

Ce document répond aux questions les plus fréquemment posées sur Cloud Manager dans AEM as a Cloud Service.

## Est-il possible d’utiliser Java 11 avec les builds de Cloud Manager ? {#java-11-cloud-manager}

Oui. Vous devez ajouter la variable `maven-toolchains-plugin` avec les paramètres appropriés pour Java 11.

* Ceci est documenté [here](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).
* Par exemple, reportez-vous à la section [exemple de code de projet wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mon build échoue avec une erreur concernant maven-scr-plugin après le passage de Java 8 à Java 11. Que puis-je faire ? {#build-fails-maven-scr-plugin}

Votre version d’AEM Cloud Manager peut échouer lors de la tentative de basculement de la version de Java 8 à 11. Si vous rencontrez l’erreur suivante, vous devez supprimer `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Pour plus d’informations sur la suppression de ce module externe, voir [ici.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Mon build échoue avec une erreur sur RequireJavaVersion après le passage de Java 8 à Java 11. Que puis-je faire ? {#build-fails-requirejavaversion}

Pour les versions de Cloud Manager, la variable `maven-enforcer-plugin` échoue avec cette erreur.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

Il s’agit d’un problème connu dû au fait que Cloud Manager utilisait une version différente de Java pour exécuter la commande maven plutôt que de compiler le code. Simplement omettre `requireJavaVersion` de votre `maven-enforcer-plugin` configurations.

## La vérification de la qualité du code a échoué et notre déploiement est bloqué. Y a-t-il un moyen de contourner cette vérification ? {#deployment-stuck}

Oui. Tous les échecs de vérification de la qualité du code, à l’exception de l’évaluation de sécurité, ne sont pas des mesures critiques. Ils peuvent donc être contournés en développant les éléments dans l’interface utilisateur des résultats.

Voir le document [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) pour plus d’informations.

## Puis-je utiliser SNAPSHOT pour la version du projet Maven ? {#use-snapshot}

Oui. Pour les déploiements de développeurs, la branche git `pom.xml` Les fichiers doivent contenir `-SNAPSHOT` à la fin de la variable `<version>` .

Cela permet de continuer à installer le déploiement suivant lorsque la version n’a pas été modifiée. Pour les déploiements développeurs, aucune version automatique n’est ajoutée ou générée pour la build maven.

Vous pouvez également définir la version sur `-SNAPSHOT` pour les versions ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée une balise pour vous dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

## Comment le contrôle de version des packages et des lots fonctionne-t-il sur les déploiements d’évaluation et de production ? {#snapshot-version}

Dans les déploiements intermédiaires et de production, une version automatique est générée sous la forme [documenté ici.](/help/implementing/cloud-manager/managing-code/project-version-handling.md)

Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven en trois parties appropriée comme `1.0.0`. Augmentez la version à chaque déploiement en production.

Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée une branche Git. Aucune configuration spécifique n’est nécessaire. Si vous ne définissez pas de version Maven comme décrit précédemment, le déploiement réussit toujours et une version est automatiquement définie.

## Ma version Maven échoue pour les déploiements de Cloud Manager, mais elle est créée localement sans erreur. Qu&#39;est-ce qui ne va pas ? {#maven-build-fail}

Voir [cette ressource git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus d’informations.

## Que faire si un déploiement Cloud Manager échoue à l’étape de déploiement dans AEM as a Cloud Service ? {#cloud-manager-deployment-cloud-service}

La raison la plus courante de l’échec d’un déploiement est due à un manque d’autorisations pour la variable `sling-distribution-importer` utilisateur. Dans ce cas, l’étape de déploiement échoue lors d’un déploiement de Cloud Manager et des erreurs telles que les suivantes sont générées.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

Le `sling-distribution-importer` l’utilisateur a besoin d’autorisations supplémentaires pour les chemins de contenu définis dans la variable `ui.content package`.  Cela signifie généralement que vous devez ajouter des autorisations pour les deux `/conf` et `/var`.

La solution consiste à ajouter une [Configuration OSGi de RepositoryInitializer](/help/implementing/deploying/overview.md#repoint) script de votre package de déploiement d’applications pour ajouter des listes de contrôle d’accès pour la variable `sling-distribution-importer` utilisateur.

Dans l’exemple d’erreur précédent, le package `myapp-base.ui.content-*.zip` inclut du contenu sous `/conf` et `/var/workflow`. Pour que le déploiement réussisse, les autorisations de la variable `sling-distribution-importer` sous ces chemins d’accès est nécessaire.

Voici un exemple [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) d’une configuration OSGi de ce type. Elle ajoute des autorisations supplémentaires pour l’utilisateur user.  `sling-distribution-importer`  Cette configuration ajoute des autorisations sous `/var`.  Ce fichier xml situé sous [1] doit être ajouté au package de l’application sous `/apps/myapp/config` (où myapp est le dossier dans lequel est stocké le code de l’application).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

## Mon déploiement de Cloud Manager échoue à l’étape de déploiement dans AEM as a Cloud Service et je dispose déjà d’une configuration OSGi RepositoryInitializer. Que puis-je faire d&#39;autre ? {#build-failures}

If [ajout d’une configuration OSGi RepositoryInitializer](##cloud-manager-deployment-cloud-service) n’a pas résolu l’erreur, elle peut être due à l’un de ces problèmes supplémentaires.

* Le déploiement peut échouer en raison d’une configuration OSGi incorrecte qui rompt un service prêt à l’emploi.
   * Vérifiez les journaux pendant le déploiement pour voir s’il y a des erreurs évidentes.

* Le déploiement peut échouer en raison de configurations Dispatcher ou Apache incorrectes.
   * Veillez à tester localement vos configurations Apache et Dispatcher à l’aide de l’image Docker incluse dans le SDK.
   * Voir la section [Dispatcher en mode cloud](/help/implementing/dispatcher/disp-overview.md#content-delivery) pour savoir comment configurer le conteneur Docker du Dispatcher pour des tests locaux faciles.

* Le déploiement peut échouer en raison d’un autre échec lors de la réplication des packages de contenu (distribution Sling) entre les instances d’auteur et de publication.
   * Suivez ces étapes pour simuler le problème sur une configuration locale.
      1. Installez une instance de création et de publication localement à l’aide des derniers fichiers JAR du SDK AEM.
      1. Connectez-vous à l’instance d’auteur.
      1. Accédez à **Outils** -> **Déploiement** -> **Distribution**.
      1. Distribuez les packages de contenu faisant partie de la base de code et vérifiez si la file d’attente est bloquée avec une erreur.

## Je ne parviens pas à définir une variable à l’aide d’une commande aio. Que puis-je faire ? {#set-variable}

Vous pouvez recevoir une `403` une erreur de ce type lors de la tentative de liste ou de définition de variables de pipeline via `aio` des commandes.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

Dans ce cas, l’utilisateur exécutant ces commandes doit être ajouté à la variable **Gérer le déploiement** dans le Admin Console.

Consultez [Autorisations d’API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) pour plus d’informations.
