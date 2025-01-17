---
title: Gérer les rapports dans la vue Assets
description: Accédez aux données de la section des rapports de la vue Assets pour évaluer l’utilisation des produits et des fonctionnalités et déduire des informations sur les mesures de succès clés.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
feature: Asset Insights, Asset Reports
role: User, Admin, Developer
source-git-commit: c92fc95d7f2774b24664b457bf785120945fc966
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 85%

---

# Gérer les rapports {#manage-reports}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les rapports de ressources offrent aux administrateurs et administratrices une visibilité sur l’activité de l’environnement Adobe Experience Manager Assets View. Ces données fournissent des informations utiles sur la façon dont les utilisateurs interagissent avec le contenu et le produit. Tous les utilisateurs et utilisatrices peuvent accéder au tableau de bord Insights et ceux qui sont affectés au profil de produit Administrateurs et administratrices peuvent créer des rapports définis par l’utilisateur ou l’utilisatrice.

## Accéder aux rapports {#access-reports}

Tous les utilisateurs affectés au profil de produit Administrateurs et administratrices AEM peuvent accéder au tableau de bord des Insights ou créer des rapports définis par l’utilisateur ou l’utilisatrice dans la vue Assets.

Pour accéder aux rapports, accédez à **[!UICONTROL Rapports]** sous **[!UICONTROL Paramètres]**.

![Rapports](assets/reports.png)

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

L’environnement d’affichage AEM Assets offre des fonctionnalités de création de rapports complètes via le tableau de bord Rapports. Cette fonctionnalité permet aux utilisateurs et utilisatrices de générer et de télécharger des rapports CSV détaillant les chargements et les téléchargements de ressources dans des périodes spécifiées, qu’il s’agisse d’intervalles ponctuels, quotidiens, hebdomadaires, mensuels ou annuels.

**Pour créer un rapport, procédez come suit :**

1. Accédez à **Reports** et cliquez sur **Créer un rapport** (dans le coin supérieur droit). La boîte de dialogue **Créer un rapport** affiche les champs suivants :
   ![create-report](/help/assets/assets/executed-reports1.svg)

   **Dans l’onglet Configuration :**

   1. **Type de rapport :** sélectionnez parmi les types [!UICONTROL charger], [!UICONTROL télécharger] ou [Rapport de diffusion Dynamic Media](#dynamic-media-delivery-reports).
   1. **Titre :** ajoutez un titre au rapport.
   1. **Description :** ajoutez une description facultative au rapport.
   1. **Sélectionner le chemin d’accès au dossier :** sélectionnez un chemin d’accès au dossier pour générer le rapport des ressources chargées et téléchargées dans ce dossier spécifique. Par exemple, si vous avez besoin d’un rapport de ressources chargées dans un dossier, indiquez le chemin d’accès à ce dossier.
   1. **Sélectionner l’intervalle de dates :** sélectionnez la période pour afficher l’activité de chargement ou de téléchargement dans le dossier.
   <br>

   >[!NOTE]
   >
   > La vue Assets convertit tous les fuseaux horaires locaux en temps universel coordonné (UTC).

   **Dans l’onglet Colonnes :** sélectionnez les noms de colonne à afficher dans le rapport. Le tableau suivant explique l’utilisation de toutes les colonnes :

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
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Chemin</td>
      <td>Chemin d’accès au dossier qui contient la ressource dans la vue Assets.</td>
      <td>Chargement, téléchargement et diffusion Dynamic Media</td>
     </tr>
     <tr>
      <td>Type MIME</td>
      <td>Type MIME de la ressource.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Taille</td>
      <td>Taille de la ressource en octets.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Téléchargé par</td>
      <td>ID d’e-mail de l’utilisateur qui a téléchargé la ressource.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Date de téléchargement</td>
      <td>Date à laquelle la ressource a été téléchargée.</td>
      <td>Téléchargement</td>
     </tr>
     <tr>
      <td>Créateur ou créatrice</td>
      <td>Le créateur ou la créatrice de la ressource.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Date de création</td>
      <td>Date à laquelle la ressource a été chargée dans la vue Assets.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Date de modification</td>
      <td>Date de dernière modification de la ressource.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Expiré</td>
      <td>Statut d’expiration de la ressource.</td>
      <td>Chargement et téléchargement</td>
     </tr>
     <tr>
      <td>Téléchargé par « Nom d’utilisateur »</td>
      <td>Nom de l’utilisateur qui a téléchargé la ressource.</td>
      <td>Téléchargement</td>
     </tr> 
     <tr>
      <td>Référent</td>
      <td>URL de diffusion ou d’inclusion de la ressource</td>
      <td>Diffusion Dynamic Media</td>
     </tr>  
     <tr>
      <td>Accès</td>
      <td>Nombre de fois où la ressource est diffusée (nombre de diffusions)</td>
      <td>Diffusion Dynamic Media</td>
     </tr>          
    </tbody>
   </table>

## Rapports de diffusion Dynamic Media {#dynamic-media-delivery-reports}

Obtenez des informations de diffusion pour les ressources diffusées avec Dynamic Media, avec le nombre de diffusions au niveau des ressources, les informations sur les référents, le chemin d’accès aux ressources dans AEM Assets et un identifiant de ressource unique. Les rapports peuvent être générés pour toutes les ressources diffusées via Dynamic Media pour le référentiel AEM Assets ou pour une hiérarchie de dossiers spécifique dans AEM Assets. Par ailleurs, les informations des rapports de diffusion Dynamic Media permettent de mesurer le retour sur investissement des ressources diffusées, de mesurer les performances des canaux et de prendre des décisions éclairées en matière de gestion des ressources.

<!--
>[!NOTE]
> 
>To get early access to the Dynamic Media Delivery Report on your Dynamic Media account, [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).
-->

### Conditions préalables {#prereqs-dynamic-media-delivery-reports}

Vous devez disposer d’une licence Dynamic Media pour créer et utiliser ce rapport.

>[!IMPORTANT]
> 
>* Les rapports sont fournis pour les ressources diffusées par Dynamic Media.
>* Les rapports sont générés pour le premier million de lignes. Pour capturer tous les fichiers dans cette limite, pensez à inclure la colonne Référent pour les dossiers plus petits.
>* Les rapports peuvent uniquement être générés pour les 3 derniers mois.

### Créer un rapport de diffusion Dynamic Media{#create-dynamic-media-delivery-report}

1. Créez un rapport de diffusion Dynamic Media, en suivant les étapes mentionnées dans [Créer un rapport](#create-report).

1. Sélectionnez **[!UICONTROL Diffusion Dynamic Media]** dans la liste déroulante **[!UICONTROL Type de rapport]**.

   ![Liste déroulante Rapport de diffusion Dynamic Media](assets/dynamic-media-delivery-report-option.png)


1. Dans l’onglet **[!UICONTROL Colonnes]**, vous pouvez sélectionner la colonne **[!UICONTROL Référent]** pour l’inclure dans votre rapport.

   ![Référent](assets/referrer.png)

   Toutes les colonnes du rapport téléchargé sont en lecture seule, à l’exception de la colonne **Référent**, que vous pouvez modifier pour l’inclure ou l’exclure du rapport. <!--Choosing a referrer displays the number of visitors received from each referred report that directs traffic to the site. It offers insights into the sources of traffic and the origin of the visitors. Such insights help measure ROI of delivered assets, measure channel performance, and help take informed asset management tasks for assets.-->

### Actions effectuées sur le rapport Diffusion Dynamic Media {#actions-performed-dynamic-media-delivery-reports}

Après avoir créé le rapport, vous pouvez effectuer les actions suivantes :

* **[!UICONTROL Supprimer]** : vous pouvez supprimer le rapport sélectionné.
* **[!UICONTROL Télécharger CSV]** : vous pouvez télécharger le rapport sélectionné au format CSV. Le rapport téléchargé se compose des colonnes Nom, Chemin, DynamicMediaID, Référent, Accès.
   * La colonne **Référent** répertorie l’URL où la ressource est diffusée ou incluse.

   * La colonne **Accès** recense le nombre de fois où la ressource est diffusée (nombre de diffusions).

Pour supprimer ou télécharger le rapport Diffusion Dynamic Media au format CSV, voir la section [Afficher et télécharger un rapport existant](#View-and-download-existing-report).

![Fichier CSV téléchargé sur le rapport de diffusion Dynamic Media](assets/csv-dynamic-media-delivery-report.png)


## Afficher et télécharger un rapport existant {#View-and-download-existing-report}

Les rapports existants s’affichent dans l’onglet **Rapports exécutés**. Cliquez sur **Rapports** et sélectionnez **Rapports exécutés** pour afficher tous les rapports créés dont le statut est **Terminé**, indiquant qu’ils peuvent être téléchargés. Pour télécharger le rapport au format CSV ou le supprimer, sélectionnez la ligne du rapport. Sélectionnez ensuite **Télécharger le fichier CSV** ou **Supprimer**.
![Affichage et téléchargement de rapports existants](/help/assets/assets/view-download-existing-report.png)


## Planifier un rapport {#schedule-report}

Dans l’interface utilisateur de la vue AEM Assets, la fonction **Planifier le rapport** configure une génération automatique de rapports à des intervalles futurs spécifiés, tels que quotidien, hebdomadaire, mensuel ou annuel. Cette fonctionnalité permet de rationaliser les besoins récurrents en matière de reporting et d’assurer des mises à jour opportunes des données. **Créer un rapport** génère pour sa part des rapports pour les dates antérieures. Les rapports terminés sont répertoriés dans **Rapports exécutés** et les rapports à venir se trouvent dans **Rapports planifiés**.

Pour planifier un rapport, procédez comme suit :

1. Cliquez sur Rapports dans le volet de gauche, puis sur Créer un rapport (en haut à droite).
1. La boîte de dialogue du rapport affiche les informations suivantes :
   1. **Type de rapport :** choisissez entre le type de chargement et de téléchargement.
   1. **Titre :** ajoutez un titre au rapport.
   1. **Description :** ajoutez une description facultative au rapport.
   1. **Sélectionner le chemin d’accès au dossier :** sélectionnez un chemin d’accès au dossier afin de générer un rapport pour les ressources qui seront chargées ou téléchargées à partir de ce dossier spécifique à l’avenir.
   1. Activer **Planifier un rapport :** activez cette option pour planifier le rapport à une date ultérieure ou récurrente.
      ![Planification d’un rapport](/help/assets/assets/schedule-reports1.svg)

   1. **Choisir la fréquence :** spécifiez l’intervalle de génération du rapport (par exemple, quotidien, hebdomadaire, mensuel, annuel ou ponctuel) et définissez la date et l’heure d’exécution du rapport ainsi que la date de fin de la périodicité. Pour un rapport ponctuel, sélectionnez la période du rapport sur le type d’activité sélectionné dans l’environnement AEM. Par exemple, si vous avez besoin d’un rapport sur les ressources téléchargées entre le 10 et le 29 (dates futures) d’un mois spécifique, sélectionnez ces dates dans le champ **Sélectionner l’intervalle de dates**.

   >[!NOTE]
   >
   > La vue Assets convertit tous les fuseaux horaires locaux en temps universel coordonné (UTC).

## Afficher les rapports planifiés {#view-scheduled-reports}

Les rapports planifiés s’affichent dans l’onglet **Rapports planifiés** et sont organisés de manière systématique. Tous les rapports terminés pour chaque rapport planifié sont stockés dans un seul dossier de rapports. Cliquez![développez, réduisez](/help/assets/assets/expand-icon1.svg)pour afficher les rapports terminés. Par exemple, si vous avez planifié un rapport quotidien, tous les rapports terminés sont regroupés dans un seul dossier. Cette organisation simplifie la navigation et la recherche des rapports. Pour afficher les rapports planifiés, cliquez sur **Rapports**, puis sur **Rapports planifiés**. Tous les rapports planifiés s’affichent, avec le statut En cours ou Terminé. Les rapports terminés peuvent être téléchargés.\
![Rapport planifié](/help/assets/assets/scheduled-reports-tab.png)

## Modifier et annuler des rapports planifiés {#edit-cancel-scheduled-reports}

1. Accédez à l’onglet **Rapports planifiés**.
1. Sélectionnez la ligne du rapport.
1. Cliquez sur **Modifier**.
1. Cliquez sur **Annuler la planification**, puis sur **Confirmer** pour annuler le rapport planifié. Pour les rapports annulés, la prochaine exécution devient vide et le statut est Annulé.
   ![Modification et annulation d’un rapport planifié](/help/assets/assets/cancel-edit-scheduled-reports.png)

### Reprendre le planning {#resume-schedule}

Pour reprendre le planning annulé, sélectionnez la ligne du rapport et cliquez sur **Reprendre le planning**. Lors de la reprise, les entrées d’exécution suivantes s’affichent à nouveau et le statut est En cours.
![Reprise du planning](/help/assets/assets/resume-schedule.png)

>[!NOTE]
>
> Si vous reprenez un rapport annulé avant la date de fin planifiée, les rapports entre la date d’annulation et la date de reprise sont automatiquement générés.

## Afficher les insights {#view-live-statistics}

La vue Assets vous permet d’afficher des données en temps réel pour votre environnement Assets à l’aide du tableau de bord Insights. Vous pouvez afficher les mesures d’événement en temps réel au cours des 30 derniers jours ou au cours des 12 derniers mois.

<!--![Toolbar options when you select an asset](assets/assets-view-live-statistics.png)-->

Cliquez sur les **[!UICONTROL Insights]** disponibles dans le volet de navigation de gauche pour afficher les graphiques générés automatiquement suivants :

* **Téléchargements** : nombre de ressources téléchargées à partir de l’environnement d’affichage Assets au cours des 30 derniers jours ou 12 derniers mois, représentées à l’aide d’un graphique linéaire.
  ![informations-téléchargements](/help/assets/assets/insights-downloads2341.svg)

* **Chargements** : nombre de ressources chargées dans l’environnement d’affichage Assets au cours des 30 derniers jours ou 12 derniers mois, représentées à l’aide d’un graphique linéaire.
  ![insights-uploads](/help/assets/assets/insights-uplods2.svg)
  <!--* **Asset Count by Size**: The division of count of assets based on their range of various sizes from 0 MB to 100 GB.-->

* **Utilisation du stockage** : utilisation du stockage, en octets, pour l’environnement d’affichage Assets représenté à l’aide d’un graphique à barres.
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
* **Nombre de ressources par type de ressource :** segmente le nombre total de ressources dans votre environnement d’affichage Assets en mettant en surbrillance le nombre et le pourcentage de ressources en fonction de leurs types de fichiers, représentés par un graphique en anneau.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assest-count-by-asset-type1.svg)