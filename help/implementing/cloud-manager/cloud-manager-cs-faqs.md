---
title: Cloud Manager - FAQ sur les Cloud Services
seo-title: FAQ sur Cloud Manager
description: Pour obtenir des conseils de dépannage, reportez-vous à la FAQ de Cloud Manager pour les Cloud Services .
seo-description: Consultez cette page pour obtenir des réponses sur les FAQ Cloud Manager - Cloud Services
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 3%

---

# Questions fréquentes sur Cloud Manager {#cloud-manager-faqs}

La section suivante fournit des réponses aux questions fréquentes sur Cloud Manager pour les Cloud Services.

## Est-il possible d’utiliser Java 11 avec les versions Cloud Manager ? {#java-11-cloud-manager}

AEM version de Cloud Manager échoue lors de la tentative de basculement de la version de Java 8 à 11. Le problème peut avoir de nombreuses causes et la plupart des causes les plus courantes sont décrites ci-dessous :

* Ajoutez le plug-in maven-toolchain-plugin avec les paramètres corrects pour Java 11, comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Par exemple, consultez l’ [exemple de code de projet wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Si vous rencontrez l’erreur ci-dessous, vous devez supprimer l’utilisation de `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6. Pour obtenir des instructions, voir [ici](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Pour les versions de Cloud Manager, le module maven Enforcement échoue avec l’erreur `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Il s’agit d’un problème connu, car Cloud Manager utilise une autre version de Java pour exécuter la commande maven plutôt que de compiler le code. Pour l’instant, omettez `requireJavaVersion` de vos configurations maven-forcer-plugin.

## Notre déploiement est bloqué car la vérification de la qualité du code a échoué. Y a-t-il un moyen de contourner ce contrôle ? {#deployment-stuck}

Tous les échecs de qualité du code, à l’exception de *Évaluation de la sécurité* ne sont pas des mesures critiques. Ils peuvent donc être contournés en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur disposant du rôle [Gestionnaire de déploiement, chef de projet ou propriétaire d’entreprise](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) peut remplacer les problèmes, auquel cas le pipeline se poursuit ou il peut accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.  Voir [Points de contrôle à trois niveaux lors de l’exécution d’un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#how-to-use) pour plus d’informations.


## Sommes-nous autorisés à utiliser SNAPSHOT dans la version du projet Maven ? Comment le contrôle de version des packages et des fichiers JAR de bundle fonctionne-t-il pour les déploiements de test et de production ? {#snapshot-version}

Reportez-vous aux scénarios suivants pour en savoir plus sur le contrôle de version des packages et des fichiers JAR de bundle pour les déploiements dans les environnements d’évaluation et de production :

1. Pour les déploiements de développeurs, les fichiers `pom.xml` de la branche Git doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`. Cela permet un déploiement ultérieur pour lequel la version ne change pas et est toujours installée. Dans les déploiements de développeurs, aucune version automatique n’est ajoutée ou générée pour la version Maven.

1. Dans les déploiements d’évaluation et de production, une version automatique est générée comme décrit [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven appropriée en 3 parties telle que `1.0.0`. Augmentez la version chaque fois que vous devez effectuer un autre déploiement en production.

1. Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée même une branche Git. Aucune configuration spéciale n’est requise. Si l’étape 3 ci-dessus est ignorée, le déploiement fonctionne toujours correctement et une version est automatiquement définie.

1. Il n’y a aucun problème si vous laissez la version avec `-SNAPSHOT` pour les versions ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée une balise pour vous dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

1. Si vous souhaitez tester du code expérimental dans un environnement de développement, vous pouvez créer une branche Git et définir le pipeline pour utiliser cette autre branche. Cela s’avère utile lorsque les déploiements commencent à échouer et que vous souhaitez tester les versions plus anciennes du code pour déterminer le moment où il a échoué.

   La commande Git ci-dessous crée une branche distante nommée *testbranch1* par rapport à une validation préexistante spécifique `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Cette branche spéciale peut être utilisée dans Cloud Manager sans affecter les autres branches :

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Pour plus d’informations, voir la [documentation Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) .

   Si vous souhaitez supprimer ultérieurement la branche de test, utilisez la commande delete :

   `git push origin --delete testbranch1`

## La version Maven échoue dans les déploiements de Cloud Manager, mais est créée localement sans erreur. Débogage? {#maven-build-fail}

Voir [Ressource Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus d’informations.

## Que faire si le déploiement de Cloud Manager échoue à l’étape de déploiement dans AEM as a Cloud Service Environment ? {#cloud-manager-deployment-cloud-service}

La raison la plus courante de l’échec des déploiements est due à des autorisations insuffisantes pour l’utilisateur *sling-distribution-importer*.
Reportez-vous à l’exemple ci-dessous pour comprendre un problème, une cause et une solution :

****
Problème : lors d’un déploiement de Cloud Manager sur AEM en tant qu’environnements de Cloud Service, l’étape de déploiement échoue et des erreurs comme celles ci-dessous sont observées.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Cause**

L’utilisateur de l’importateur de distribution Sling a besoin d’autorisations supplémentaires pour les chemins de contenu définis dans le package ui.content.  Cela signifie généralement que nous devons ajouter des autorisations pour /conf et /var.

****
SolutionLa solution consiste à ajouter un  [script de configuration OSGi ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#deploying) RepositoryInitializer à votre package de déploiement d’applications afin d’ajouter des listes de contrôle d’accès pour l’utilisateur de l’importateur de distribution Sling.
Dans l’exemple d’erreur ci-dessus, le package myapp-base.ui.content-*.zip inclut du contenu sous `/conf` et `/var/workflow`. Pour que le déploiement n’échoue pas, nous devons ajouter des autorisations pour l’importateur de distribution Sling sous ces chemins.
Voici un exemple [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) d’une configuration OSGi de ce type qui ajoute des autorisations supplémentaires pour l’utilisateur de l’importateur de distribution Sling.  Cette configuration ajoute des autorisations sous /var.  Ce fichier xml situé sous [1] doit être ajouté au package de l’application sous `/apps/myapp/config` (où myapp est le dossier dans lequel le code de l’application est stocké).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Si *sling-distribution-importer* n’est pas la cause, le déploiement peut échouer en raison d’une configuration OSGi incorrecte qui rompt un service prêt à l’emploi. Vérifiez les journaux pendant le déploiement pour voir s’il existe des erreurs évidentes.

1. Le déploiement peut échouer en raison de configurations Dispatcher ou Apache incorrectes. Veillez à tester localement vos configurations Apache et Dispatcher à l’aide de l’image Docker incluse dans le SDK. Voir [Dispatcher dans Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=fr#content-delivery) pour savoir comment configurer le conteneur Docker de Dispatcher pour des tests locaux simples.

1. Le déploiement peut échouer en raison d’un autre échec lors de la réplication des packages de contenu (distribution sling) entre les instances d’auteur et de publication.

   Reportez-vous aux étapes ci-dessous pour simuler cela sur une configuration locale :

   * Installez une instance de création et de publication (à l’aide des derniers jars de SDK AEM).
   * Connectez-vous à l’instance d’auteur .
   * Accédez à **Outils** -> **Déploiement** -> **Distribution**
   * Distribuer les packages de contenu qui font partie de la base de code et voir si la file d’attente est bloquée avec une erreur

## Impossible de définir une variable via les variables de pipeline définies par aio cloud manager. Comment déboguer ces problèmes ? {#set-variable}

Si vous obtenez une erreur `403` lorsque vous essayez de répertorier ou de définir des variables de pipeline via des commandes similaires à celles ci-dessous, vous devez être ajouté en tant que rôle de produit *Deployment Manager* Cloud Manager dans le Admin Console.\
Voir [Autorisations API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) pour plus d’informations.

Commandes et erreurs associées :

`$ aio cloudmanager:list-pipeline-variables 222`

*Erreur*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Erreur*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Erreur*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
