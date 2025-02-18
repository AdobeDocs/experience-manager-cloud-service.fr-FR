---
title: Gestion des données taxonomiques
description: Découvrez comment gérer les données taxonomiques pour utiliser des balises avec des sites AEM avec Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 017982e4-a4c8-4097-8751-9619cc4639d0
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '974'
ht-degree: 100%

---


# Gestion des données taxonomiques {#managing-taxonomy-data}

Découvrez comment gérer les données taxonomiques pour utiliser des balises avec des sites AEM avec Edge Delivery Services.

## Présentation {#introduction}

Le balisage est une fonctionnalité importante qui vous aide à organiser et à gérer vos pages. [La console de balisage](/help/sites-cloud/administering/tags.md#tagging-console) d’AEM vous permet de créer une taxonomie riche de balises pour organiser vos pages.

Ces balises s’avèrent utiles non seulement pour vous et les personnes chargées de la création dans l’organisation de votre contenu, mais également pour vos lecteurs et lectrices. Les balises et leur taxonomie peuvent être utilisées dans les composants de la page pour aider vos lecteurs et lectrices à parcourir votre contenu.

L’éditeur universel fonctionne uniquement avec les identifiants de vos balises. En créant une page de taxonomie pour votre contenu, vous exposez les descriptions de ces balises dans toutes les langues à l’éditeur universel afin qu’il puisse utiliser ces informations lors du rendu du contenu.

## Création d’une page de taxonomie {#creating}

Une taxonomie est créée comme [toute autre page dans AEM](/help/sites-cloud/authoring/sites-console/creating-pages.md).

1. Accédez à la console [**Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).

1. Sélectionnez l’emplacement où vous souhaitez créer votre taxonomie.

1. Appuyez ou cliquez sur **Créer** -> **Page**.

   ![Création d’une page](assets/taxonomy/create-page.png)

1. Dans l’onglet **Modèle** de l’assistant **Créer une page**, sélectionnez le modèle **Taxonomie** et appuyez ou cliquez sur **Suivant**.

   ![Modèle de taxonomie](assets/taxonomy/taxonomy-template.png)

1. Dans l’onglet **Propriétés** de l’assistant **Créer une page**, indiquez un **titre** significatif pour la page. Dans le champ **Balises**, [utilisez le sélecteur de balises](/help/sites-cloud/authoring/sites-console/tags.md) pour sélectionner la ou les balises ou les espaces de noms que vous souhaitez inclure dans votre taxonomie.

   ![Propriétés de taxonomie](assets/taxonomy/create-page-wizard-properties.png)

1. Appuyez ou cliquez sur **Créer**.

La page de taxonomie est créée. Dans la boîte de dialogue **Réussite**, vous pouvez appuyer ou cliquer sur la boîte de dialogue **Terminé** pour ignorer le message ou sur **Ouvrir** pour modifier la page dans l’[Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md).

Notez le nom de page obtenu pour la page de taxonomie à utiliser dans les étapes suivantes.

## Modification d’une page de taxonomie {#editing}

Vous commencez à modifier une page de taxonomie comme toute autre page dans AEM.

1. Accédez à la console [**Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).

1. Sélectionnez la taxonomie que vous souhaitez modifier.

1. Appuyez ou cliquez sur **Modifier** dans la barre d’actions.

1. L’éditeur de page s’ouvre, affichant la taxonomie.

   * La page de taxonomie est en lecture seule dans l’éditeur de page.

   ![Modifier la taxonomie](assets/taxonomy/edit-page.png)

1. Appuyez ou cliquez sur l’icône **Informations sur la page** dans la barre d’outils et sélectionnez **Ouvrir les propriétés**.

   ![Ouvrir les propriétés](assets/taxonomy/open-properties.png)

1. Dans la fenêtre **Propriétés de la page**, vous pouvez mettre à jour le nom de la page et utiliser le sélecteur de balises pour mettre à jour la ou les balises et les espaces de noms inclus dans votre taxonomie.

   ![Modifier les propriétés de la page](assets/taxonomy/edit-properties.png)

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La page affichée dans l’éditeur de page est en lecture seule, car le contenu de la taxonomie est généré automatiquement à partir des balises et espaces de noms sélectionnés. Ils agissent comme une sorte de filtre pour générer automatiquement le contenu de la taxonomie. Il n’y a donc aucune raison de modifier directement la page dans l’éditeur.

AEM met automatiquement à jour le contenu de la page de taxonomie lorsque vous mettez à jour les balises et les espaces de noms sous-jacents. Cependant, vous devez [republier la taxonomie](#publishing) après toute modification pour que ces modifications soient disponibles pour vos utilisateurs et utilisatrices.

## Mise à jour de paths.json pour la publication de taxonomie {#paths-json}

Comme lorsque vous [gérez et publiez des données tabulaires pour votre site Edge Delivery Services](/help/edge/wysiwyg-authoring/tabular-data.md), vous devez mettre à jour le fichier `paths.json` de votre projet pour permettre la publication de vos données de taxonomie.

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

   * `<taxonomy-page-name>` doit correspondre au nom de la [page de taxonomie que vous avez créée](#creating).
   * `<taxonomy-json-name>` peut être n’importe quel nom valide de votre choix.

1. Cliquez sur **Valider les modifications...** pour enregistrer les modifications apportées à `main`.

   * Vous pouvez effectuer la validation vers `main` ou créer une requête d’extraction conformément à votre processus.

Ce processus ne doit être effectué qu’une seule fois par page de taxonomie. Une fois cette opération terminée, vous pouvez publier votre taxonomie.

>[!TIP]
>
>Pour plus d’informations sur les mappages de chemins, consultez le document [Mappage de chemins pour Edge Delivery Services](/help/edge/wysiwyg-authoring/path-mapping.md).

## Publication d’une taxonomie {#publishing}

Une taxonomie n’est pas disponible pour l’éditeur universel ou vos utilisateurs et utilisatrices tant qu’elle n’a pas été publiée.

Les pages de taxonomie sont publiées comme n’importe quelle autre page [à l’aide des icônes **Publication rapide** ou **Gérer la publication** de la barre d’outils](/help/sites-cloud/authoring/sites-console/publishing-pages.md).

Vous devez republier votre page de taxonomie à chaque fois que vous effectuez l’une des opérations suivantes :

* Modifier la page de taxonomie.
* Réailser une modification ou un ajout aux balises et aux espaces de noms inclus dans votre page de taxonomie.

Si vous créez une page de taxonomie, vous devez d’abord [y ajouter un mappage au fichier `paths.json` de votre projet](#paths-json).

## Accès aux informations sur la taxonomie {#accessing}

Une fois votre taxonomie publiée, ses informations peuvent être exploitées par l’éditeur universel et rendues visibles à vos utilisateurs et utilisatrices.

Vous pouvez accéder à la taxonomie en tant que données JSON à l’adresse suivante.

`https://<branch>--<repository>--<owner>.aem.page/<taxonomy-json-name>.json`

Utilisez le `<taxonomy-json-name>` que vous avez défini lors du [mappage de votre taxonomie au fichier `paths.json` de votre projet](#paths-json). Les données de taxonomie sont renvoyées sous forme de données JSON, comme dans l’exemple ci-après.

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
  "columns": [
    "tag",
    "title"
  ],
  ":type": "sheet"
}
```

Ces données JSON sont automatiquement mises à jour lorsque vous mettez à jour la taxonomie et que vous la republiez. Votre application peut accéder à ces informations par programmation pour vos utilisateurs et utilisatrices.

[Si vous conservez des balises dans plusieurs langues](/help/sites-cloud/administering/tags.md#managing-tags-in-different-languages), vous pouvez accéder à ces langues en transmettant le code de langue ISO2 comme valeur d’un paramètre `sheet=`.

## Exposition des propriétés de balise supplémentaires {#additional-properties}

Par défaut, votre taxonomie contiendra des valeurs `tag` et `title` comme illustré [dans l’exemple précédent](#accessing). Vous pouvez configurer votre taxonomie pour exposer des propriétés de balise supplémentaires. Dans cet exemple, nous allons exposer la description de la balise.

1. Utilisez la console Sites pour sélectionner la taxonomie que vous avez créée.
1. Appuyez ou cliquez sur l’icône **Propriétés** dans la barre d’outils.
1. Dans la section **Propriétés supplémentaires**, appuyez ou cliquez sur **Ajouter** pour ajouter un champ.
1. Dans le nouveau champ, saisissez le nom de la propriété JRC à exposer. Dans ce cas, saisissez `jcr:description` pour la description de la balise.
1. Appuyez et cliquez sur **Enregistrer et fermer**.
1. Laissez la taxonomie sélectionnée et appuyez ou cliquez sur **Publication rapide** dans la barre d’outils.

Désormais, [lorsque vous accédez à votre taxonomie](#accessing), la description de la balise (ou toute propriété que vous avez choisi d’exposer) est incluse dans le fichier JSON.

```json
{
  "total": 3,
  "offset": 0,
  "limit": 3,
  "data": [
    {
      "tag": "default:",
      "title": "Standard Tags",
      "jcr:description": "These are the standard tags"
    },
    {
      "tag": "do-not-translate",
      "title": "Do Not Translate",
      "jcr:description": "Tag to mark pages that should not be translated"
    },
    {
      "tag": "translate",
      "title": "Translate",
      "jcr:description": "Tag to mark pages that should be translated"
    }
  ],
  "columns": [
    "tag",
    "title",
    "jcr:description"
  ],
  ":type": "sheet"
}
```
