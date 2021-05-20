---
title: Modifications notables du module complémentaire CIF (Commerce Integration Framework)
description: Modifications notables de Commerce Integration Framework (CIF) par rapport aux anciennes versions de CIF.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
source-git-commit: 7a52e4b62f5a18f9c68e5afb0d464bd11be732d2
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 15%

---

# Modifications notables apportées au module complémentaire CIF (Commerce Integration Framework){#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Pour en savoir plus sur ces fonctionnalités, suivez le lien correspondant aux [modifications apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Ce document met en évidence les différences importantes entre le module complémentaire CIF (Commerce Integration Framework) et les anciennes versions de CIF, connues principalement sous le nom de CIF Classic (Quickstart) et CIF Open Source.

## Installation et mises à jour

Le module complémentaire CIF AEM est installé via Cloud Manager. L’installation nécessite un crédit CIF, à l’exception des environnements de test dans lesquels CIF peut être installé sans crédits. Les crédits sont automatiquement reçus via la mise en service du module complémentaire CIF dans votre contrat AEM.

Le module complémentaire est automatiquement mis à jour dans le cadre de l’AEM standard en tant que Cloud Service.

**Versions CIF précédentes**

* CIF Classic : Aucune installation n’était nécessaire, CIF faisait partie du Quickstart. Les mises à jour CIF faisaient partie des mises à jour régulières d’AEM ou de Service Pack.
* CIF Open Source pour AEM On-Premise : Installation via GitHub. Les mises à jour faisaient partie du travail manuel de mise à jour/maintenance.
* CIF Open Source pour AEM Adobe Managed Services : Installation via Customer Success Manager. Les mises à jour faisaient partie du travail manuel de mise à jour/maintenance.

## Configuration du point d’entrée

Le point de terminaison est configuré et mis à jour via l’interface utilisateur de Cloud Manager ou via son interface de ligne de commande.

**Versions CIF précédentes**

* CIF Classic : Via la configuration OSGi dans AEM
* CIF Open Source : Via le navigateur de configuration CIF

## Déploiement du projet CIF Venia

Projet disponible dans le [référentiel Git de Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) et déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html)

**Versions CIF précédentes**

* CIF Classic : Via l’installation AEM package
* CIF Open Source : Via [Cloud Manager](https://docs.adobe.com/content/help/fr/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)

## Données du catalogue de produits

Les données du catalogue de produits sont demandées à la demande via des appels en temps réel vers un point de terminaison externe qui prend en charge les API GraphQL requises. Ces API prennent en charge l’accès aux données actives ou intermédiaires à n’importe quelle date donnée. Aucune réplication n’est nécessaire.

**Versions CIF précédentes**

* CIF Classic : Les données des produits en direct et intermédiaires sont importées et conservées dans JCR sur l’auteur AEM via l’importation de produits complète ou delta. Les données de produit en direct sont répliquées vers AEM Publish.

## Expériences du catalogue de produits avec rendu AEM

AEM effectue le rendu à la volée des expériences de catalogue de produits à l’aide AEM modèles de catalogue qui ont été affectés aux produits et aux catégories. Aucune réplication n’est nécessaire.

**Versions CIF précédentes**

* CIF Classic : AEM Author crée une page d’AEM pour chaque catégorie/produit à l’aide de l’outil de plan directeur de catalogue. Ces pages sont répliquées vers AEM Publish.

>[!NOTE]
>
>Pour obtenir de la documentation supplémentaire sur l’utilisation de CIF avec AEM Managed Service ou AEM On-premise, voir [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
