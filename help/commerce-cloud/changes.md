---
title: Modifications notables apportées au module complémentaire CIF (Commerce Integration Framework)
description: Modifications notables de Commerce Integration Framework (CIF) par rapport aux anciennes versions de CIF.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
source-git-commit: 6c9a44940ea9e52bd27a233c7aa24e320a24076c
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 79%

---

# Modifications notables apportées au module complémentaire CIF (Commerce Integration Framework){#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion de vos projets AEM. Pour en savoir plus sur ces fonctionnalités, suivez le lien correspondant aux [modifications apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Ce document met en évidence les différences importantes entre le module complémentaire CIF (Commerce Integration Framework) et les anciennes versions de CIF, connues sous le nom de CIF Classic (Quickstart) et CIF Open Source.

## Installation et mises à jour

Le module complémentaire CIF d’AEM est installé à l’aide de Cloud Manager. L’installation nécessite un crédit CIF, à l’exception des sandbox dans lesquels CIF peut être installé sans crédits. Les crédits sont automatiquement reçus via la mise en service du module complémentaire CIF dans votre contrat AEM.

Le module complémentaire est automatiquement mis à jour dans le cadre de la mise à jour as a Cloud Service régulière AEM.

**Versions CIF précédentes**

* CIF Classic : aucune installation n’était nécessaire, CIF faisait partie de la version Quickstart. Les mises à jour CIF faisaient partie des mises à jour régulières d’AEM ou de service pack.
* CIF Open-source for AEM On-premises : installation via GitHub. Les mises à jour faisaient partie des opérations de mise à jour manuelle/de maintenance.
* CIF Open Source pour AEM Adobe Managed Services : Installation par l’intermédiaire de l’équipe du compte d’Adobe. Les mises à jour faisaient partie des opérations de mise à jour manuelle/de maintenance.

## Configuration du point d’entrée

Le point d’entrée est configuré et mis à jour via l’interface utilisateur de Cloud Manager ou par le biais de son interface de ligne de commande.

**Versions CIF précédentes**

* CIF Classic : via la configuration OSGi dans AEM
* CIF Open Source : via l’explorateur de configurations CIF

## Déploiement du projet CIF Venia

Projet disponible dans le [référentiel Git de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/integrating-with-git.html) et déploiement effectué via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=fr)

**Versions CIF précédentes**

* CIF Classic : Au moyen de l’installation AEM package
* CIF Open Source : via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=fr)

## Données du catalogue de produits

Les données du catalogue de produits sont accessibles à la demande par le biais d’appels en temps réel vers un point d’entrée externe qui prend en charge les API GraphQL requises. Ces API autorisent l’accès aux données actives ou intermédiaires à n’importe quelle date. Aucune réplication n’est nécessaire.

**Versions CIF précédentes**

* CIF Classic : les données de produits actives et intermédiaires sont importées et conservées dans JCR sur AEM Author grâce à des importations de produits complètes ou par différence. Les données de produits actives sont répliquées vers le service de publication AEM.

## Expériences de catalogue de produits avec rendu dans AEM

AEM effectue le rendu à la volée des expériences de catalogue de produits à l’aide de modèles de catalogues AEM préalablement affectés aux produits et aux catégories. Aucune réplication n’est nécessaire.

**Versions CIF précédentes**

* CIF Classic : AEM Author crée une page AEM pour chaque catégorie/produit à l’aide de l’outil de plan directeur de catalogue. Ces pages sont répliquées vers le service de publication AEM

>[!NOTE]
>
>Pour obtenir de la documentation supplémentaire sur l’utilisation de CIF avec AEM Managed Service ou AEM On-premise, voir [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
