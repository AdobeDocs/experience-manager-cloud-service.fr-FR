---
title: Modifications notables apportées à AEM Commerce as a Cloud Service
description: Modifications notables apportées à AEM Commerce as a Cloud Service par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 2934d0d8d3977bb7884bae9654ac26e9fa57b34f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---


# Modifications notables apportées à AEM Commerce as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Ce document met en évidence les différences importantes de fonctionnalité Commerce entre Commerce Integration Framework (CIF) pour On-premise, Adobe Managed Service et Experience Manager as a Cloud Service. Concernant les autres changements, consultez le document générique [Modifications apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :
* [Prise en charge de CIF Classic](#cif-classic)
* [Déploiement des outils de création CIF](#cif-tools)
* [Transition depuis On-Premise et Adobe Managed Service](#moving-cif-cs)

## Prise en charge de CIF Classic/Quickstart sur Experience Manager as a Cloud Service {#cif-classic}

Commerce Integration Framework Classic, qui incluait un importateur de produits pour importer et stocker des catalogues de produits dans Experience Manager, n’est plus disponible dans Experience Manager as a Cloud Service. L’utilisation de CIF Classic n’est pas prise en charge dans Experience Manager as a Cloud Service et les projets qui l’utilisent devront remplacer son implémentation par la version prise en charge, comme décrit dans [CIF dans Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/commerce/architecture/magento.html#overview).

## Déploiement de CIF {#deployment}

Vous trouverez ci-dessous les différents modèles de déploiement de Commerce Integration Framework pour les différentes offres d’AEM :

|  | AEM On-premise | AEM Managed Services | AEM Cloud Service |
|-------------     |-----------|-----------|-----------|
| Comment déployer les outils de création CIF pour le serveur principal Magento | [Reportez-vous au connecteur CIF](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) pris en charge sur AEM 6.5. | [Reportez-vous au connecteur CIF](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) pris en charge sur AEM 6.5. | AEM as a Cloud Service doit être provisionné avec un module complémentaire CIF. Contactez votre représentant commercial pour plus de détails. |
| Comment déployer le projet [CIF Venia](https://github.com/adobe/aem-cif-guides-venia) | Module d’installation AEM | Déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Projet déplacé dans le [référentiel Git de Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) et déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html) |

>[!NOTE]
>
>Pour obtenir de la documentation supplémentaire sur l’utilisation de CIF avec AEM Managed Service ou AEM On-premise, voir [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).

>[!NOTE]
>
>La version CIF Classic/Quickstart de Commerce Integration Framework peut être utilisée sur les offres AEM On-premise dans des cas d’utilisation très limités. Cependant, il ne s’agit pas de la solution recommandée.

## Passage à AEM Commerce as a Cloud Service à partir d’On-premise et de Managed Services {#moving-cif-cs}

Les clients qui passent d’une installation AEM On-Premise ou Managed Services à AEM as a Cloud Service doivent effectuer quelques ajustements mineurs sur le projet AEM.

Le premier ajustement, tel que décrit ci-dessus, est nécessaire au connecteur CIF. Le connecteur CIF est remplacé par le module complémentaire CIF déployé par Adobe. Par conséquent, ne l’installez pas sur AEM as a Cloud Service. En outre, l’utilisation avec le SDK AEM Cloud local n’est pas prise en charge ; Adobe fournit également le module complémentaire CIF pour le [développement local](develop.md).

Deuxièmement, ayez une compréhension de la [structure de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) et des caractéristiques d’AEM as a Cloud Service. Adaptez la configuration de votre projet à la disposition d’AEM as a Cloud Service.
Les principales différences sont ici les suivantes :

* Le bundle OSGI du client GraphQL **ne doit plus** être inclus dans le projet AEM ; il est déployé via le module complémentaire CIF.
* Les configurations OSGI du client GraphQL et le service de données GraphQL **ne doivent plus** être inclus dans le projet AEM

>[!TIP]
>
>Extrayez le projet [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) sur GitHub. Ce projet fournit aux déploiements AEM as a Cloud Service et sur site des profils Maven qui tiennent compte des différentes conditions de framework.
