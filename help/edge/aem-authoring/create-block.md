---
title: Créer des blocs instrumentés pour une utilisation avec l’éditeur universel
description: Découvrez comment créer des blocs instrumentés pour une utilisation avec l’éditeur universel dans l’instance de création AEM avec des projets Edge Delivery Services.
exl-id: 65a5600a-8d16-4943-b3cd-fe2eee1b4abf
source-git-commit: cc41ff626f6fc6d72785401e3ba38b189945bf74
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 93%

---


# Créer des blocs instrumentés pour une utilisation avec l’éditeur universel {#create-block}

Découvrez comment créer des blocs instrumentés pour une utilisation avec l’éditeur universel dans l’instance de création AEM avec des projets Edge Delivery Services.

## Conditions préalables {#prerequisites}

Ce guide fournit des instructions détaillées sur la création de blocs instrumentés pour l’éditeur universel dans l’instance de création AEM avec des projets Edge Delivery Services. Il aborde l’ajout de composants, le chargement de définitions de composants dans l’éditeur universel, la publication de pages, l’implémentation des décorations et des styles de bloc, l’application des modifications à l’environnement de production ainsi que la vérification de ces modifications. Quand vous aurez terminé ce guide, vous pourrez créer et déployer un nouveau bloc pour votre propre projet.

Ce guide nécessite obligatoirement une connaissance de l’instance de création AEM avec des projets Edge Delivery Services ainsi qu’une connaissance de l’éditeur universel. Avant de commencer ce guide, vous devez déjà avoir accès à Edge Delivery Services et connaître ses principes de base, notamment :

Vous avez terminé le [tutoriel sur Edge Delivery Services.](/help/edge/developer/tutorial.md)
* Vous avez accès à un [sandbox AEM Cloud Service.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)
* Vous avez [activé l’éditeur universel dans le même environnement de sandbox.](/help/implementing/universal-editor/getting-started.md)
* Vous avez terminé le guide : [Guide de prise en main du développement pour l’instance de création AEM avec Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md).

Ce guide s’appuie sur le travail effectué dans le [Guide de prise en main du développement pour l’instance de création AEM avec Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md).

## Ajouter un nouveau bloc à votre projet {#add-block}

Dans ce guide, vous allez créer un bloc pour afficher une citation mémorable sur votre page.

Pour simplifier cet exemple, toutes les modifications sont apportées à la branche `main` du référentiel du projet. Bien sûr, pour votre projet réel, [vous devez suivre les bonnes pratiques en matière de développement](https://www.aem.live/docs/dev-collab-and-good-practices) en effectuant le développement sur une autre branche et en examinant toutes les modifications via une demande d’extraction avant de fusionner vers `main`.

Adobe vous recommande de développer des blocs selon une approche en trois étapes :

1. Créez la définition et le modèle du bloc, vérifiez-le et transférez-le en production.
1. Créez du contenu avec le nouveau bloc.
1. Implémentez la décoration et les styles du nouveau bloc.

L’exemple de bloc de citation suivant suit cette approche.

### Créer une définition et un modèle de bloc {#create-block-model}

1. Clonez le projet GitHub local que vous avez créé dans le [Guide de prise en main du développement pour l’instance de création AEM avec Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) et ouvrez-le dans l’éditeur de votre choix.

   * L’éditeur Microsoft Code est utilisé ici à titre d’exemple.

   ![Clonage du projet](assets/create-block/clone.png)

1. Modifiez le fichier `component-definition.json` à la racine du projet et ajoutez la définition suivante à votre nouveau bloc de citation, puis enregistrez le fichier.

   ```json
   {
     "title": "Quote",
     "id": "quote",
     "plugins": {
       "xwalk": {
         "page": {
           "resourceType": "core/franklin/components/block/v1/block",
           "template": {
             "name": "Quote",
             "model": "quote",
             "quote": "<p>Think, McFly! Think!</p>",
             "author": "Biff Tannen"
           }
         }
       }
     }
   }
   ```

   ![Modification du fichier component-definitions.json pour définir le bloc de citation](assets/create-block/component-definitions.png)

1. Modifiez le fichier `component-models.json` à la racine du projet et ajoutez la [définition de modèle](/help/implementing/universal-editor/field-types.md#model-structure) suivante à votre nouveau bloc de citation, puis enregistrez le fichier.

   * Consultez le document [Modélisation de contenu pour l’instance de création AEM avec des projets Edge Delivery Services](/help/edge/aem-authoring/content-modeling.md) pour plus d’informations sur ce qu’il importe de prendre en compte lors de la création de modèles de contenu.

   ```json
   {
     "id": "quote",
     "fields": [
        {
          "component": "text-area",
          "name": "quote",
          "value": "",
          "label": "Quote",
          "valueType": "string"
        },
        {
          "component": "text-input",
          "valueType": "string",
          "name": "author",
          "label": "Author",
          "value": ""
        }
      ]
   }
   ```

   ![Modification du fichier component-models.json pour définir le modèle du bloc de citation](assets/create-block/component-models.png)

1. Modifiez le fichier `component-filters.json` à la racine du projet et ajoutez le bloc de citation à la [définition de filtre](/help/implementing/universal-editor/customizing.md#filtering-components) afin de permettre d’ajouter le bloc à n’importe quelle section, puis l’enregistrement du fichier.

   ```json
   {
     "id": "section",
     "components": [
       "text",
       "image",
       "button",
       "title",
       "hero",
       "cards",
       "columns",
       "quote"
      ]
   }
   ```

   ![Modification du fichier component-filters.json pour définir les filtres du bloc de citation](assets/create-block/component-filters.png)

1. À l’aide de Git, validez ces modifications dans votre branche `main`.

   * La validation dans `main` est effectuée à titre d’exemple uniquement. [Respectez les bonnes pratiques](https://www.aem.live/docs/dev-collab-and-good-practices) et utilisez une demande d’extraction lors d’un travail sur un projet réel.

### Créer du contenu avec le bloc {#create-content}

Maintenant que votre bloc de citation de base est défini et validé dans l’exemple de projet, vous pouvez ajouter un bloc de citation à une page existante.

1. Dans un navigateur, connectez-vous à AEM as a Cloud Service. [À l’aide de la console Sites,](/help/sites-cloud/authoring/basic-handling.md) accédez au site que vous avez créé dans le [Guide de prise en main du développement pour l’instance de création AEM avec Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) et sélectionnez une page.

   * Dans ce cas, `index` est utilisé à titre d’exemple.

   ![Sélection de la page d’index dans la console Sites](assets/create-block/sites-console.png)

1. Appuyez ou cliquez sur **Modifier** dans la barre d’outils de la console, l’éditeur universel s’ouvre alors.

   * Pour charger la page, vous devrez peut-être appuyer ou cliquer sur **Se connecter avec Adobe** pour vous authentifier dans AEM dans l’éditeur universel.

1. Sélectionnez une section dans l’éditeur universel. Dans le rail des propriétés, appuyez ou cliquez sur l’icône **Ajouter**, puis sélectionnez votre nouveau bloc de **Citation** dans le menu.

   * L’icône **Ajouter** est un symbole plus.
   * Vous pouvez savoir que vous avez sélectionné une section si le contour bleu de l’objet sélectionné comporte un onglet intitulé **Section**.
   * Dans cet exemple, appuyer ou cliquer légèrement au-dessus du titre **Lorem Ipsum** sélectionne une section contenant le titre et le texte lorem ipsum.

   ![Sélection d’une section dans l’éditeur universel](assets/create-block/add-quote-block.png)

1. La page est rechargée et le bloc de citation est ajouté au bas de la section sélectionnée avec le contenu par défaut spécifié dans le fichier `component-definitions.json`.

   * Le bloc de citation peut être sélectionné et modifié comme tout autre bloc, soit directement sur le bloc, soit dans le rail de propriétés.
   * Les styles seront appliqués lors d’une étape ultérieure.

   ![Page avec le nouveau bloc de citation dans la section sélectionnée](assets/create-block/quote-added.png)

1. Une fois que le contenu de votre citation vous satisfait, vous pouvez publier la page en appuyant ou en cliquant sur le bouton **Publier** dans la barre d’outils de l’éditeur universel.

1. Vérifiez que le contenu a été publié en accédant à la page publiée. Le lien sera similaire à `https://<branch>--<repo>--<owner>.hlx.page`.

   ![Citation publiée](assets/create-block/quote-published.png)

### Appliquer un style au bloc {#style-block}

Maintenant que vous avez un bloc de citation fonctionnel, vous pouvez lui appliquer un style.

1. Revenez à l’éditeur de votre projet.

1. Créez un dossier `quote` dans le dossier `blocks`.

   ![Création d’un dossier de citation](assets/create-block/new-folder.png)

1. Dans le nouveau dossier `quote`, ajoutez un fichier `quote.js` pour implémenter la décoration du bloc en ajoutant le code JavaScript suivant, puis enregistrez le fichier.

   ```javascript
   export default function decorate(block) {
     const [quoteWrapper] = block.children;
   
     const blockquote = document.createElement('blockquote');
     blockquote.textContent = quoteWrapper.textContent.trim();
     quoteWrapper.replaceChildren(blockquote);
   }
   ```

   ![Ajout de code JavaScript pour la décoration du bloc](assets/create-block/quote-js.png)


1. Dans le dossier `quote`, ajoutez un fichier `quote.css` pour définir le style du bloc en ajoutant le code CSS suivant, puis enregistrez le fichier.

   ```css
   .block.quote {
       background-color: #ccc;
       padding: 0 0 24px;
       display: flex;
       flex-direction: column;
       margin: 1rem 0;
   }
   
   .block.quote blockquote {
       margin: 16px;
       text-indent: 0;
   }
   
   .block.quote > div:last-child > div {
       margin: 0 16px;
       font-size: small;
       font-style: italic;
       position: relative;
   }
   
   .block.quote > div:last-child > div::after {
       content: "";
       display: block;
       position: absolute;
       left: 0;
       bottom: -8px;
       height: 5px;
       width: 30px;
       background-color: darkgray;
   }
   ```

   ![Ajout de code CSS pour définir le style du bloc](assets/create-block/quote-css.png)

1. À l’aide de Git, validez ces modifications dans votre branche `main`.

   * La validation dans `main` est effectuée à titre d’exemple uniquement. [Respectez les bonnes pratiques](https://www.aem.live/docs/dev-collab-and-good-practices) et utilisez une demande d’extraction lors d’un travail dans un projet réel.

1. Revenez à l’onglet de navigateur dans l’éditeur universel dans lequel vous étiez en train de modifier la page de votre projet, puis rechargez la page pour afficher le bloc avec son style appliqué.

1. Vous voyez ainsi sur la page le bloc de citation avec son style appliqué.

   ![Bloc de citation avec son style appliqué dans l’éditeur universel](assets/create-block/quote-styled.png)

1. Vérifiez que les modifications ont été transférées en production en accédant à la page publiée. Le lien sera similaire à `https://<branch>--<repo>--<owner>.hlx.page`.

   ![Bloc de citation publié et avec son style appliqué](assets/create-block/quote-styled-published.png)

Félicitations. Vous disposez maintenant d’un bloc de citation entièrement fonctionnel et avec un style appliqué. Vous pouvez utiliser cet exemple comme base pour concevoir vos propres blocs spécifiques à des projets.

## Utiliser d’autres branches de travail {#other-branches}

Dans ce guide, vous avez validé vos modifications directement dans la branche `main` pour des raisons de simplicité. Dans le cadre d’une expérimentation dans un référentiel d’exemple, ce n’est généralement pas un problème. Dans le cadre d’un travail dans un projet réel, [vous devez suivre les bonnes pratiques en matière de développement](https://www.aem.live/docs/dev-collab-and-good-practices) en effectuant le développement dans une autre branche et en vérifiant toutes les modifications via une demande d’extraction avant de fusionner vers `main`.

Lorsque vous ne développez pas dans la branche `main`, vous pouvez ajouter `?ref=<branch>` dans la barre d’emplacement de l’éditeur universel pour charger la page à partir de votre branche. `<branch>` est le nom de la branche tel qu’il serait utilisé pour la prévisualisation de votre projet ou pour les URL actives, par exemple `https://<branch>--<repo>--<owner>.hlx.page`.

La publication de contenu avec un nouveau modèle n’est prise en charge que lorsque le modèle est fusionné avec la branche `main`.

## Étapes suivantes {#next-steps}

Maintenant que vous savez comment créer des blocs, il est essentiel de comprendre comment modéliser le contenu d’une manière sémantique pour obtenir une expérience de développement allégée.

Consultez le document [Modélisation de contenu pour la création AEM avec des projets Edge Delivery Services](/help/edge/aem-authoring/content-modeling.md) pour découvrir comment fonctionne la modélisation de contenu pour la création AEM avec des projets Edge Delivery Services.

>[!TIP]
>
>Pour une présentation exhaustive de la création d’un projet Edge Delivery Services activé pour la création AEM avec AEM as a Cloud Service comme source de contenu, consultez [ce webinaire GEMs AEM.](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)
