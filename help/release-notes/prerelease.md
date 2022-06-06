---
title: Canal de version prédéfinie « [!DNL Adobe Experience Manager] as a Cloud Service »
description: Canal de version prédéfinie « [!DNL Adobe Experience Manager] as a Cloud Service »
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: c2f0b9c904374b5e59ce2b2f268fdd73dfdbfd21
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 84%

---

# Canal de version prédéfinie d’[!DNL Adobe Experience Manager] as a Cloud Service {#prerelease-channel}


## Présentation {#introduction}

[!DNL Adobe Experience Manager] as a Cloud Service offre de nouvelles fonctionnalités à une cadence mensuelle, conformément au planning de la [feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr#aem-as-cloud-service). Pour vous familiariser avec les fonctionnalités programmées pour le mois suivant, les clients peuvent s’abonner au canal de version préliminaire, accessible en configurant de manière appropriée des environnements de développement de programme standard ou tout environnement de programme de test. Les clients peuvent prévisualiser les modifications apportées à la console Sites, mais aussi créer du code lié à toute nouvelle API de version préliminaire.

La liste des fonctionnalités de version préliminaire pour un mois donné est publiée dans les [notes de mise à jour mensuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!VIDEO](/help/release-notes/assets/prerelease-overview.mp4)

## Activation de la version préliminaire {#enable-prerelease}

Les fonctionnalités de la version préliminaire peuvent être expérimentées de différentes manières :

* Environnements cloud (environnements de développement de programme standard ou tout type d’environnement de programme de test)
* SDK local

### Environnements cloud {#cloud-environments}

Pour mettre à jour un environnement Cloud afin d’utiliser la version préliminaire, ajoutez une nouvelle [variable d&#39;environnement](../implementing/cloud-manager/environment-variables.md) à l’aide de l’interface utilisateur de configuration de l’environnement dans Cloud Manager :

1. Accédez au **Programme** > **Environnement** > **Configuration de l’environnement** vous souhaitez mettre à jour.
1. Ajouter un nouveau [variable d&#39;environnement](../implementing/cloud-manager/environment-variables.md):

   | Nom | Valeur | Service appliqué | Type |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Tous | Variable |

1. Enregistrez les modifications et l’environnement s’actualisera avec les bascules de fonctionnalités de version préliminaire activés.

   ![Nouvelle variable d’environnement](assets/env-configuration-prerelease.png)


**Sinon** vous pouvez utiliser l’API Cloud Manager et l’interface de ligne de commande pour mettre à jour les variables d’environnement :

* Utilisation [Point d’entrée des variables d’environnement de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables), définissez la variable **AEM_RELEASE_CHANNEL** de la variable d’environnement à la valeur **préliminaires**.

   ```
   PATCH /program/{programId}/environment/{environmentId}/variables
   [
           {
                   "name" : "AEM_RELEASE_CHANNEL",
                   "value" : "prerelease",
                   "type" : "string"
           }
   ]
   ```

* L’interface de ligne de commande de Cloud Manager peut également être utilisée, conformément aux instructions à l’adresse [https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)

   ```aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease”```


La variable peut être supprimée ou redéfinie sur une autre valeur si vous souhaitez que l’environnement soit restauré avec le comportement du canal normal (hors version préliminaire).

### SDK local {#local-sdk}

Vous pouvez voir les nouvelles fonctionnalités de la console Sites dans le SDK Quickstart local et le code par rapport aux nouvelles API dans la version préliminaire en demandant à votre projet Maven de référencer la version préliminaire `API Jar` située dans Maven Central. Vous pouvez également voir ces fonctionnalités sur votre ordinateur local en démarrant le SDK Quickstart standard en mode version préliminaire :

* Téléchargez le SDK à partir du portail de distribution de logiciels et installez-le comme décrit dans la section [Accès au SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).
* Lors du lancement du démarrage rapide du SDK, incluez l’argument `-r prerelease`.
* La valeur est *sticky*. Elle ne peut donc être sélectionnée que lors du premier démarrage. Réinstallez le SDK pour modifier l’option de ligne de commande.

Comme il peut y avoir plusieurs versions de maintenance AEM entre les versions mensuelles des fonctionnalités, vous pouvez télécharger ces nouveaux SDK et référencer les nouvelles versions du SDK API Jar dans les projets Maven. Les versions de maintenance n’ajouteront pas de fonctionnalités de version préliminaire supplémentaires, mais pourraient inclure d’autres modifications plus modestes comme des correctifs de bogues ou de sécurité et des améliorations de performances.
Les JavaDocs sont publiés sur Maven Central.

Pour créer un build à partir du SDK de version préliminaire :

1. modifiez le fichier pom.xml de votre projet maven pour référencer un fichier jar api du sdk de version préliminaire distinct, qui est publié sur Maven central. Il contient une nouvelle api Java éventuelle pour les fonctionnalités de la version préliminaire et possède une dépendance liée au jar de l’api du sdk. Il utilise la même version.

   À titre d’exemple, voici un extrait de code de la section de gestion des dépendances du modèle pom parent faisant référence au fichier Jar d’API classique :

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
1. Si vous êtes satisfait de son fonctionnement local, validez le code d’une branche de développement et utilisez un pipeline hors production Cloud Manager pour le déploiement dans un environnement abonné au canal de version préliminaire.

>[!CAUTION]
> 
> L’artifactId `aem-prerelease-sdk-api` ne doit jamais être utilisé lors d’un déploiement dans l’environnement intermédiaire ou de production. Utilisez toujours aem-sdk-api lors d’un déploiement via le pipeline de production. De même, les API de version préliminaire de référencement de code ne doivent pas être déployées via le pipeline de production.

Le [module externe maven d’analyseur de build du SDK CS AEM version 1.0, et versions ultérieures](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr#developing) détectera si l’api de version préliminaire est utilisée dans un projet en examinant les dépendances. Si l’analyseur le trouve, il utilisera l’api sdk de version préliminaire pour analyser le projet.

## Considérations {#considerations}

Éléments à retenir concernant le canal de version préliminaire :

* Certaines fonctionnalités déployées dans la version du mois suivant ne seront pas nécessairement incluses dans le canal de version préliminaire.
* Les fonctionnalités de la version préliminaire sont soumises à un contrôle qualité rigoureux et sont conçues pour être complètes et non en version bêta. Si vous constatez des problèmes, signalez-les comme vous le feriez si vous suspectez des bogues dans les fonctionnalités d’une version d’AEM normale.
* Pour déterminer si un environnement est configuré pour le canal de version préliminaire, accédez à la page **À propos** de la console AEM et vérifiez si le numéro de version AEM comprend un suffixe *prerelrelease* tel que ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![about](/help/release-notes/assets/about.png)
