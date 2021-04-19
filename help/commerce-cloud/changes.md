---
title: Modifications notables du module complémentaire CIF (Commerce Integration Framework)
description: Changements notables du cadre d’intégration commerciale (CIF) par rapport aux anciennes versions de CIF.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
translation-type: tm+mt
source-git-commit: 7a52e4b62f5a18f9c68e5afb0d464bd11be732d2
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 15%

---

# Modifications notables de l&#39;Ajoute du cadre d&#39;intégration commerciale (CIF){#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Pour en savoir plus sur ces fonctionnalités, veuillez suivre le lien [modifications apportées au Experience Manager en tant que Cloud Service](/help/release-notes/aem-cloud-changes.md).

Ce document souligne les différences importantes entre le module complémentaire du Commerce Integration Framework (CIF) et les anciennes versions de CIF, principalement connues sous le nom de CIF Classic (Quickstart) et CIF Open Source.

## Installation et mises à jour

Le module complémentaire AEM CIF est installé via Cloud Manager. L&#39;installation nécessite un crédit CIF, sauf pour les sandbox où CIF peut être installé sans crédits. Les crédits sont reçus automatiquement par l&#39;intermédiaire de l&#39;approvisionnement du module complémentaire CIF dans votre contrat AEM.

Le module complémentaire est automatiquement mis à jour dans le cadre de l’AEM ordinaire en tant que Cloud Service.

**Versions CIF précédentes**

* CIF Classic : Aucune installation n&#39;était nécessaire, CIF faisait partie de Quickstart. Les mises à jour CIF faisaient partie des mises à jour régulières des AEM ou Service Pack.
* CIF Source ouverte pour l&#39;AEM sur site : Installation via GitHub. Les mises à jour faisaient partie du travail manuel de mise à jour/maintenance.
* CIF Open source pour AEM Adobe Managed Services : Installation via Customer Success Manager. Les mises à jour faisaient partie du travail manuel de mise à jour/maintenance.

## Configuration du point de terminaison

Le point de terminaison est configuré et mis à jour via l’interface utilisateur de Cloud Manager ou son interface de ligne de commande.

**Versions CIF précédentes**

* CIF Classic : Via la configuration OSGi dans AEM
* CIF Open source : Via le navigateur de configuration CIF

## Déploiement du projet CIF Venia

Projet disponible dans [le référentiel Git de Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) et déploiement effectué via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html)

**Versions CIF précédentes**

* CIF Classic : Via l’installation AEM package
* CIF Open source : Via [Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)

## Données du catalogue de produits

Les données du catalogue de produits sont demandées à la demande via des appels en temps réel vers un point de terminaison externe qui prend en charge les API GraphQL requises. Ces API prennent en charge l’accès aux données actives ou d’évaluation à une date donnée. Aucune réplication n&#39;est nécessaire.

**Versions CIF précédentes**

* CIF Classic : Les données des produits en direct et intermédiaires sont importées et conservées dans le JCR sur AEM Author par le biais d’une importation de produits complète ou delta. Les données des produits en direct sont répliquées dans AEM Publish.

## Expériences de catalogue de produits avec rendu AEM

AEM effectue le rendu des expériences de catalogue de produits à la volée à l’aide de modèles de catalogue AEM qui ont été affectés à des produits et des catégories. Aucune réplication n&#39;est nécessaire.

**Versions CIF précédentes**

* CIF Classic : AEM Author crée une page d’AEM pour chaque catégorie/produit à l’aide de l’outil de schéma directeur du catalogue. Ces pages sont répliquées dans AEM Publish.

>[!NOTE]
>
>Pour obtenir de la documentation supplémentaire sur l’utilisation de CIF avec AEM Managed Service ou AEM On-premise, voir [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
