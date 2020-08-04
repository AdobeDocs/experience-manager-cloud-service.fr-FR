---
title: Outil de migration des workflows de ressources
description: 'Outil de migration des workflows de ressources '
translation-type: tm+mt
source-git-commit: 3a438de3c460d4dc5a8b8617f0ec0eefc56f1665
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 46%

---


# Outil de migration des workflows de ressources {#asset-workflow-migration}

L’outil de migration des workflows de ressources permet d’effectuer automatiquement la migration des workflows de traitement de ressources, entre des déploiements d’AEM on-premise ou sur AMS et le traitement de profils et de configurations OSGi destinés à être utilisés dans AEM Assets as a Cloud Service.

## Présentation {#introduction}

Cette section décrit les ressources et les détails de la mise en œuvre de l’outil de migration des workflows de ressources.

Grâce à cet utilitaire, les développeurs AEM peuvent effectuer la migration des workflows de traitement de ressources vers AEM as a Cloud Service.

## workflows pris en charge {#migration-support-for-workflows}

Les workflows offrent un niveau de prise en charge de la migration variable. Consultez cette [liste de workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties)spécifiques. Les workflows sont classés dans les catégories suivantes en fonction de l&#39;appui fourni. Adobe prend en charge la migration des workflows répertoriés dans `SUPPORTED`, `REQUIRED`ou `OPTIONAL` catégories. Les étapes de processus mentionnées dans les autres catégories ne sont pas prises en charge.

* `SUPPORTED`: Fonctionnalités prises en charge en [!DNL Experience Manager Assets] tant que Cloud Service.
* `OPTIONAL`: Fonctionnalité facultative en [!DNL Experience Manager Assets] tant que Cloud Service.
* `REQUIRED`: Étape requise ajoutée au processus.
* `UNNECESSARY`: La fonctionnalité n’est pas nécessaire en [!DNL Experience Manager Assets] tant que Cloud Service.
* `NUI_OOTB`: Fonctionnalités fournies par [Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Fonctionnalités fournies par [!DNL Dynamic Media] les connecteurs par défaut.
* `NUI_MIGRATED`: Migration vers un profil de [traitement pour le service](/help/assets/asset-microservices-configure-and-use.md)Asset Compute.
* `UNSUPPORTED`: Actuellement non pris en charge en [!DNL Experience Manager Assets] tant que Cloud Service.

## Installation de l’outil de migration des workflows de ressources {#installing-tool}

Pour en savoir plus sur l’installation et la création de code à partir de la source, voir **[Ressource Git : AEM Assets as a Cloud Service – Migration des workflows](https://github.com/adobe/aem-cloud-migration)**.
