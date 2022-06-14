---
title: Création de rapports de contrat SLA
description: Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 9%

---


# Création de rapports de contrat SLA {#sla-reporting}

Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).

## Présentation  {#introduction}

Les données de rapport SLA sont disponibles pour chaque programme de production via la variable **Rapports** . Pour y accéder, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Rapports** à partir de l’onglet **Présentation** page.

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

Le **Analyse des événements** La section située sous le graphique affiche l’ensemble des incidents survenus pour le programme au cours de l’année sélectionnée.

Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Exemple d’analyse d’événement](assets/sla-reporting-c.png)
