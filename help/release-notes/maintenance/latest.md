---
title: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 4aa4954f214545dcd768fdf955f1fc2f776da939
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 17%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante présente les notes techniques de mise à jour de la version de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 11835 {#release-11835}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 11835, qui a été publiée publiquement le 19 avril 2023. Cette version de maintenance est une mise à jour de la version de maintenance 11382 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Consultez les [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Problèmes résolus {#fixed-issues-11835}

- SITES-12573 - Les requêtes GraphQL utilisant des variables à l’intérieur d’un filtre échouent si une variable n’est pas spécifiée. Veuillez ne pas mettre à jour cette version si vous utilisez GraphQL avec AEM as a Cloud Service.
- SKYOPS-51970 - Régression identifiée de la version FACT utilisée dans l’étape buildImage, ce qui entraîne un mappage utilisateur non correspondant.
- GRANITE-44542 - Des problèmes ont été signalés pour les clients qui n’ont pas spécifié de type de noeud de package (en fournissant un fichier .content.xml avec jcr:primaryType) pour les dossiers inclus dans le filtre de package. Ces dossiers étaient alors traités comme nt:folder, ce qui entraînait des problèmes dans plusieurs cas.
- SKYOPS-56928 - La régression Apache HTTPD peut entraîner des erreurs 404. Si vous rencontrez ces problèmes, pour des raisons de sécurité, il est recommandé de restaurer la version précédente et d’éviter tout pipeline s’exécutant pendant cette période.

### Technologies intégrées {#embedded-tech-11835}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [API 1.44.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du langage de modèle de HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.21.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
