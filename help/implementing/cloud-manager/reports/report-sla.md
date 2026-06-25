---
title: Rapports de contrat SLA
description: Découvrez comment évaluer les performances de votre environnement de production AEM par rapport au Service level agreement sous-traité.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 884f991bbc067b8c2d628600c18a89e5950df17c
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 9%

---


# Rapports SLA {#sla-reporting}

Découvrez comment évaluer les performances de votre environnement de production AEM par rapport au contrat SLA (Service level agreement).

## Affichage d’un rapport SLA {#introduction}

Les données de rapport SLA effectuent le suivi des mesures de performances pour deux niveaux de production : niveau création et niveau publication.

Le graphique linéaire d’une année sélectionnée comprend des points de données pour chaque mois, de janvier à décembre. Les mesures suivantes sont suivies.

| Mesure suivie | Couleur de ligne | Description |
| --- | --- | --- |
| Niveau d’auteur – réel | Vert clair | Temps de disponibilité mesuré du niveau de création de production comptabilisant les incidents causés par les fournisseurs Adobe ou Adobe. |
| Niveau de création – contrat | Bleu foncé | SLA défini dans votre contrat avec Adobe pour le niveau de création. |
| Niveau de publication – réel | Orange | Temps de disponibilité mesuré du niveau de publication de production, en tenant compte des incidents causés par les fournisseurs Adobe ou Adobe. |
| Niveau de publication – contrat | Rouge | SLA défini dans votre contrat avec Adobe pour le niveau de publication. |

**Pour afficher un rapport SLA, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, dans le menu de gauche, cliquez sur **Rapports**.

1. Cliquez sur **Rapports**.

   ![Graphique linéaire du rapport &#x200B;](/help/implementing/cloud-manager/reports/assets/cm-sla-report2.png)

1. Cliquez sur l’année souhaitée pour afficher un graphique linéaire des données SLA.

1. (En option) Effectuez l’une des actions suivantes :

   * Pour afficher les valeurs spécifiques d’un point de données, placez le curseur sur celui-ci dans le graphique linéaire.
   * Sous l’année du graphique linéaire, cliquez sur l’icône **Télécharger** pour enregistrer un fichier image PNG du graphique linéaire.
   * Cliquez sur le nom d’une mesure pour afficher ses données. `Shift` Vous pouvez également appuyer sur le clavier et le maintenir enfoncé tout en sélectionnant ou en désactivant un ou plusieurs noms de mesures.

## Analyse des événements {#event-analysis}

La section **Analyse des événements** située sous le graphique indique l’ensemble des incidents survenus pour le programme au cours de l’année sélectionnée.

Chacun des incidents comporte une période, une cause et un ensemble de commentaires.

![Exemple d’analyse des événements](/help/implementing/cloud-manager/reports/assets/sla-reporting-c.png)

## Intervalle d’actualisation des rapports SLA {#refresh}

Les rapports SLA fournissent des informations sur les performances de votre environnement de production AEM. Ils sont à jour, mais pas instantanés. La génération du rapport SLA a lieu tous les mois et est générée pour les nouveaux programmes marqués comme `Production previous month`. Ce n&#39;est pas instantané. En raison de ce retard, gardez à l’esprit les points suivants lorsque vous examinerez votre rapport SLA :

* Le SLA signalé est celui qui existait au début du mois, même si SLA a changé pendant ce mois.
* S’il n’y avait pas de SLA au début du mois parce que le programme n’existait pas, le SLA qui existait à la date de création du programme s’applique.

## Environnements de prévisualisation {#preview}

L’environnement de prévisualisation est conçu comme un outil permettant aux personnes en charge de la création de contenu de réviser le contenu avant sa publication. En raison de cette fonctionnalité, les environnements de prévisualisation ne sont pas conçus avec une haute disponibilité et ne disposent pas d’un SLA associé.

