---
title: Création de rapports de contrat SLA
description: Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: 90250c13c5074422e24186baf78f84c56c9e3c4f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 8%

---


# Création de rapports de contrat SLA {#sla-reporting}

Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).

## Présentation {#introduction}

Les données de rapport SLA sont disponibles pour chaque programme de production via la variable **Rapports** . Pour y accéder, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme dans l’écran .

1. Accédez au **Rapports** à partir de la **Présentation** page.

1. Cliquez sur l’année souhaitée pour afficher les données SLA sous forme de graphique.

![Exemple de graphique SLA](assets/sla-reporting-1.png)

Placez le curseur sur un point de données pour afficher les valeurs spécifiques de ce point.

![Affichage des données détaillées](assets/sla-reporting-b.png)

## Mesures SLA {#sla-metrics}

Le graphique de l’année sélectionnée comprend plusieurs jeux de données.

* **Contrat de niveau publication** - Il s’agit du contrat SLA défini dans votre contrat avec Adobe pour le niveau de publication.

* **Niveau de publication réel** - Il s’agit de la période de disponibilité mesurée du niveau publication de production comptabilisant les incidents causés par les fournisseurs d’Adobe ou d’Adobe.

* **Contrat de niveau auteur** - Il s’agit du contrat SLA défini dans votre contrat avec l’Adobe pour le niveau auteur.

* **Niveau de création réel** - Il s’agit de la période de disponibilité mesurée du niveau auteur de production prenant en compte les incidents causés par les fournisseurs d’Adobe ou d’Adobe.

## Analyse des événements {#event-analysis}

La variable **Analyse des événements** La section située sous le graphique affiche l’ensemble des incidents survenus pour le programme au cours de l’année sélectionnée.

Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Exemple d’analyse d’événement](assets/sla-reporting-c.png)
