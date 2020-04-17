---
title: Exporter au format CSV
description: Exportez les informations relatives à vos pages vers un fichier CSV situé sur votre système local
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Exporter au format CSV   {#export-to-csv}

L’option **Créer une exportation CSV** vous permet d’exporter les informations relatives à vos pages vers un fichier CSV situé sur votre système local.

* Le fichier téléchargé est nommé `export.csv`.
* Le contenu dépend des propriétés que vous sélectionnez.
* Vous pouvez définir le chemin, ainsi que la profondeur de l’exportation.

>[!NOTE]
>
>La fonction de téléchargement et la destination par défaut du navigateur sont utilisées.

L’assistant **Créer une exportation CSV** vous permet de sélectionner les éléments suivants :

* Propriétés à exporter
   * Métadonnées
      * Nom
      * Modifié
      * Publié
      * Modèle
      * Workflow
   * Traduction
      * Traduit
   * Analyse
      * Pages vues
      * Visiteurs uniques
      * Temps sur la page
* Profondeur
   * Chemin d’accès parent
   * Enfants directs uniquement
   * Niveaux supplémentaires d’enfants
   * Niveaux

Vous pouvez ouvrir le fichier `export.csv` obtenu dans Excel (ou toute autre application compatible).

Pour créer une exportation CSV :

1. Ouvrez la console **Sites**, puis, le cas échéant, accédez à l’emplacement requis.
   * L’option **Créer un rapport CSV** est disponible lorsque vous parcourez la console **Sites** (en mode Liste).
   * Il s’agit d’une option du menu déroulant **Créer** :

      ![option Créer un fichier CSV](/help/sites-cloud/authoring/assets/csv-create.png)

1. Dans la barre d’outils, sélectionnez **Créer** puis **Rapport CSV** pour ouvrir l’assistant :

   ![Options d’exportation CSV](/help/sites-cloud/authoring/assets/csv-options.png)

1. Sélectionnez les propriétés requises à exporter.
1. Sélectionnez **Créer**.
   ![Exportation CSV résultante dans Excel](/help/sites-cloud/authoring/assets/csv-example.png)
