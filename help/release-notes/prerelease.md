---
title: Canal de version préliminaire Adobe Experience Manager as a Cloud Service
description: Découvrez comment utiliser le canal de version préliminaire pour obtenir un aperçu des fonctions à venir à AEM as a Cloud Service.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: 9a76a1c2b5e3b7986654b0843842b015811679a2
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 23%

---


# Canal de version préliminaire Adobe Experience Manager as a Cloud Service {#prerelease-channel}

Découvrez comment utiliser le canal de version préliminaire pour obtenir un aperçu des fonctions à venir à AEM as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service offre de nouvelles fonctionnalités à un rythme mensuel, selon les [Experience Manager relâche la feuille de route.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr#aem-as-cloud-service)

Pour vous familiariser avec les fonctionnalités programmées pour le mois suivant, vous pouvez vous abonner au canal de version préliminaire, accessible par la configuration de vos environnements de développement ou de tout environnement de test. Vous pouvez prévisualiser les modifications accessibles via l’interface utilisateur d’AEM et créer du code par rapport à toute nouvelle API de version préliminaire.

La liste des fonctionnalités de version préliminaire pour un mois donné est publiée dans la variable [notes de mise à jour mensuelles.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## AEM versions as a Cloud Service {#releases}

AEM as a Cloud Service comporte deux types de versions.

* **Versions mensuelles** ajouter des fonctionnalités à AEM as a Cloud Service
* **Mises à jour critiques** ajoutez des mises à jour de sécurité, des améliorations de performances et des correctifs de bogues, qui sont appliquées quotidiennement.

Ce modèle garantit des versions continues sans interruption de service.

Le canal de version préliminaire vous permet de prévisualiser les fonctionnalités programmées pour la version mensuelle à venir afin d’évaluer les fonctionnalités à venir et de planifier leur mise en oeuvre possible pour vos propres projets. Il vous permet de planifier la prochaine version mensuelle.

Si, par exemple, nous sommes en mai et que vous êtes abonné au canal de version préliminaire, vous pouvez évaluer les fonctionnalités de la version de juin à venir.

![Graphique de cadence de version préliminaire](assets/prerelease-cadence.png)

La version préliminaire vous donne un délai d’un mois pour découvrir les fonctionnalités AEMaaCS à venir, ce qui vous donne le temps d’évaluer l’impact de toutes nouvelles fonctionnalités sur vos projets et personnalisations, ainsi que de planifier le déploiement de telles fonctionnalités, les tests et la formation des utilisateurs.

Pour tirer pleinement parti du canal de version préliminaire, quatre étapes sont nécessaires.

1. [Marquer vos calendriers](#mark-calendars)
1. [Consultez les notes de mise à jour](#release-notes)
1. [Accès aux nouvelles fonctionnalités et essai](#new-features)
1. [Formation des utilisateurs](#train-users)

## Marquage de vos calendriers {#mark-calendars}

Les versions mensuelles sont planifiées bien à l’avance et les dates de publication sont publiées le [Adobe Experience League.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr#aem-as-cloud-service)

Prenez note des dates de publication afin de prévoir le temps de passer en revue et de tester les fonctionnalités à venir.

## Passez en revue les notes de mise à jour {#release-notes}

Une fois que les dates de publication sont indiquées dans votre calendrier, veillez à cocher la case [Adobe Experience League](/help/release-notes/release-notes-cloud/release-notes-current.md) le jour de la mise à jour pour consulter les dernières notes de mise à jour.

Chaque version est accompagnée de notes de mise à jour qui documentent non seulement les nouveautés de cette version, mais également les fonctionnalités disponibles pour l’évaluation de version préliminaire. Familiarisez-vous avec l’avance et prévoyez de profiter des dernières fonctionnalités d’AEMaaCS !

Vous pouvez également [vérifier les problèmes connus ;](/help/release-notes/known-issues.md) qui sont publiés avec chaque version afin que vous puissiez également être informé de tout problème technique susceptible de présenter un problème lors de votre évaluation ou de l’adoption éventuelle de nouvelles fonctionnalités.

## Activation du canal version préliminaire pour accéder aux nouvelles fonctionnalités et en tester de nouvelles {#new-features}

Le canal de version préliminaire peut être activé dans n’importe quel environnement de développement ou d’environnement de test. La version préliminaire ne peut pas être activée dans les environnements d’évaluation ou de production.

Les fonctionnalités de la version préliminaire peuvent être expérimentées de différentes manières :

* [Environnements cloud](#cloud-environments)
* [SDK local](#local-sdk)

### Environnements cloud {#cloud-environments}

Pour mettre à jour un environnement cloud afin d’utiliser la version préliminaire, vous devez ajouter une nouvelle variable d’environnement. Vous pouvez le faire à l’aide de l’interface utilisateur de Cloud Manager ou via l’interface de ligne de commande.

#### Ajout d’une variable d’environnement à l’aide de l’interface utilisateur {#add-with-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Accédez au programme dans lequel vous souhaitez activer la version préliminaire.

1. Sélectionnez l’environnement dans lequel vous souhaitez activer la version préliminaire et accéder à sa configuration via **Programme** > **Environnement** > **Configuration de l’environnement**.

1. Ajouter un nouveau [Variable d’environnement :](../implementing/cloud-manager/environment-variables.md)

   | Nom | Valeur | Service appliqué | Type |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Tous | Variable |

1. Enregistrez les modifications et l’environnement s’actualisera avec les boutons (bascule) pour les fonctionnalités de version préliminaire activées.

   ![Nouvelle variable d’environnement](assets/env-configuration-prerelease.png)

#### Ajout d’une variable d’environnement à l’aide de l’interface en ligne de commande {#add-with-cli}

Vous pouvez également utiliser l’API Cloud Manager et l’interface de ligne de commande pour mettre à jour les variables d’environnement.

* Utilisation [point de terminaison des variables d’environnement de l’API Cloud Manager,](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables) définissez la variable `AEM_RELEASE_CHANNEL` de la variable d’environnement à la valeur `prerelease`.

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

* [Interface de ligne de commande de Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) peut également être utilisé.

   ```shell
   aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease
   ```

La variable peut être supprimée ou redéfinie sur une autre valeur si vous souhaitez que l’environnement soit restauré avec le comportement du canal normal (hors version préliminaire).

### SDK local {#local-sdk}

Vous pouvez voir les nouvelles fonctionnalités dans la console Sites dans le SDK Quickstart local et le code par rapport aux nouvelles API dans la version préliminaire en configurant votre projet Maven pour référencer la version préliminaire. `API Jar` situé dans Maven Central. Vous pouvez également voir ces fonctionnalités de version préliminaire dans votre environnement de développement local en démarrant le SDK Quickstart standard en mode de version préliminaire.

#### Démarrage du SDK de démarrage rapide en mode version préliminaire {#prerelease-mode}

1. Téléchargez le SDK à partir du portail de distribution de logiciels et installez-le comme décrit dans la section [Accès au SDK d’AEM as a Cloud Service.](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. Lors du lancement du démarrage rapide du SDK, incluez l’argument `-r prerelease`.

La valeur est sticky. Elle ne peut donc être sélectionnée que lors du premier démarrage. Réinstallez le SDK pour modifier l’option de ligne de commande.

Comme il peut y avoir plusieurs versions de maintenance AEM entre les versions mensuelles des fonctionnalités, vous pouvez télécharger ces nouveaux SDK et référencer les nouvelles versions du SDK API Jar dans les projets Maven. Les versions de maintenance n’ajouteront pas de fonctionnalités de version préliminaire supplémentaires, mais pourraient inclure d’autres modifications plus modestes comme des correctifs de bogues ou de sécurité et des améliorations de performances.
Les JavaDocs sont publiés sur Maven Central.

#### Création par rapport au SDK de version préliminaire {#build-sdk}

1. Modification du projet Maven `pom.xml` pour référencer un fichier jar API SDK de version préliminaire distinct, qui est publié sur Maven Central. Contient toute nouvelle API Java pour les fonctionnalités de la version préliminaire et dépend du fichier jar de l’API SDK. Il utilise la même version.

   À titre d’exemple, voici un extrait de code de la section de gestion des dépendances du modèle pom parent faisant référence au fichier jar de l’API classique :

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

1. Déploiement sur votre serveur local 

1. Si vous êtes satisfait de son fonctionnement local, validez le code d’une branche de développement et utilisez un pipeline hors production de Cloud Manager pour le déploiement dans un environnement qui s’abonne au canal de version préliminaire.

>[!CAUTION]
> 
> Le `aem-prerelease-sdk-api` artifactId ne doit jamais être utilisé lors d’un déploiement en environnement intermédiaire ou de production. Toujours utiliser la variable `aem-sdk-api` lors d’un déploiement via le pipeline de production. De même, le code qui référence les API de version préliminaire ne doit pas être déployé via le pipeline de production.

Le [AEM SDK CS Build Analyzer Module externe Maven v1.0 et version ultérieure](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing) détectera si l’API de version préliminaire est utilisée dans un projet en examinant les dépendances. Si l’analyseur le trouve, il utilisera l’API SDK de version préliminaire pour analyser le projet.

## Formation des utilisateurs {#train-users}

Une fois que vous avez testé les nouvelles fonctionnalités dans le canal de version préliminaire et que vous avez décidé de les exploiter dans vos projets, vous devez former vos utilisateurs.

Adobe Experience League offre de nombreuses ressources pour apprendre à utiliser AEMaaCS.

* [Documentation d’AEMaaCS](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr)
* [Tutoriels](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-tutorials/overview.html)
* [Vidéo de présentation de la version mensuelle](/help/release-notes/release-notes-cloud/release-notes-current.md#release-video) dans les notes de mise à jour

## Considérations {#considerations}

Quelques éléments doivent être pris en compte lors de l’utilisation du canal bêta.

* Le canal de version préliminaire ne contient pas nécessairement toutes les nouvelles fonctionnalités à déployer dans la version suivante.
* Les fonctionnalités de la version préliminaire sont soumises à un contrôle qualité rigoureux et sont conçues pour être complètes et non en version bêta. Si vous constatez des problèmes, signalez-les comme vous le feriez si vous suspectez des bogues dans les fonctionnalités d’une version d’AEM normale.
* Pour déterminer si un environnement est configuré pour le canal de version préliminaire, accédez au **A propos** et vérifier si le numéro de version AEM comprend une *préliminaires* suffixe, par exemple ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![À propos](/help/release-notes/assets/about.png)
