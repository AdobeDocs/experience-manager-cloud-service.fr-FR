---
title: Migration vers le module complémentaire CIF (Commerce Integration Framework) AEM
description: Comment migrer vers le module complémentaire CIF (Commerce Integration Framework) d’AEM à partir d’une ancienne version
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 21%

---

# Guide de migration pour le Experience Manager Cloud Service {#cif-migration}

Ce guide permet d’identifier les zones à mettre à jour pour la migration des Experience Manager Cloud Service.

## Module complémentaire CIF

Pour Experience Manager en tant que Cloud Service, le module complémentaire CIF est la seule solution d’intégration commerciale prise en charge pour Adobe Commerce et les solutions commerciales tierces. Le module complémentaire CIF est déployé automatiquement pour les clients sur Experience Manager en tant que Cloud Service, aucun déploiement manuel n’est nécessaire. Voir [Prise en main d’AEM Commerce as a Cloud Service](getting-started.md).

Pour prendre en charge les projets qui déploient l’Adobe CIF, indiquez [AEM les composants principaux CIF](https://github.com/adobe/aem-core-cif-components).

Le module complémentaire CIF est également disponible pour AEM 6.5 via le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Il est compatible et fournit les mêmes fonctionnalités que le module complémentaire CIF pour Experience Manager en tant que Cloud Service ; aucun ajustement n’est nécessaire.

Le CIF classique avec ses dépendances n’est plus disponible. Le code s’appuyant sur cette version de CIF à l’aide des API Java `com.adobe.cq.commerce.api` doit être adapté au module complémentaire CIF et à ses principes.

Le connecteur CIF précédemment disponible ne peut plus être installé. Le code reposant sur ce connecteur doit être adapté au module complémentaire CIF et à ses principes.

## Structure du projet

Découvrez la [AEM structure de projet](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr) et les caractéristiques d’AEM en tant que Cloud Service. Adaptez la configuration de votre projet à la disposition d’AEM as a Cloud Service.
Par rapport aux déploiements AEM 6.5, il existe deux différences principales :

* Le bundle OSGI du client GraphQL **ne doit plus** être inclus dans le projet AEM ; il est déployé via le module complémentaire CIF.
* Les configurations OSGI du client GraphQL et le service de données GraphQL **ne doivent plus** être inclus dans le projet AEM

>[!TIP]
>
>Extrayez le projet [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) sur GitHub. Ce projet fournit aux déploiements AEM as a Cloud Service et sur site des profils Maven qui tiennent compte des différentes conditions de framework.

## Catalogue de produits

L’import de données de catalogue de produits n’est plus pris en charge. L’utilisation du module complémentaire CIF permet aux demandes de produits et de catalogues de se faire sur demande par le biais d’appels en temps réel vers une solution de commerce externe. Accédez au chapitre Intégration pour en savoir plus sur l’intégration d’une solution de commerce.

>[!TIP]
>
>Si aucune API en temps réel n’est disponible, un cache de produit externe avec les API doit être utilisé pour l’intégration. Exemple [Magento open-source](https://magento.com/products/magento-open-source).

## Expériences du catalogue de produits avec rendu AEM

Si vous utilisez le plan directeur de catalogue avec CIF classique, vous devez mettre à jour le workflow du catalogue de produits. Le module complémentaire CIF effectue désormais le rendu à la volée des expériences de catalogue de produits à l’aide de modèles de catalogue AEM. Aucune réplication des données de produit ou des pages de produit n’est plus nécessaire.

## Données non mises en cache et interaction d’achat

Les requêtes côté client pour les données et interactions non mises en cache (par exemple, ajout au panier, recherche) doivent accéder directement au point de terminaison de commerce (solution de commerce ou couche d’intégration) via CDN/Dispatcher. Supprimez tous les appels pour lesquels AEM n’était qu’un proxy.
