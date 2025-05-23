---
title: Utiliser des feuilles de calcul pour gérer les données tabulaires
description: Découvrez comment utiliser des feuilles de calcul pour gérer les données tabulaires pour diverses valeurs, telles que les métadonnées et les redirections de votre site AEM avec Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 26d4db90-3e4b-4957-bf21-343c76322cdc
role: Admin, Architect, Developer
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '1294'
ht-degree: 100%

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
>Pour plus d’informations sur le fonctionnement général des feuilles de calcul avec Edge Delivery Services, consultez le document [Feuilles de calcul et JSON](/help/edge/developer/spreadsheets.md).

>[!TIP]
>
>Les feuilles de calcul ne doivent être utilisées que pour conserver des données tabulaires. Pour stocker des données structurées, [découvrez les fonctionnalités découplées d’AEM](/help/headless/introduction.md).

## Conditions préalables {#prerequisites}

Pour créer des mappages à l’aide de feuilles de calcul dans votre projet AEM avec Edge Delivery Services, vous devez avoir créé votre site à l’aide du modèle de site le plus récent.

Pour plus d’informations, consultez le document [Guide de prise en main du développement pour la création WYSIWYG avec Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).

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

## Import de données de feuille de calcul {#importing}

Outre la modification des feuilles de calcul dans l’éditeur de page d’AEM, vous pouvez également importer des données à partir d’un fichier CSV.

1. Lorsque vous modifiez votre feuille de calcul dans AEM, appuyez ou cliquez sur le bouton **Charger** dans le coin supérieur gauche de l’écran.
1. Dans la liste déroulante, sélectionnez le mode d’import de vos données.
   * Sélectionnez **Remplacer document** pour remplacer le contenu de toute la feuille de calcul par le contenu du fichier CSV que vous allez charger.
   * Sélectionnez **Ajouter au document** pour ajouter les données du fichier CSV que vous allez charger au contenu existant de la feuille de calcul.
1. Dans la boîte de dialogue qui s’ouvre, sélectionnez votre fichier CSV, puis appuyez ou cliquez sur **Ouvrir**.

Une boîte de dialogue s’ouvre lors du traitement de l’import. Une fois l’opération terminée, les données du fichier CSV sont ajoutées au contenu de la feuille de calcul ou le remplacent. Si des erreurs se produisent, par exemple une incohérence de colonnes, elles sont signalées afin que vous puissiez corriger votre fichier CSV.

>[!NOTE]
>
>* Les en-têtes du fichier CSV doivent correspondre exactement aux colonnes de la feuille de calcul.
>* L’import de l’intégralité du fichier CSV ne modifie pas les en-têtes de colonne, mais uniquement les lignes de contenu.
>* Si vous devez mettre à jour les colonnes, vous devez le faire dans l’éditeur de page d’AEM avant d’effectuer l’import du fichier CSV.
>* Un fichier CSV ne peut pas dépasser 10 Mo pour l’import.

En fonction de votre sélection de `mode`, vous pouvez également `create`, `replace` ou `append` dans des feuilles de calcul à l’aide d’un fichier CSV et d’une commande cURL similaire à la suivante.

```text
curl --request POST \
  --url http://<aem-instance>/bin/asynccommand \
  --header 'content-type: multipart/form-data' \
  --form file=@/path/to/your.csv \
  --form spreadsheetPath=/content/<your-site>/<your-spreadsheet> \
  --form 'spreadsheetTitle=Your Spreadsheet' \
  --form cmd=spreadsheetImport \
  --form operation=asyncSpreadsheetImport \
  --form _charset_=utf-8 \
  --form mode=append
```

L’appel renvoie une page HTML contenant des informations sur l’ID du tâche.

```text
Message | Job(Id:2024/9/18/15/27/5cb0cacc-585d-4176-b018-b684ad2dfd02_90) created successfully. Please check status at Async Job Status Navigation.
```

[Vous pouvez utiliser la **console Tâches**](/help/operations/asynchronous-jobs.md) pour afficher le statut de la tâche ou utiliser l’ID renvoyé pour le demander.

```text
https://<aem-instance>/bin/asynccommand?optype=JOBINF&jobid=2024/10/24/14/1/8da63f9e-066b-4134-95c9-21a9c57836a5_1
```

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
   >Cette entrée `paths.json` est basée sur l’exemple de création de redirections à l’aide de données tabulaires. Veillez à mettre à jour le chemin d’accès approprié vers le [type de feuille de calcul que vous créez](#other).

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
>Pour plus d’informations sur les mappages de chemins, consultez le document [Mappage de chemins pour Edge Delivery Services](/help/edge/wysiwyg-authoring/path-mapping.md).

## Autres types de feuilles de calcul {#other}

Maintenant que vous savez comment créer une feuille de calcul de redirection, vous pouvez créer n’importe quel autre type de feuille de calcul standard :

* [Espaces réservés](https://www.aem.live/docs/placeholders)
* [Métadonnées](https://www.aem.live/docs/bulk-metadata)
* [En-têtes](https://www.aem.live/docs/custom-headers)
* [Configuration](https://www.aem.live/docs/configuration), par exemple pour [invalidation du cache](https://www.aem.live/docs/byo-cdn-adobe-managed#setup-push-invalidation)
* [Taxonomie](/help/edge/wysiwyg-authoring/taxonomy.md)

Suivez simplement les mêmes étapes dans les sections [Créer une feuille de calcul](#spreadsheet) et [Mettre à jour le fichier paths.json](#paths-json). Choisissez le modèle approprié, puis mettez à jour le fichier `paths.json`.

Pour [Configuration](https://www.aem.live/docs/configuration), [En-têtes](https://www.aem.live/docs/custom-headers) et [Métadonnées](https://www.aem.live/docs/bulk-metadata) veillez à ajouter un mappage afin de les publier à leurs emplacements par défaut :

* Configuration : `/.helix/config.json`
* En-têtes : `/.helix/headers.json`
* Métadonnées : `/metadata.json`
* Taxonomie : pour plus d’informations, consultez le document [Gestion des données taxonomiques](/help/edge/wysiwyg-authoring/taxonomy.md).

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

