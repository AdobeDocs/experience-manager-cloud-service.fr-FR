---
title: Création de rapports de contrat SLA
description: Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 7%

---


# Création de rapports de contrat SLA {#sla-reporting}

Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service (SLA).

## Présentation {#introduction}

Les données de rapport SLA sont disponibles pour chaque programme de production via l&#39;onglet **Rapports** . Pour y accéder, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. À l’aide du panneau de navigation latéral, accédez à l’onglet **Rapports** à partir de la page **Aperçu**.

1. Cliquez sur l’année souhaitée pour afficher les données SLA sous forme de graphique.

![Exemple de graphique SLA](assets/sla-reporting-1.png)

Placez le curseur sur un point de données pour afficher les valeurs spécifiques de ce point.

![Affichage de données détaillées](assets/sla-reporting-b.png)

## Mesures SLA {#sla-metrics}

Le graphique de l’année sélectionnée comprend plusieurs jeux de données.

* **Contrat de niveau Publish** : il s’agit du contrat SLA défini dans votre contrat avec Adobe pour le niveau de publication.

* **Niveau Publish réel** : il s’agit de la période de disponibilité mesurée du niveau publication de production comptabilisant les incidents provoqués par les fournisseurs d’Adobe ou d’Adobe.

* **Contrat de niveau auteur** : il s’agit du contrat SLA défini dans votre contrat avec l’Adobe pour le niveau auteur.

* **Niveau de création réel** : il s’agit de la période de disponibilité mesurée du niveau de création de production qui tient compte des incidents causés par les fournisseurs d’Adobe ou d’Adobe.

## Analyse des événements {#event-analysis}

La section **Analyse des événements** sous le graphique affiche l’ensemble des incidents qui se sont produits pour le programme au cours de l’année sélectionnée.

Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Exemple d’analyse d’événement](assets/sla-reporting-c.png)

## Actualiser l’intervalle {#refresh}

Les rapports de contrat SLA vous donnent des informations sur les performances de votre environnement de production AEM et sont à jour, mais pas instantanés. La génération des rapports SLA a lieu tous les mois et elle est générée pour les nouveaux programmes marqués comme Production le mois précédent. Ce n&#39;est pas instantané. En raison de ce délai, tenez compte des points suivants lorsque vous passez en revue votre rapport SLA :

* Le contrat de niveau de service signalé sera celui qui existait au début du mois, même si le contrat a changé au cours de ce mois.
* Si aucun contrat SLA n’existait au début du mois car le programme n’existait pas alors, le contrat SLA qui existait à la date de création du programme s’applique.

## Aperçu des environnements {#preview}

L’environnement d’aperçu est conçu comme un outil permettant aux auteurs de contenu de vérifier l’expérience finale du contenu avant de le publier. Pour cette raison, les environnements d’aperçu ne sont pas conçus avec une haute disponibilité et n’ont pas de contrat SLA associé.
