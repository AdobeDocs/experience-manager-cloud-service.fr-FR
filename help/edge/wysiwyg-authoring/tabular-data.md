---
title: Utiliser des feuilles de calcul pour gérer les données tabulaires
description: Découvrez comment utiliser des feuilles de calcul pour gérer les données tabulaires pour diverses valeurs, telles que les métadonnées et les redirections de votre site AEM avec Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 26d4db90-3e4b-4957-bf21-343c76322cdc
role: Admin, Architect, Developer
source-git-commit: 69c8e54bde6c6047fdefbbbb1f166af690584f88
workflow-type: tm+mt
source-wordcount: '1014'
ht-degree: 92%

---


# Utiliser des feuilles de calcul pour gérer les données tabulaires {#tabular-data}

Découvrez comment utiliser des feuilles de calcul pour gérer les données tabulaires pour diverses valeurs, telles que les métadonnées et les redirections de votre site AEM avec Edge Delivery Services.

## Cas d’utilisation {#use-cases}

Pour tout site AEM avec Edge Delivery Services, il est nécessaire de conserver des listes de données tabulaires comme pour les mappages clé-valeur. Il peut s’agir de listes de nombreuses valeurs différentes, telles que des métadonnées et des redirections. Edge Delivery Services vous permet de gérer les listes tabulaires de ce type à l’aide d’un outil intuitif : la feuille de calcul. AEM convertit ces feuilles de calcul en fichiers JSON qui peuvent être facilement consommés par votre site web ou votre application web.

Cas d’utilisation courants :

* [Espaces réservés](/help/edge/docs/placeholders.md)
* [Métadonnées](/help/edge/docs/bulk-metadata.md)
* [En-têtes](/help/edge/docs/custom-headers.md)
* [Redirections](/help/edge/docs/redirects.md)
* [Configurations](/help/edge/docs/setup-byo-cdn-push-invalidation.md), comme pour les configurations CND

Vous pouvez également [créer des feuilles de calcul](#own-spreadsheet) de n’importe quelle structure pour stocker les mappages à vos propres fins.

Ce document utilise l’exemple des redirections pour illustrer la création de feuilles de calcul de ce type. Pour plus d’informations sur chaque cas d’utilisation, reportez-vous aux rubriques précédemment liées dans la documentation Edge Delivery Services.

>[!TIP]
>
>Pour plus d’informations sur le fonctionnement général des feuilles de calcul avec Edge Delivery Services, consultez le document [Feuilles de calcul et JSON.](/help/edge/developer/spreadsheets.md)

>[!TIP]
>
>Les feuilles de calcul ne doivent être utilisées que pour conserver des données tabulaires. Pour stocker des données structurées, [découvrez les fonctionnalités découplées d’AEM.](/help/headless/introduction.md)

## Conditions préalables {#prerequisites}

Pour créer des mappages à l’aide de feuilles de calcul dans votre projet AEM avec Edge Delivery Services, vous devez avoir créé votre site à l’aide du modèle de site le plus récent.

Pour plus d’informations, consultez le document [Guide de prise en main du développeur pour la création WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) .

## Créer une feuille de calcul {#spreadsheet}

Dans cet exemple, vous allez créer une feuille de calcul pour gérer les redirections pour votre site AEM avec Edge Delivery Services. Les mêmes étapes s’appliquent aux [autres types de feuilles de calcul](#other) que vous souhaitez créer.

1. Connectez-vous à votre instance de création AEM as a Cloud Service, accédez à la console **Sites**, puis à la racine du site qui nécessite une feuille de calcul. Appuyez ou cliquez sur **Créer** -> **Page**.

   ![Création d’une page](assets/tabular-data/tabular-data-create-page.png)

1. Dans l’onglet **Modèle** de l’assistant de création de page, appuyez ou cliquez sur le modèle **Redirections** pour le sélectionner, puis appuyez ou cliquez sur **Suivant**.

   ![Sélection d’un modèle](assets/tabular-data/tabular-data-create-page-teamplate-redirects.png)

1. L’onglet **Propriétés** de l’assistant présente les valeurs par défaut de la feuille de calcul des redirections. Appuyez ou cliquez sur **Créer**.

   * **Titre** : conservez cette valeur telle quelle.
   * **Colonnes** : les colonnes minimales requises pour les redirections sont préremplies.
      * **source** : la page à rediriger.
      * **destination** : la page vers laquelle rediriger.

   ![Propriétés de la feuille de calcul](assets/tabular-data/tabular-data-create-page-properties-redirects.png)

1. Dans la boîte de dialogue **Succès**, appuyez ou cliquez **Ouvrir**.

   ![Boîte de dialogue Succès](assets/tabular-data/tabular-data-success.png)

1. Un nouvel onglet s’ouvre sur la feuille de calcul chargée dans un éditeur avec les colonnes **source** et **destination** prédéfinies. Pour définir vos redirections, appuyez ou cliquez sur la ligne vide de la colonne **source**. Les modifications sont enregistrées automatiquement lorsque vous modifiez la feuille de calcul.

   ![Modification de la feuille de calcul](assets/tabular-data/tabular-data-edit-redirects.png)

   * La **source** est relative au domaine de votre site web, elle ne contient donc que le chemin relatif.
   * La **destination** peut être une URL complète si vous redirigez vers un site web tiers ou un chemin relatif si vous redirigez vers votre propre site web.
   * Utilisez la touche de tabulation pour déplacer la sélection vers la cellule suivante.
   * L’éditeur ajoute de nouvelles lignes à la feuille de calcul selon les besoins.
   * Pour supprimer ou déplacer une ligne, utilisez l’icône **Supprimer** à la fin de chaque ligne et les poignées de déplacement au début de chaque ligne, respectivement.

## Publier une feuille de calcul paths.json {#paths-json}

Pour qu’AEM puisse publier les données dans votre feuille de calcul, vous devez également mettre à jour le fichier `paths.json` dans votre projet.

1. Ouvrez la racine de votre projet dans GitHub.

1. Appuyez ou cliquez sur le fichier `paths.json` pour ouvrir ses détails, puis sur l’icône **Modifier**.

   ![Fichier paths.json](assets/tabular-data/tabular-data-paths-json.png)

1. Ajoutez une ligne pour mapper votre nouvelle feuille de calcul à une ressource `redirects.json`.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/redirects:/redirects.json"
     ]
   }
   ```

   >[!NOTE]
   >
   >Cette entrée `paths.json` est basée sur l’exemple de création de redirections à l’aide de données tabulaires. Veillez à mettre à jour le chemin d’accès approprié au type [de feuille de calcul que vous créez.](#other)

1. Cliquez sur **Valider les modifications...** pour enregistrer les modifications apportées à `main`.

   * Vous pouvez effectuer la validation vers `main` ou créer une requête d’extraction conformément à votre processus.

1. Lorsque vous avez terminé de définir vos redirections et que vous avez mis à jour le mappage du chemin, revenez à la console **Sites**.

1. Appuyez ou cliquez pour sélectionner la feuille de calcul de redirections que vous avez créée dans la console, puis appuyez ou cliquez sur **Publication rapide** dans la barre d’actions pour publier la feuille de calcul.

   ![Sélection de la feuille de calcul dans la console Sites](assets/tabular-data/tabular-data-select-publish.png)

1. Dans la boîte de dialogue **Publication rapide**, appuyez ou cliquez sur **Publier**.

   ![Confirmation de la publication](assets/tabular-data/tabular-data-quick-publish.png)

1. Une bannière confirme la publication.

   ![Bannière de confirmation de la publication](assets/tabular-data/tabular-data-publish-banner.png)

La feuille de calcul des redirections est maintenant publiée et accessible au public.

>[!TIP]
>
>Pour plus d’informations sur les mappages de chemins, consultez le document [Mappage de chemins pour les Edge Delivery Services.](/help/edge/wysiwyg-authoring/path-mapping.md)

## Autres types de feuilles de calcul {#other}

Maintenant que vous savez comment créer une feuille de calcul de redirection, vous pouvez créer n’importe quel autre type de feuille de calcul standard :

* Espaces réservés
* Métadonnées
* En-têtes
* Configuration
* [Taxonomie](/help/edge/wysiwyg-authoring/taxonomy.md)

Suivez simplement les mêmes étapes dans les sections [Créer une feuille de calcul](#spreadsheet) et [Mettre à jour le fichier paths.json](#paths-json). Choisissez le modèle approprié, puis mettez à jour le fichier `paths.json`.

Pour [Configuration](https://www.aem.live/docs/configuration), [En-têtes](https://www.aem.live/docs/custom-headers) et [Métadonnées](https://www.aem.live/docs/bulk-metadata) veillez à ajouter un mappage afin de les publier à leurs emplacements par défaut :

* Configuration : `/.helix/config.json`
* En-têtes : `/.helix/headers.json`
* Métadonnées : `/metadata.json`
* Taxonomie : Pour plus d’informations, consultez le document [Gestion des données taxonomiques](/help/edge/wysiwyg-authoring/taxonomy.md) .

En outre, vous pouvez [créer votre propre feuille de calcul](#own-spreadsheet) avec des colonnes arbitraires pour votre propre utilisation.

>[!NOTE]
>
>Il n’est pas nécessaire de créer une feuille de calcul pour gérer l’indexation pour AEM as a Cloud Service avec les projets Edge Delivery Services.
>
>Si vous souhaitez créer vos propres index, [consultez cette documentation](https://www.aem.live/developer/indexing#setting-up-more-index-configurations) pour créer votre propre fichier `helix-query.yaml`.

## Créer votre propre feuille de calcul {#own-spreadsheet}

1. Suivez les mêmes étapes que dans la section [Créer une feuille de calcul](#spreadsheet).

1. Lors de la sélection du modèle, choisissez **Feuille de calcul**.

1. Dans l’onglet **Propriétés** de l’assistant, vous pouvez ajouter vos propres colonnes.

   ![Ajout de vos propres colonnes](assets/tabular-data/tabular-data-own-spreadsheet.png)

   * Dans la section **Colonnes**, appuyez ou cliquez sur **Ajouter** pour ajouter une nouvelle colonne.
   * Donnez un nom à la colonne.
   * Supprimez ou réorganisez les colonnes à l’aide des icônes **Supprimer** et de poignée de glissement, respectivement.

1. Créez la feuille de calcul et publiez-la conformément aux instructions de la feuille de calcul des redirections.

1. Ajoutez un mappage au fichier `paths.json` conformément aux instructions de la feuille de calcul des redirections.

