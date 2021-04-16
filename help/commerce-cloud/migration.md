---
title: Migration vers le module complémentaire AEM Commerce Integration Framework (CIF)
description: Comment migrer vers le module complémentaire AEM Commerce Integration Framework (CIF) à partir d’une ancienne version
translation-type: tm+mt
source-git-commit: cda25048e171f6aacd5349706ad4192965e703db
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 22%

---

# Guide de migration pour le Experience Manager Cloud Service {#cif-migration}

Ce guide vous aide à identifier les zones à mettre à jour pour la migration des Experience Manager Cloud Service.

## Module complémentaire CIF

Pour Experience Manager en tant que Cloud Service, le module complémentaire CIF est la seule solution d&#39;intégration commerciale prise en charge pour les solutions de commerce Adobe Commerce et tierces. Le module complémentaire CIF est déployé automatiquement pour les clients sur Experience Manager en tant que Cloud Service, aucun déploiement manuel n’est nécessaire. Voir [Prise en main de AEM Commerce en tant que Cloud Service](getting-started.md).

Pour soutenir les projets de déploiement de l&#39;Adobe CIF, fournissez [AEM Composants principaux CIF](https://github.com/adobe/aem-core-cif-components).

Le module complémentaire CIF est également disponible pour AEM 6.5 via le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Il est compatible et offre les mêmes fonctionnalités que le module complémentaire CIF pour Experience Manager en tant que Cloud Service - aucun réglage n&#39;est nécessaire.

CIF classique avec ses dépendances n&#39;est plus disponible. Le code s’appuyant sur cette version CIF utilisant les API Java `com.adobe.cq.commerce.api` doit être ajusté au module complémentaire CIF et à ses principes.

Le connecteur CIF précédemment disponible ne peut plus être installé. Le code reposant sur ce connecteur doit être ajusté au module complémentaire CIF et à ses principes.

## Structure du projet

Découvrez la [AEM Structure du projet](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) et les caractéristiques de l&#39;AEM en tant que Cloud Service. Adaptez la configuration de votre projet à la disposition d’AEM as a Cloud Service.
Par rapport à AEM 6,5 déploiements, il y a deux différences principales :

* Le bundle OSGI du client GraphQL **ne doit plus** être inclus dans le projet AEM ; il est déployé via le module complémentaire CIF.
* Les configurations OSGI du client GraphQL et le service de données GraphQL **ne doivent plus** être inclus dans le projet AEM

>[!TIP]
>
>Extrayez le projet [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) sur GitHub. Ce projet fournit aux déploiements AEM as a Cloud Service et sur site des profils Maven qui tiennent compte des différentes conditions de framework.

## Catalogue de produits

L’importation de données de catalogue de produits n’est plus prise en charge. L&#39;utilisation des identifiants CIF complémentaires produit et catalogue demande des appels en temps réel à une solution de commerce externe. Accédez au chapitre Intégration pour en savoir plus sur l&#39;intégration d&#39;une solution commerciale.

>[!TIP]
>
>Si aucune API en temps réel n’est disponible, un cache de produit externe avec des API doit être utilisé pour l’intégration. Exemple [Magento open-source](https://magento.com/products/magento-open-source).

## Expériences de catalogue de produits avec rendu AEM

Si vous utilisez le modèle de catalogue avec CIF classique, vous devez mettre à jour le processus du catalogue de produits. Le module complémentaire CIF effectue désormais le rendu en temps réel des expériences de catalogue de produits à l’aide de modèles de catalogue AEM. Aucune réplication des données de produit ou des pages de produits n’est plus requise.

## Interaction entre les données et les achats non mises en cache

Les demandes côté client pour des données et interactions non mises en cache (par exemple, ajouts au panier, recherche) doivent être envoyées directement au point de terminaison du commerce (solution commerciale ou couche d’intégration) via CDN/Répartiteur. Supprimez les appels pour lesquels AEM n&#39;était qu&#39;un proxy.
