---
title: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: fb9b735c44dddda9572d3a1f90d49452c6ddc094
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante présente les notes techniques de mise à jour de la version de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 11382 {#release-11382}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 11382, publiée publiquement le 28 mars 2023. Cette version de maintenance est une mise à jour de la version de maintenance 11289 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Consultez les [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

>[!IMPORTANT]
>
> Une incohérence peut être signalée sur l’interface utilisateur de Cloud Manager, indiquant &quot;2023.3.11382&quot;, tandis que la version officielle est &quot;2023.02&quot;. Cela est dû au retard de l’activation des fonctionnalités 2023.02.
> Nous travaillons à corriger ce problème pour les prochaines versions.

### Problèmes connus {#known-issues-11382}

- SITES-12573 - Les requêtes GraphQL utilisant des variables à l’intérieur d’un filtre échouent si une variable n’est pas spécifiée. Veuillez ne pas mettre à jour cette version si vous utilisez GraphQL avec AEM as a Cloud Service.
- SKYOPS-51970 - Régression identifiée de la version FACT utilisée dans l’étape buildImage, ce qui entraîne un mappage utilisateur non correspondant.
- GRANITE-44542 - Des problèmes ont été signalés pour les clients qui n’ont pas spécifié de type de noeud de package (en fournissant un fichier .content.xml avec jcr:primaryType) pour les dossiers inclus dans le filtre de package. Ces dossiers étaient alors traités comme nt:folder, ce qui entraînait des problèmes dans plusieurs cas.

### Problèmes résolus {#fixed-issues-11382}

- ASSETS-21023 - Correction du rendu de recadrage intelligent, grâce auquel les clients pouvaient observer une exception de pointeur nul sur l’instance de l’éditeur de tous les environnements AEM lorsqu’ils tentaient d’accéder à ces rendus via l’API.
- SKYOPS-49280 - Lors de l’installation d’une configuration ou d’une mise à jour de lot à l’aide de RDE dans Publier, le résultat peut ne pas être observable, car le cache du Dispatcher de publication n’est pas invalidé.

#### Sites {#sites-issues-11382}

- SITES-7796 - Possibilité pour l’auteur de contenu de publier le fragment de contenu de Principal et ses variantes respectives lors de l’exportation vers la cible
- SITES-97 - GraphQL : Pagination et tri, filtrage hybride

>[!NOTE]
>
> Dans SITES-97, certaines améliorations ont été apportées à l’implémentation de GraphQL, qui peuvent entraîner un comportement inattendu. Voir [Modifications d’AEM GraphQL concernant la gestion des valeurs nulles](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-21792.html?lang=fr) pour plus d’informations.

#### Ressources {#assets-issues-11382}

- ASSETS-20076 - Ajout de la prise en charge du filigrane vidéo correspondant à la prise en charge actuelle du filigrane d’image
- ASSETS-21428 - Ajout d’exclusions pour les modifications CSS

#### Forms {#forms-issues-11382}

- CQ-4351502 - Mise à jour du mappage utilisateur du service pour autoriser l’accès en lecture dans Sites

#### Plateforme {#platform-issues-11382}

- SITES-11040 - Activation conditionnelle de la mise en cache des requêtes persistantes de GraphQL dans Dispatcher

### Technologies intégrées {#embedded-tech-11382}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [API 1.44.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du langage de modèle de HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.21.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
