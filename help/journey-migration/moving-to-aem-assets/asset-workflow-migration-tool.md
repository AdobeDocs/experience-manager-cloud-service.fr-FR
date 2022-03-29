---
title: Outil de migration des workflows de ressources
description: Outil de migration des workflows de ressources
exl-id: a95caf5e-e6b2-463f-bebd-b791104fd25c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 100%

---

# Outil de migration des workflows de ressources {#asset-workflow-migration}

L’outil de migration des workflows de ressources permet d’effectuer automatiquement la migration des workflows de traitement de ressources, entre des déploiements d’AEM on-premise ou sur AMS et le traitement de profils et de configurations OSGi destinés à être utilisés dans AEM Assets as a Cloud Service.

## Présentation {#introduction}

Cette section décrit les ressources et les détails de la mise en œuvre de l’outil de migration des workflows de ressources.

Grâce à cet utilitaire, les développeurs AEM peuvent effectuer la migration des workflows de traitement de ressources vers AEM as a Cloud Service.

## Workflows pris en charge {#migration-support-for-workflows}

Les workflows offrent un niveau de prise en charge de la migration variable. Consultez cette [liste de workflows spécifiques](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). Les workflows sont classés dans les catégories suivantes en fonction de la prise en charge assurée. Adobe prend en charge la migration des workflows répertoriés dans les catégories `SUPPORTED`, `REQUIRED` ou `OPTIONAL`. Les étapes de workflow mentionnées dans les autres catégories ne sont pas prises en charge.

* `SUPPORTED` : fonctionnalité prise en charge dans [!DNL Experience Manager Assets] as a Cloud Service.
* `OPTIONAL` : fonctionnalité facultative dans [!DNL Experience Manager Assets] as a Cloud Service.
* `REQUIRED` : étape requise ajoutée au workflow.
* `UNNECESSARY` : fonctionnalité non requise dans [!DNL Experience Manager Assets] as a Cloud Service.
* `NUI_OOTB` : fonctionnalité fournie par [Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB` : fonctionnalité fournie par les connecteurs [!DNL Dynamic Media] par défaut.
* `NUI_MIGRATED` : migré vers un [profil de traitement pour Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED` : actuellement non pris en charge dans [!DNL Experience Manager Assets] as a Cloud Service.

## Utilisation de l’outil de migration des workflows de ressources {#use-workflow-migrator}

* **[!DNL Adobe I/O]Interface de ligne de commande** : Adobe recommande d’utiliser l’outil de migration des workflows de ressources via `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] en tant que module externe de refactorisation de code [!DNL Cloud Service] pour l’interface de ligne de commande [!DNL Adobe I/O]). Pour savoir comment installer et utiliser le module externe, voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **Utilitaire autonome** : l’outil de migration des workflows de ressources peut également être exécuté en tant qu’utilitaire autonome. Pour en savoir plus sur l’installation et la création de code à partir de la source, voir [Ressource Git : [!DNL Experience Manager Assets]  en tant que  [!DNL Cloud Service] - migration des workflows](https://github.com/adobe/aem-cloud-migration).
