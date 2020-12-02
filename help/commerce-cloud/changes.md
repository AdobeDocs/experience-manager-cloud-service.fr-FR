---
title: Modifications notables apportées à AEM Commerce en tant que Cloud Service
description: Changements notables apportés à AEM Commerce en tant que Cloud Service par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 2934d0d8d3977bb7884bae9654ac26e9fa57b34f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 14%

---


# Modifications notables apportées à AEM Commerce en tant que Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Ce document met en évidence les différences importantes entre le cadre d&#39;intégration commerciale (CIF) pour les services sur site, les services gérés par Adobe et les Experience Manager en tant que Cloud Service. Concernant les autres changements, consultez le document générique [Modifications apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :
* [Prise en charge de CIF Classic](#cif-classic)
* [Déploiement des outils de création CIF](#cif-tools)
* [Passage d&#39;un service géré sur site et par Adobe](#moving-cif-cs)

## Prise en charge de CIF Classic/Quickstart sur Experience Manager en tant que Cloud Service {#cif-classic}

Le cadre d’intégration du commerce classique qui incluait un importateur de produits pour importer et stocker des catalogues de produits en Experience Manager n’est plus disponible en tant que Cloud Service dans Experience Manager. L’utilisation de CIF classique n’est pas prise en charge en Experience Manager en tant que Cloud Service et les projets utilisant CIF classique devront remplacer l’implémentation CIF classique par la version prise en charge, comme décrit dans [CIF sur Experience Manager en tant que Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/architecture/magento.html#overview)

## Déploiement du CIF {#deployment}

Vous trouverez ci-dessous les différents modèles de déploiement de Commerce Integration Framework pour les différentes offres d’AEM :

|  | aem sur site | aem Managed Services | cloud service AEM |
|-------------     |-----------|-----------|-----------|
| Comment déployer les outils de création CIF pour le serveur principal Magento | [Reportez-vous à CIF ](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) Connectorsupported on AEM 6.5 | [Reportez-vous à CIF ](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) Connectorsupported on AEM 6.5 | aem en tant que Cloud Service doit être configuré avec un module complémentaire CIF. Contactez votre représentant commercial pour plus de détails. |
| Comment déployer [CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) | Installation AEM package | Déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Le projet a été déplacé dans le [référentiel Git de Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) et le déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html) |

>[!NOTE]
>
>Pour obtenir de la documentation supplémentaire sur l&#39;utilisation du FIC avec le service AEM géré ou AEM sur site, consultez [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)

>[!NOTE]
>
>La version CIF Classic/Quickstart de Commerce Integration Framework peut être utilisée sur AEM offre sur site pour des utilisations très limitées. Cependant, il ne s’agit pas de la solution recommandée.

## Passage à AEM Commerce en tant que Cloud Service de On-premise et Managed Services {#moving-cif-cs}

Les clients qui passent d’une installation sur site AEM ou de Managed Services à une installation sur AEM en tant que Cloud Service doivent effectuer quelques ajustements mineurs sur le projet AEM.

Le premier ajustement, tel que décrit ci-dessus, est nécessaire pour le connecteur CIF. Le connecteur CIF est remplacé par le module complémentaire CIF déployé par Adobe. Par conséquent, n’installez pas CIF Connector sur AEM en tant que Cloud Service. En outre, l’utilisation avec le SDK Cloud AEM local n’est pas prise en charge, l’Adobe fournit également le module complémentaire CIF pour [le développement local](develop.md).

Deuxièmement, comprenez la [AEM Structure du projet](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) et les caractéristiques de l&#39;AEM en tant que Cloud Service. Adaptez la configuration de votre projet à l’AEM en tant que mise en page Cloud Service.
Les principales différences sont les suivantes :

* Le lot OSGI client GraphQL **ne doit plus** être inclus dans le projet AEM, il est déployé via le module complémentaire CIF
* Les configurations OSGI pour le client GraphQL et le service de données Graphql **ne doivent plus** être inclus dans le projet AEM

>[!TIP]
>
>Consultez le projet [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) sur GitHub. Ce projet fournit des profils Maven pour AEM en tant que Cloud Service et sur site, qui tiennent compte des différentes conditions-cadres.
