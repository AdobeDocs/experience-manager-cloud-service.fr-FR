---
title: Cloud Manager – FAQ relative à Cloud Services
seo-title: Cloud Manager FAQs
description: Consultez la FAQ relative à Cloud Manager for Cloud Services pour obtenir un certain nombre de conseils de dépannage
seo-description: Follow this page to get answers on Cloud Manager - Cloud Services FAQs
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 100%

---

# FAQ relatives à Cloud Manager {#cloud-manager-faqs}

La section suivante fournit des réponses aux questions les plus fréquentes sur Cloud Manager for Cloud Services.

## Est-il possible d’utiliser Java 11 avec les builds de Cloud Manager ? {#java-11-cloud-manager}

Le build AEM Cloud Manager échoue en cas de tentative de basculement de la version Java 8 à Java 11. Le problème peut avoir de nombreuses causes et la plupart des causes les plus courantes sont documentées ci-dessous :

* Ajoutez le plug-in maven-toolchain-plugin avec les paramètres appropriés pour Java 11, comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=fr#getting-started).  Par exemple, consultez [l’exemple de code de projet wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Si vous rencontrez l’erreur ci-dessous, vous devez supprimer l’utilisation de `maven-scr-plugin` et convertir toutes les annotations OSGi en annotations OSGi R6. Pour obtenir des instructions, consultez [ce lien](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Pour les builds de Cloud Manager, le plug-in Maven Enforcer échoue en présentant l’erreur `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Il s’agit d’un problème connu dû au fait que Cloud Manager utilisait une version différente de Java pour exécuter la commande maven plutôt que de compiler le code. Pour l’instant, évitez d’utiliser `requireJavaVersion` dans vos configurations maven-force-application-plugin.

## Notre déploiement est bloqué en raison de l’échec de la vérification de la qualité du code. Y a-t-il un moyen de contourner cette vérification ? {#deployment-stuck}

Tous les échecs de qualité du code, à l’exception de la *Cote de sécurité*, ne sont pas des mesures critiques ; ils peuvent donc être contournés en développant les éléments dans l’interface utilisateur des résultats.

Un utilisateur ayant un rôle de [responsable de déploiement, responsable de projet ou propriétaire d’entreprise](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr#requirements) peut, au choix, contourner les problèmes, auquel cas le pipeline continue, ou les accepter, auquel cas le pipeline s’arrête avec un échec.  Voir la section [Portes à trois niveaux lors de l’exécution d’un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#how-to-use) pour plus d’informations.


## Sommes-nous autorisés à utiliser SNAPSHOT dans la version de projet Maven ? Comment fonctionne le contrôle de version des packages et des fichiers jar par lot pour les déploiements des environnements d’évaluation et de production ? {#snapshot-version}

Reportez-vous aux scénarios suivants pour en savoir plus sur le contrôle de version des packages et des fichiers jar par lots pour les déploiements en évaluation et en production :

1. Pour les déploiements de développeurs, les fichiers de la branche Git `pom.xml` doivent contenir `-SNAPSHOT` à la fin de la valeur `<version>`. Cela permet les déploiements ultérieurs lorsque la version ne change pas. Pour les déploiements développeurs, aucune version automatique n’est ajoutée ou générée pour la build maven.

1. En cas de déploiement d’évaluation et de production, une version automatique est générée comme indiqué [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=fr#managing-code).

1. Pour le contrôle de version personnalisé dans les déploiements d’évaluation et de production, définissez une version maven en 3 parties telle que `1.0.0`. Mettez à jour la version chaque fois que vous devez effectuer un autre déploiement en production.

1. Cloud Manager ajoute automatiquement sa version aux versions d’évaluation et de production et crée même une branche Git. Aucune configuration spécifique n’est nécessaire. Si l’étape 3 ci-dessus est ignorée, le déploiement fonctionnera correctement et une version sera automatiquement définie.

1. Il n’y aura aucun problème si vous laissez la version avec `-SNAPSHOT` pour les versions ou déploiements d’évaluation et de production. Cloud Manager définit automatiquement un numéro de version approprié et crée pour vous une balise dans Git. Cette balise peut être référencée ultérieurement, si nécessaire.

1. Si vous souhaitez tester un code sur l’environnement de développement, vous pouvez créer une nouvelle branche Git et configurer le pipeline pour qu’il utilise cette autre branche. Cela peut s’avèrer utile lorsque le lancement des déploiements échoue et que vous souhaitez tester les versions plus anciennes du code pour déterminer à quel moment il a échoué.

   La commande Git ci-dessous crée une branche distante nommée *testbranch1* par rapport à une validation préexistante spécifique `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Cette branche spéciale peut être utilisée dans Cloud Manager sans affecter les autres branches :

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consultez la [documentation Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) pour plus d’informations.

   Si vous souhaitez supprimer ultérieurement la branche de test, utilisez la commande delete :

   `git push origin --delete testbranch1`

## La compilation Maven échoue dans les déploiements de Cloud Manager, mais se crée localement sans erreurs. Comment déboguer ? {#maven-build-fail}

Consultez [Ressource Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) pour plus d’informations.

## Que faire si le déploiement de Cloud Manager échoue lors de l’étape de déploiement dans l’environnement AEM as a Cloud Service ?  {#cloud-manager-deployment-cloud-service}

La raison la plus courante de l’échec des déploiements résulte d’autorisations insuffisantes pour l’utilisateur *sling-distribution-importer*.
Référez-vous à l’exemple ci-dessous pour comprendre un problème, une cause et une solution :

**Problème**
Lors d’un déploiement de Cloud Manager dans les environnements AEM as a Cloud Service, l’étape de déploiement échoue et des erreurs semblables à celles observées ci-dessous surviennent.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Cause**

L’utilisateur sling-distribution-importer a besoin d’autorisations supplémentaires pour les chemins de contenu définis dans le package ui.content.  Généralement, cela signifie qu’il faut ajouter des autorisations pour /conf et /var.

**Solution**
La solution consiste à ajouter un script de [configuration RepositoryInitializer OSGi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#deploying) à votre package de déploiement d’applications afin d’ajouter des listes de contrôle d’accès pour l’utilisateur sling-distribution-importer.
Dans l’exemple d’erreur ci-dessus, le package myapp-base.ui.content-*.zip inclut le contenu situé sous `/conf` et `/var/workflow`. Pour que le déploiement n’échoue pas, nous devons ajouter des autorisations pour sling-distribution-importer sous ces chemins.
Voici un exemple [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) d’une configuration OSGi de ce type. Elle ajoute des autorisations supplémentaires pour l’utilisateur sling-distribution-importer user.  Cette configuration ajoute des autorisations sous /var.  Ce fichier xml situé sous [1] doit être ajouté au package de l’application sous `/apps/myapp/config` (où myapp est le dossier dans lequel est stocké le code de l’application).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Si *sling-distribution-importer* n’est pas la cause, le déploiement peut échouer en raison d’une mauvaise configuration OSGi qui bloque un service prêt à l’emploi. Vérifiez les journaux pendant le déploiement pour voir s’il y a des erreurs évidentes.

1. Le déploiement peut échouer en raison de configurations de Dispatcher ou Apache incorrectes. Veillez à tester vos configurations Apache et Dispatcher localement à l’aide de l’image Docker incluse dans le SDK. Voir la section [Dispatcher en mode cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=fr#content-delivery) pour savoir comment configurer le conteneur Docker du Dispatcher pour des tests locaux faciles.

1. Le déploiement peut échouer en raison d’une autre défaillance lors de la réplication des packages de contenu (distribution sling) entre les instances d’auteur et de publication.

   Référez-vous aux étapes ci-dessous pour simuler cette situation sur une configuration locale :

   * Installation d’une instance d’auteur et de publication (à l’aide des derniers fichiers jar du SDK AEM)
   * Connexion à l’instance d’auteur
   * Accédez à **Outils** -> **Déploiement** -> **Distribution**
   * Distribuez les packages de contenu faisant partie de la base de code et vérifiez si la file d’attente est bloquée avec une erreur

## Impossible de définir une variable à l’aide des variables de pipeline définies par aio cloud manager. Comment déboguer ces problèmes ? {#set-variable}

Si vous obtenez une erreur `403` lorsque vous tentez de référencer ou de définir des variables de pipeline au moyen de commandes similaires à celles ci-dessous, vous devez être ajouté en tant que rôle de produit *Responsable de déploiement* Cloud Manager dans Admin Console.\
Consultez [Autorisations d’API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) pour plus d’informations.

Commandes et erreurs connexes :

`$ aio cloudmanager:list-pipeline-variables 222`

*Erreur* : `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Erreur* : `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Erreur* : `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
