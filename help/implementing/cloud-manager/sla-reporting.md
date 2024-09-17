---
title: Rapports de contrat SLA
description: Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au contrat de niveau de service.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: c46b6df488722fe750e524ad2bb383f25bf00b0f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 10%

---


# Rapports de contrat SLA {#sla-reporting}

Découvrez comment voir les performances de votre environnement d’AEM de production par rapport au SLA contractuel (contrat de niveau de service).

## Affichage d’un rapport SLA {#introduction}

Les données du rapport SLA effectuent le suivi des mesures de performances pour deux niveaux de production : Niveau de création et Niveau Publish.

Le graphique linéaire d’une année sélectionnée inclut des points de données pour chaque mois de janvier à décembre. Les mesures suivantes sont suivies.

| Mesure suivie | Couleur de ligne | Description |
| --- | --- | --- |
| Niveau d’auteur – réel | Vert clair | Temps de disponibilité mesuré du niveau Auteur de production comptabilisant les incidents causés par les fournisseurs d’Adobe ou d’Adobe. |
| Niveau de création – contrat | bleu foncé | Le SLA défini dans votre contrat avec l’Adobe pour le niveau de création. |
| Niveau de publication – réel | Orange | Temps de disponibilité mesuré du niveau Publish de production, en tenant compte des incidents causés par les fournisseurs d’Adobe ou d’Adobe. |
| Niveau de publication – contrat | Rouge | SLA défini dans votre contrat avec Adobe pour le niveau Publish. |

**Pour afficher un rapport SLA :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, dans le panneau de navigation de gauche, cliquez sur **Rapports**.

1. Cliquez sur **Rapports SLA**.

   ![Graphique de ligne de rapport SLA](/help/implementing/cloud-manager/assets/cm-sla-report.png)

1. Cliquez sur l’année souhaitée pour afficher un graphique linéaire des données SLA.

1. (En option) Effectuez l’une des actions suivantes :

   * Placez le curseur sur un point de données du graphique linéaire pour afficher les valeurs spécifiques de ce point.
   * Sous l’année du graphique linéaire, cliquez sur l’icône Télécharger pour enregistrer un fichier image PNG du graphique linéaire.
   * Cliquez sur le nom d’une mesure pour afficher uniquement les données de cette mesure. Ou appuyez sur `Shift` sur le clavier lors de la sélection ou de la désélection d’un ou de plusieurs noms de mesure.

   ![Affichage de données détaillées](/help/implementing/cloud-manager/assets/cm-sla-download.png)

## Analyse des événements {#event-analysis}

La section **Analyse des événements** sous le graphique affiche l’ensemble des incidents qui se sont produits pour le programme au cours de l’année sélectionnée.

Chaque incident comporte une période, une cause et un ensemble de commentaires.

![Exemple d’analyse d’événement](assets/sla-reporting-c.png)

## Actualisation de l’intervalle des rapports SLA {#refresh}

Les rapports SLA vous donnent des informations sur les performances de votre environnement de production AEM et sont à jour, mais pas instantanés. La génération des rapports SLA se produit tous les mois et elle est générée pour les nouveaux programmes marqués comme `Production previous month`. Ce n&#39;est pas instantané. En raison de ce délai, tenez compte des points suivants lorsque vous passez en revue votre rapport SLA :

* Le SLA signalé est celui qui existait au début du mois, même si SLA a changé au cours de ce mois.
* S’il n’y avait pas de SLA au début du mois car le programme n’existait pas, le SLA qui existait à la date de création du programme s’applique.

## Aperçu des environnements {#preview}

L’environnement d’aperçu est conçu comme un outil permettant aux auteurs de contenu de vérifier l’expérience finale du contenu avant de le publier. En raison de cette fonctionnalité, les environnements d’aperçu ne sont pas conçus pour une haute disponibilité et n’ont pas de SLA associé.
