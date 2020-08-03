---
title: Modifications notables apportées à AEM Commerce en tant que Cloud Service
description: Changements notables apportés à AEM Commerce en tant que Cloud Service par rapport à l'Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: df6f679b70a7cc70e4f76612c0a72a31443cd1b8
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 13%

---


# Notable changes to AEM Commerce as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Ce document met en évidence les différences importantes entre le cadre d&#39;intégration commerciale (CIF) pour les services sur site, les services gérés par Adobe et les Experience Manager en tant que Cloud Service. Concernant les autres changements, consultez le document générique [Modifications apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :
* [Prise en charge de CIF Classic](#cif-classic)
* [Déploiement des outils de création CIF](#cif-tools)
* [Passage d&#39;un service géré sur site et par Adobe](#moving-cif-cs)

## Prise en charge de CIF Classic/Quickstart en tant que Cloud Service {#cif-classic}

Le cadre d’intégration du commerce classique qui incluait un importateur de produits pour importer et stocker des catalogues de produits en Experience Manager n’est plus disponible en tant que Cloud Service dans Experience Manager. L’utilisation de CIF classique n’est pas prise en charge en Experience Manager en tant que Cloud Service et les projets utilisant CIF classique devront remplacer l’implémentation CIF classique par la version prise en charge, comme décrit dans [CIF sur Experience Manager en tant que Cloud Service.](https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.en/blob/cif/help/commerce-cloud/architecture.md)

## Déploiement du FIC {#deployment}

Vous trouverez ci-dessous les différents modèles de déploiement de Commerce Integration Framework pour les différentes offres d’AEM :

|  | AEM sur site | AEM Managed Services | Cloud Service AEM |
|-------------     |-----------|-----------|-----------|
| Comment déployer les outils de création CIF pour le serveur principal Magento | [Reportez-vous à CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) pris en charge sur AEM 6.5. | [Reportez-vous à CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) pris en charge sur AEM 6.5. | AEM en tant que Cloud Service doit être configuré avec un module complémentaire CIF. Contactez votre représentant commercial pour plus de détails. |
| Comment déployer [CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) | Installation AEM package | Déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Projet déplacé dans le référentiel [Git de](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) Cloud Manager et déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html) |

>[!NNote]
>
>La version CIF Classic/Quickstart de Commerce Integration Framework peut être utilisée sur AEM offre sur site pour des utilisations très limitées. Cependant, il ne s’agit pas de la solution recommandée.

## Passage à AEM Commerce en tant que Cloud Service de On-premise et Managed Services {#moving-cif-cs}

Les clients qui passent d’une installation sur site AEM ou de Managed Services à une installation sur AEM en tant que Cloud Service doivent effectuer quelques ajustements mineurs sur le projet AEM.

Le premier ajustement, tel que décrit ci-dessus, est nécessaire pour le connecteur CIF. Le connecteur CIF est remplacé par le module complémentaire CIF déployé par Adobe. Par conséquent, n’installez pas CIF Connector sur AEM en tant que Cloud Service. En outre, l’utilisation avec le SDK Cloud AEM local n’est pas prise en charge, l’Adobe fournit également le module complémentaire CIF pour le développement [](develop.md)local.

Deuxièmement, comprendre la structure [](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) AEM projet et les caractéristiques de l&#39;AEM en tant que Cloud Service. Adaptez la configuration de votre projet à l’AEM en tant que mise en page Cloud Service.
Les principales différences sont les suivantes :

* Le lot OSGI client GraphQL **ne doit plus** être inclus dans le projet AEM, il est déployé via le module complémentaire CIF.
* Les configurations OSGI pour le client GraphQL et le service de données Graphql ne **doivent plus** être incluses dans le projet AEM

>[!Tip]
>
>Découvrez le projet [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) sur GitHub. Ce projet fournit des profils Maven pour AEM en tant que Cloud Service et sur site, qui tiennent compte des différentes conditions-cadres.
