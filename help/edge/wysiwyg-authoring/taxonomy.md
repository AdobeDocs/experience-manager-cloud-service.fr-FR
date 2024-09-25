---
title: Gérer des données taxonomiques
description: Découvrez comment gérer les données de taxonomie pour utiliser des balises avec votre AEM avec des sites Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 017982e4-a4c8-4097-8751-9619cc4639d0
source-git-commit: 13bde08db33ff4b81a6e76cad91bb5ea257ab195
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 7%

---

# Gérer des données taxonomiques {#managing-taxonomy-data}

Découvrez comment gérer les données de taxonomie pour utiliser des balises avec votre AEM avec des sites Edge Delivery Services.

## Présentation {#introduction}

Le balisage est une fonctionnalité importante qui vous aide à organiser et gérer vos pages. [La console de balisage](/help/sites-cloud/administering/tags.md#tagging-console) dans AEM vous permet de créer une taxonomie riche de balises pour organiser vos pages.

Ces balises s’avèrent utiles non seulement pour vous et vos auteurs dans l’organisation de votre contenu, mais également pour vos lecteurs. Les balises et leur taxonomie peuvent être utilisées dans les composants de la page pour aider vos lecteurs à parcourir votre contenu.

L’éditeur universel fonctionne uniquement avec les identifiants de vos balises. En créant une page de taxonomie pour votre contenu, vous exposez les descriptions de ces balises dans toutes les langues à l’éditeur universel afin qu’il puisse utiliser ces informations lors du rendu du contenu.

## Créer une page de taxonomie {#creating}

Une taxonomie est créée comme [toute autre page dans AEM.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Accédez à la console [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

1. Sélectionnez l’emplacement où vous souhaitez créer votre taxonomie.

1. Appuyez ou cliquez sur **Créer** -> **Page**.

   ![Création d’une page](assets/taxonomy/create-page.png)

1. Dans l’onglet **Template** de l’assistant **Créer une page**, sélectionnez le modèle **Taxonomie** et appuyez ou cliquez sur **Suivant**.

   ![Modèle de taxonomie](assets/taxonomy/taxonomy-template.png)

1. Dans l’onglet **Propriétés** de l’assistant **Créer une page**, indiquez un **titre** significatif pour la page. Dans le champ **Balises**, [utilisez le sélecteur de balises](/help/sites-cloud/authoring/sites-console/tags.md) pour sélectionner la ou les balises ou les espaces de noms que vous souhaitez inclure dans votre taxonomie.

   ![Propriétés de taxonomie](assets/taxonomy/create-page-wizard-properties.png)

1. Appuyez ou cliquez sur **Créer**.

La page de taxonomie est créée. Dans la boîte de dialogue **Succès**, vous pouvez appuyer ou cliquer sur la boîte de dialogue **Terminé** pour ignorer le message ou sur **Ouvrir** pour modifier la page dans l’ [Éditeur de page.](/help/sites-cloud/authoring/page-editor/introduction.md)

Prenez note du nom de page obtenu de la page de taxonomie à utiliser dans les étapes suivantes.

## Modification d’une page de taxonomie {#editing}

Vous commencez à modifier une page de taxonomie comme toute autre page dans AEM.

1. Accédez à la console [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

1. Sélectionnez la taxonomie que vous souhaitez modifier.

1. Appuyez ou cliquez sur **Modifier** dans la barre d’actions.

1. L’éditeur de page s’ouvre, affichant la taxonomie.

   * La page de taxonomie est en lecture seule dans l’éditeur de page.

   ![Modifier la taxonomie](assets/taxonomy/edit-page.png)

1. Appuyez ou cliquez sur l’icône **Informations sur la page** dans la barre d’outils et sélectionnez **Ouvrir les propriétés**.

   ![Ouvrir les propriétés](assets/taxonomy/open-properties.png)

1. Dans la fenêtre **Propriétés de page**, vous pouvez mettre à jour le nom de la page et utiliser le sélecteur de balises pour mettre à jour la ou les balises et les espaces de noms inclus dans votre taxonomie.

   ![Modifier les propriétés de page](assets/taxonomy/edit-properties.png)

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La page affichée dans l’éditeur de page est en lecture seule, car le contenu de la taxonomie est généré automatiquement à partir des balises et espaces de noms sélectionnés. Ils agissent comme une sorte de filtre pour générer automatiquement le contenu de la taxonomie. Il n’y a donc aucune raison de modifier directement la page dans l’éditeur.

AEM met automatiquement à jour le contenu de la page de taxonomie lorsque vous mettez à jour les balises et les espaces de noms sous-jacents. Cependant, vous devez [republier la taxonomie](#publishing) après toute modification pour que ces modifications soient disponibles pour vos utilisateurs.

## Mise à jour de paths.json pour la publication de taxonomie {#paths-json}

Comme lorsque vous [ gérez et publiez des données tabulaires pour votre site de Edge Delivery Services, ](/help/edge/wysiwyg-authoring/tabular-data.md) vous devez mettre à jour votre fichier `paths.json` de votre projet pour permettre la publication de vos données de taxonomie.

1. Ouvrez la racine de votre projet dans GitHub.

1. Appuyez ou cliquez sur le fichier `paths.json` pour ouvrir ses détails, puis sur l’icône **Modifier**.

   ![Fichier paths.json](assets/taxonomy/paths-json.png)

1. Ajoutez une ligne pour mapper votre nouvelle page de taxonomie à une ressource `.json`.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/<taxonomy-page-name>:/<taxonomy-json-name>.json"
     ]
   }
   ```

   * `<taxonomy-page-name>` doit correspondre au nom de la [page de taxonomie que vous avez créée.](#creating)
   * `<taxonomy-json-name>` peut être n’importe quel nom valide de votre choix.

1. Cliquez sur **Valider les modifications...** pour enregistrer les modifications apportées à `main`.

   * Vous pouvez effectuer la validation vers `main` ou créer une requête d’extraction conformément à votre processus.

Ce processus ne doit être effectué qu’une seule fois par page de taxonomie. Une fois cette opération terminée, vous pouvez publier votre taxonomie.

>[!TIP]
>
>Pour plus d’informations sur les mappages de chemins, consultez le document [Mappage de chemins pour les Edge Delivery Services.](/help/edge/wysiwyg-authoring/path-mapping.md)

## Publier une taxonomie {#publishing}

Une taxonomie n’est pas disponible pour l’éditeur universel ou vos utilisateurs tant qu’elle n’a pas été publiée.

Les pages de taxonomie sont publiées comme n&#39;importe quelle autre page par [à l&#39;aide des icônes **Quick Publish** ou **Gérer la publication** de la barre d&#39;outils.](/help/sites-cloud/authoring/sites-console/publishing-pages.md)

Vous devez republier votre page de taxonomie à chaque fois que vous :

* Modifiez la page de taxonomie.
* Modifiez ou ajoutez à la ou aux balises et aux espaces de noms inclus dans votre page de taxonomie.

Si vous créez une page de taxonomie, vous devez d&#39;abord [y ajouter un mappage au fichier `paths.json` de votre projet.](#paths-json)

## Accès aux informations sur la taxonomie {#accessing}

Une fois votre taxonomie publiée, ses informations peuvent être exploitées par l’éditeur universel et rendues visibles par vos utilisateurs.

Vous pouvez accéder à la taxonomie en tant que données JSON à l’adresse suivante.

`https://<branch>--<repository>--<owner>.hlx.page/<taxonomy-json-name>.json`

Utilisez le `<taxonomy-json-name>` que vous avez défini lors du [mappage de votre taxonomie au fichier `paths.json` de votre projet.](#paths-json) Les données de taxonomie sont renvoyées sous forme de données JSON, comme dans l’exemple suivant.

```json
{
  "total": 3,
  "offset": 0,
  "limit": 3,
  "data": [
    {
      "tag": "default:",
      "title": "Standard Tags"
    },
    {
      "tag": "do-not-translate",
      "title": "Do Not Translate"
    },
    {
      "tag": "translate",
      "title": "Translate"
    }
  ],
  ":type": "sheet"
}
```

Ces données JSON sont automatiquement mises à jour lorsque vous mettez à jour la taxonomie et que vous la republiez. Votre application peut accéder à ces informations par programmation pour vos utilisateurs.

[Si vous conservez des balises dans plusieurs langues,](/help/sites-cloud/administering/tags.md#managing-tags-in-different-languages) vous pouvez accéder à ces langues en transmettant le code de langue ISO2 comme valeur d’un paramètre `sheet=`.
