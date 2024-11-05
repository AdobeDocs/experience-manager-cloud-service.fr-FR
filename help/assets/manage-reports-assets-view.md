---
title: Gérer les rapports dans la vue Assets
description: Accédez aux données de la section des rapports de la vue Assets pour évaluer l’utilisation des produits et des fonctionnalités et déduire des informations sur les mesures de succès clés.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
feature: Asset Insights, Asset Reports
role: User, Admin, Developer
source-git-commit: 5ff36490c4d9a6f61255ad06ffab984f18c1823b
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 31%

---

# Gérer les rapports {#manage-reports}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les rapports de ressources offrent aux administrateurs une visibilité sur l’activité de l’environnement Vue Adobe Experience Manager Assets. Ces données fournissent des informations utiles sur la façon dont les utilisateurs interagissent avec le contenu et le produit. Tous les utilisateurs et utilisatrices peuvent accéder au tableau de bord Insights et ceux qui sont affectés au profil de produit Administrateurs et administratrices peuvent créer des rapports définis par l’utilisateur ou l’utilisatrice.

## Accéder aux rapports {#access-reports}

Tous les utilisateurs et toutes les utilisatrices affectés au profil de produit Administration de la vue Assets peuvent accéder au tableau de bord des Insights ou créer des rapports définis par l’utilisateur dans la vue Assets.

Pour accéder aux rapports, accédez à **[!UICONTROL Rapports]** sous **[!UICONTROL Paramètres]**.

![Rapports.](assets/reports.png)

<!--
In the **[!UICONTROL Reports]** screen, various components are shown in the tabular format which includes the following:

* **Title**: Title of the report
* **Type**: Determines whether the report is uploaded or downloaded to the repository
* **Description**: Provide details of the report that was given during uploading/downloading the report
* **Status**: Determines whether the report is completed, under progress, or deleted.
* **Author**: Provides email of the author who has uploaded/downloaded the report.
* **Created**: Gives information of the date when the report was generated.
-->

## Créer un rapport {#create-report}

L’environnement de vue AEM Assets offre des fonctionnalités de création de rapports complètes par le biais du tableau de bord Rapports. Cette fonctionnalité permet aux utilisateurs de générer et télécharger des rapports CSV détaillant les téléchargements et les téléchargements de ressources dans des périodes spécifiées allant d’une fois unique à des intervalles quotidiens, hebdomadaires, mensuels ou annuels.

**Pour créer un rapport :**

1. Accédez à **Reports** et cliquez sur **Créer un rapport** (dans le coin supérieur droit). La boîte de dialogue **créer un rapport** affiche les champs suivants :
   ![create-report](/help/assets/assets/executed-reports1.svg)

   **Dans l’onglet Configuration :**

   1. **Type de rapport :** Choisissez entre le type de téléchargement et de téléchargement.
   1. **Titre :** Ajoutez un titre au rapport.
   1. **Description :** Ajoutez une description facultative au rapport.
   1. **Sélectionner le chemin d’accès au dossier :** Sélectionnez un chemin d’accès au dossier pour générer le rapport des ressources chargées et téléchargées dans ce dossier spécifique. Par exemple, si vous avez besoin du rapport des ressources chargées dans un dossier, indiquez le chemin d’accès à ce dossier.
   1. **Sélectionner un intervalle de dates :** Sélectionnez la période pour afficher l’activité de téléchargement ou de téléchargement dans le dossier.
   <br>

   >[!NOTE]
   >
   > La vue Assets convertit tous les fuseaux horaires locaux en temps universel coordonné (UTC).

   **Onglet Colonnes :** Sélectionnez les noms de colonne à afficher dans le rapport. Le tableau suivant explique l’utilisation de toutes les colonnes :

   <table>
    <tbody>
     <tr>
      <th><strong>Nom de la colonne</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Type de rapport</strong></th>
     </tr>
     <tr>
      <td>Titre</td>
      <td>Titre de la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Chemin d’accès</td>
      <td>Chemin d’accès au dossier qui contient la ressource dans la vue Assets.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Type MIME</td>
      <td>Type MIME de la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Taille</td>
      <td>Taille de la ressource en octets.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Téléchargé par</td>
      <td>ID d’e-mail de l’utilisateur qui a téléchargé la ressource.</td>
      <td>Télécharger</td>
     </tr>
     <tr>
      <td>Date de téléchargement</td>
      <td>Date à laquelle la ressource a été téléchargée.</td>
      <td>Télécharger</td>
     </tr>
     <tr>
      <td>Créateur ou créatrice</td>
      <td>Le créateur ou la créatrice de la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Date de création</td>
      <td>Date à laquelle la ressource a été chargée dans la vue Assets.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Date de modification</td>
      <td>Date de dernière modification de la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Expiré</td>
      <td>Statut d’expiration de la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Téléchargé par « Nom d’utilisateur »</td>
      <td>Nom de l’utilisateur qui a téléchargé la ressource.</td>
      <td>Télécharger</td>
     </tr>           
    </tbody>
   </table>

## Afficher et télécharger un rapport existant {#View-and-download-existing-report}

Les rapports existants s’affichent sous l’onglet **Rapports exécutés** . Cliquez sur **Rapports** et sélectionnez **Rapports exécutés** pour afficher tous les rapports créés avec l’état **terminé**, indiquant qu’ils sont prêts à être téléchargés. Pour télécharger le rapport au format CSV ou le supprimer, sélectionnez la ligne du rapport. Sélectionnez ensuite **Télécharger CSV** ou **Supprimer**.
![afficher et télécharger des rapports existants](/help/assets/assets/view-download-existing-report.png)

## Planification d’un rapport {#schedule-report}

Dans l’interface utilisateur de la vue AEM Assets, la fonction **Planification du rapport** configure une génération automatique de rapports à des intervalles futurs spécifiés, par exemple tous les jours, toutes les semaines, tous les mois ou tous les ans. Cette fonctionnalité permet de rationaliser les besoins de création de rapports récurrents et d’assurer des mises à jour opportunes des données. Pendant que **Créer un rapport** génère des rapports pour les dates antérieures. Les rapports terminés sont répertoriés sous **Rapports exécutés** et les rapports à venir se trouvent sous ****.

Pour planifier un rapport, procédez comme suit :

1. Cliquez sur Rapports dans le volet de gauche, puis sur Créer un rapport (en haut à droite).
1. La boîte de dialogue du rapport affiche les informations suivantes :
   1. **Type de rapport :** Choisissez entre le type de téléchargement et de téléchargement.
   1. **Titre :** Ajoutez un titre au rapport.
   1. **Description** : ajoutez une description facultative au rapport.
   1. **Sélectionner le chemin d’accès au dossier :** Sélectionnez un chemin d’accès au dossier pour générer un rapport pour les ressources qui seront chargées ou téléchargées à partir de ce dossier spécifique à l’avenir.
   1. Basculez de **Planification du rapport :** Basculez pour planifier le rapport pour une fois ultérieure ou pour son occurrence répétée.
      ![rapport de planification](/help/assets/assets/schedule-reports1.svg)

   1. **Choisir la fréquence :** Spécifiez l’intervalle de génération du rapport (par exemple, quotidien, hebdomadaire, mensuel, annuel ou une fois) et définissez la date et l’heure d’exécution du rapport ainsi que la date de fin de la périodicité. Pour un rapport unique, sélectionnez la période du rapport sur le type d’activité sélectionné dans l’environnement AEM. Par exemple, si vous avez besoin d’un rapport sur les ressources téléchargées du 10e au 29e (dates futures) d’un mois spécifique, sélectionnez ces dates dans le champ **Sélectionner l’intervalle de dates** .

   >[!NOTE]
   >
   > La vue Assets convertit tous les fuseaux horaires locaux en temps universel coordonné (UTC).

## Affichage des rapports planifiés {#view-scheduled-reports}

Les rapports planifiés s’affichent sous l’onglet **Rapports planifiés** d’une manière systématique organisée. Tous les rapports terminés pour chaque rapport planifié sont stockés dans un seul dossier de rapports. Cliquez sur ![développer la réduction](/help/assets/assets/expand-icon1.svg) pour afficher les rapports terminés. Par exemple, si vous avez planifié un rapport quotidien, tous les rapports terminés sont regroupés dans un seul dossier. Cette organisation simplifie la navigation et la découverte des rapports. Pour afficher les rapports planifiés, cliquez sur **Rapports**, puis sur **Rapports planifiés**. Tous les rapports planifiés s’affichent, avec leur état comme étant en cours ou terminé. Les rapports terminés sont prêts à être téléchargés.\
![rapport planifié](/help/assets/assets/scheduled-reports-tab.png)

## Modification et annulation de rapports planifiés {#edit-cancel-scheduled-reports}

1. Accédez à l’onglet **Rapports programmés** .
1. Sélectionnez la ligne du rapport.
1. Cliquez sur **Modifier**.
1. Cliquez sur **Annuler le planning**, puis sur **Confirmer** pour annuler le rapport planifié. Pour les rapports annulés, la prochaine exécution devient vide et l’état est annulé.
   ![modifier et annuler le rapport planifié](/help/assets/assets/cancel-edit-scheduled-reports.png)

### Reprendre le planning {#resume-schedule}

Pour reprendre la planification annulée, sélectionnez la ligne du rapport et cliquez sur **Reprendre la planification**. Lors de la reprise, les entrées d’exécution suivantes s’affichent à nouveau et l’état s’affiche en cours.
![Reprendre la planification](/help/assets/assets/resume-schedule.png)

>[!NOTE]
>
> Si vous reprenez un rapport annulé avant la date de fin planifiée, les rapports de la date d’annulation à la date de reprise sont automatiquement générés.

## Afficher les insights {#view-live-statistics}

La vue Assets vous permet d’afficher des données en temps réel pour votre environnement Assets à l’aide du tableau de bord Insights. Vous pouvez afficher les mesures d’événement en temps réel au cours des 30 derniers jours ou au cours des 12 derniers mois.

<!--![Toolbar options when you select an asset](assets/assets-view-live-statistics.png)-->

Cliquez sur les **[!UICONTROL Insights]** disponibles dans le volet de navigation de gauche pour afficher les graphiques générés automatiquement suivants :

* **Téléchargements** : nombre de ressources téléchargées à partir de l’environnement d’affichage Assets au cours des 30 ou 12 derniers jours représentés à l’aide d’un graphique linéaire.
  ![insights-downloads](/help/assets/assets/insights-downloads2341.svg)

* **Téléchargements** : nombre de ressources chargées dans l’environnement d’affichage Assets au cours des 30 ou 12 derniers jours représentés à l’aide d’un graphique linéaire.
  ![insights-uploads](/help/assets/assets/insights-uplods2.svg)
  <!--* **Asset Count by Size**: The division of count of assets based on their range of various sizes from 0 MB to 100 GB.-->

* **Utilisation du stockage** : utilisation du stockage, en octets, pour l’environnement de vue Assets représenté à l’aide d’un graphique à barres.
  ![insights-uploads](/help/assets/assets/insights-storage-usage1.svg)
  <!--* **Delivery**: The graph depicts the count of assets as the delivery dates.-->

<!--* **Asset Count by Asset Type**: Represents count of various MIME types of the available assets. For example, application/zip, image/png, video/mp4, application/postscripte.-->

* **Principales recherches** : affichez les termes recherchés les plus fréquemment, ainsi que le nombre de fois où ces termes ont été recherchés dans l’environnement de la vue Assets au cours des 30 derniers jours ou 12 derniers mois, représentés sous forme de tableau.
  ![insights-uploads](/help/assets/assets/insights-top-search.svg)
  <!--
   ![Insights](assets/insights1.png)
   ![Insights](assets/insights2.png)
   -->
* **Nombre de ressources par taille :** segmente le nombre total de ressources dans votre environnement de la vue Assets en différentes plages de tailles, en soulignant le nombre et le pourcentage de ressources dans chaque plage de tailles, représentés par un graphique en anneau.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assets-count-by-size.svg)
* **Nombre de ressources par type de ressource :** Segmente le nombre total de ressources dans l’environnement de la vue Assets, en soulignant le nombre et le pourcentage de ressources en fonction de leurs types de fichiers, représentés par un graphique en anneau.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assest-count-by-asset-type1.svg)