---
title: Canal de version préliminaire d’Adobe Experience Manager as a Cloud Service
description: Découvrez comment utiliser le canal de version préliminaire pour obtenir un aperçu des prochaines fonctionnalités d’AEM as a Cloud Service.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
feature: Release Information
role: Admin
source-git-commit: 36da09746f02daad82875329b0aa53ee4eb7c074
workflow-type: ht
source-wordcount: '889'
ht-degree: 100%

---


# Canal de version préliminaire d’Adobe Experience Manager as a Cloud Service {#prerelease-channel}

Découvrez comment utiliser le canal de version préliminaire pour obtenir un aperçu des prochaines fonctionnalités d’AEM as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service propose régulièrement de nouvelles fonctionnalités. La liste des nouvelles fonctionnalités et de celles à venir pour une mise à jour donnée est publiée dans les [notes de mise à jour.](/help/release-notes/release-notes-cloud/release-notes-current.md)

Les fonctionnalités à venir sont généralement disponibles de l’une des deux façons suivantes :

* Dans le cadre d’un programme destiné aux utilisateurs et utilisatrices précoces
* Dans le cadre du canal de version préliminaire

Ce document décrit comment activer le canal de version préliminaire. Le canal de version préliminaire permet d’accéder aux premières fonctionnalités qui seront introduites dans une prochaine version d’AEM. Vous avez ainsi la possibilité de valider les nouvelles fonctionnalités et de planifier leur adoption en vue de leur publication ultérieure. Pour plus d’informations sur le planning des versions d’AEM, consultez le document [Notes de mise à jour d’Adobe Experience Manager (AEM) as a Cloud Service](/help/release-notes/home.md).

## Activer le canal de version préliminaire pour accéder aux fonctionnalités à venir et les essayer {#enable-prerelease}

Le canal de version préliminaire peut être activé dans tout environnement de développement ou de sandbox. Le canal de version préliminaire ne peut pas être activé dans les environnements d’évaluation et de production.

Le canal de version préliminaire est accessible de deux manières :

* [Environnements cloud](#cloud-environments)
* [SDK local](#local-sdk)

### Environnements cloud {#cloud-environments}

Pour mettre à jour un environnement cloud afin d’utiliser le canal de version préliminaire, vous devez ajouter une nouvelle variable d’environnement. Cette opération peut être réalisée dans l’interface utilisateur de Cloud Manager ou l’interface de ligne de commande.

#### Ajouter une variable d’environnement à l’aide de l’interface utilisateur {#add-with-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Accédez au programme pour lequel vous souhaitez activer le canal de version préliminaire.

1. Sélectionnez l’environnement dans lequel vous souhaitez activer le canal de version préliminaire, puis accédez à sa configuration via **Programme** > **Environnement** > **Configuration de l’environnement**.

1. Ajoutez une nouvelle [variable d’environnement](/help/implementing/cloud-manager/environment-variables.md).

   | Nom | Valeur | Service appliqué | Type |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Tous | Variable |

1. Enregistrez les modifications et l’environnement s’actualisera avec le canal de version préliminaire activé.

   ![Nouvelle variable d’environnement](assets/env-configuration-prerelease.png)

#### Ajouter une variable d’environnement à l’aide de l’interface de ligne de commande {#add-with-cli}

Vous pouvez également utiliser l’API Cloud Manager et l’interface de ligne de commande pour mettre à jour les variables d’environnement.

* À l’aide du [point d’entrée des variables d’environnement de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables), appliquez la variable d’environnement `AEM_RELEASE_CHANNEL` à la valeur `prerelease`.

  ```text
  PATCH /program/{programId}/environment/{environmentId}/variables
  [
          {
                  "name" : "AEM_RELEASE_CHANNEL",
                  "value" : "prerelease",
                  "type" : "string"
          }
  ]
  ```

* [L’interface de ligne de commande de Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) peut également être utilisée.

  ```shell
  aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL "prerelease
  ```

La variable peut être supprimée si vous souhaitez restaurer le comportement standard de l’environnement (canal hors version préliminaire).

### SDK local {#local-sdk}

Vous pouvez accéder aux fonctionnalités à venir du canal de version préliminaire dans votre SDK de démarrage rapide local et développer avec les nouvelles API en configurant votre projet Maven pour référencer le fichier `API Jar` du canal de version préliminaire situé dans Maven Central. Vous pouvez également accéder au canal de version préliminaire dans votre environnement de développement local en démarrant le SDK de démarrage rapide standard en mode version préliminaire.

#### Démarrer le SDK de démarrage rapide en mode version préliminaire {#prerelease-mode}

1. Téléchargez le SDK à partir du portail de distribution logicielle et installez-le comme décrit dans la section [Accès au SDK d’AEM as a Cloud Service.](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. Lors du lancement du démarrage rapide du SDK, incluez l’argument `-r prerelease`.

La valeur est sticky. Elle ne peut donc être sélectionnée que lors du premier démarrage. Réinstallez le SDK pour modifier l’option de ligne de commande.

Comme il peut y avoir plusieurs versions de maintenance AEM entre les versions mensuelles des fonctionnalités, vous pouvez télécharger ces nouveaux SDK et référencer les nouvelles versions du SDK API Jar dans les projets Maven. Les versions de maintenance n’ajouteront pas de fonctionnalités de version préliminaire supplémentaires, mais pourraient inclure d’autres modifications plus modestes comme des correctifs de bogues ou de sécurité et des améliorations de performances.
Les JavaDocs sont publiés sur Maven Central.

#### Créer une version à partir du SDK de version préliminaire {#build-sdk}

1. Modifiez le `pom.xml` de votre projet maven pour référencer un jar de l’API du SDK de version préliminaire distinct, qui est publié sur Maven Central. Il contient une nouvelle API Java pour les fonctionnalités de la version préliminaire et possède une dépendance liée au jar de l’API du SDK. Il utilise la même version.

   À titre d’exemple, voici un extrait de code de la section de gestion des dépendances du modèle pom parent faisant référence au jar de l’API standard :

   ```
   <dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
        </dependency>
   ```

   Puis l’utilisation dans un module :

   ```
    <dependencies>
     <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-sdk-api</artifactId>
     </dependency>
   ```

   Pour passer au SDK de la version préliminaire, remplacez simplement la dépendance de `com.adobe.aem:aem-sdk-api` par `com.adobe.aem:aem-prerelease-sdk-api` comme indiqué ci-dessous :

   ```
   <dependencyManagement>
    <dependencies>
      <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-prerelease-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
      </dependency>
   <dependencies>
      <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-prerelease-sdk-api</artifactId>
      </dependency>
   ```

   Comme d’habitude, les projets individuels peuvent utiliser la dépendance.

1. Procédez au déploiement sur votre serveur local.

1. Si son fonctionnement local vous satisfait, validez le code d’une branche de développement et utilisez un pipeline hors production Cloud Manager pour le déploiement dans un [environnement dont le canal de version préliminaire est activé.](#cloud-environments)

>[!CAUTION]
> 
> L’artifactId `aem-prerelease-sdk-api` ne doit jamais être utilisé lors d’un déploiement dans l’environnement en évaluation ou production. Utilisez toujours le `aem-sdk-api` lors d’un déploiement via le pipeline de production. De même, le code référençant les API de version préliminaire ne doit pas être déployé via le pipeline de production.

Le [module externe maven d’analyseur de création du SDK CS AEM version 1.0, et versions ultérieures](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr#developing) détectera si l’API de version préliminaire est utilisée dans un projet en examinant les dépendances. Si l’analyseur le trouve, il utilisera l’API du SDK de version préliminaire pour analyser le projet.

## Considérations {#considerations}

Quelques éléments doivent être pris en compte lors de l’utilisation du canal de version préliminaire.

* Le canal de version préliminaire ne contient pas nécessairement toutes les nouvelles fonctionnalités à déployer dans la version suivante.
* Les fonctionnalités de la version préliminaire sont soumises à un contrôle qualité rigoureux et sont conçues pour être complètes et non en version bêta. Si vous constatez des problèmes, signalez-les comme vous le feriez si vous suspectez des bogues dans les fonctionnalités d’une version d’AEM normale.
* Pour déterminer si un environnement est configuré pour le canal de version préliminaire, accédez à la page **À propos** de la console AEM et vérifiez si le numéro de version AEM comprend un suffixe `PRERELEASE` tel que `Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE`.

![À propos](/help/release-notes/assets/about.png)
