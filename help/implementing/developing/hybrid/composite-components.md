---
title: Composants composites dans SPA
description: Découvrez comment créer vos propres composants composites, composants composés d’autres composants, qui fonctionnent avec l’éditeur d’application AEM page unique (SPA).
exl-id: fa1ab1dd-9e8e-4e2c-aa9a-5b46ed8a02cb
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Composants composites dans SPA {#composite-components-in-spas}

Les composants composites exploitent la nature modulaire des composants AEM en combinant plusieurs composants de base en un seul composant. Le cas d’utilisation courant d’un composant composite est celui du composant de carte, composé d’une combinaison des composants image et texte.

Lorsque les composants composites sont correctement implémentés dans la structure de l’éditeur d’application de page unique (SPA) d’AEM, les auteurs de contenu peuvent faire glisser et déposer ces composants comme s’ils le feraient pour tout autre composant, tout en ayant la possibilité de modifier individuellement chaque composant qui constitue le composant composite.

Cet article explique comment ajouter un composant composite à votre application d’une seule page pour travailler en toute transparence avec AEM SPA Editor.

## Exemple d’utilisation  {#use-case}

Cet article utilisera le composant de carte type comme exemple d’utilisation. Les cartes sont un élément d’interface utilisateur courant pour de nombreuses expériences numériques. Elles sont généralement constituées d’une image et du texte ou de la légende associés. L’auteur souhaite pouvoir faire glisser et déposer l’ensemble de la carte, mais aussi modifier individuellement l’image de la carte et personnaliser le texte associé.

## Prérequis {#prerequisites}

Les modèles suivants pour la prise en charge des cas d’utilisation des composants composites nécessitent les conditions préalables suivantes.

* Votre instance de développement AEM s’exécute localement sur le port 4502 avec un exemple de projet.
* L’application React externe opérationnelle [est activée pour modification dans AEM.](editing-external-spa.md)
* L’application React est chargée dans l’éditeur d’AEM [à l’aide du composant RemotePage.](remote-page.md)

## Ajout de composants composites à une SPA {#adding-composite-components}

Il existe trois modèles différents pour mettre en oeuvre votre composant composite en fonction de votre mise en oeuvre SPA dans AEM.

* [Le composant n’existe pas dans votre projet AEM.](#component-does-not-exist)
* [Le composant existe dans votre projet AEM, mais son contenu requis ne l’est pas.](#content-does-not-exist)
* [Le composant et son contenu requis existent tous deux dans votre projet AEM.](#both-exist)

Les sections suivantes présentent des exemples d’implémentation de chaque cas à l’aide du composant Carte.

### Le composant n’existe pas dans votre projet AEM. {#component-does-not-exist}

Commencez par créer les composants qui constitueront le composant composite, c’est-à-dire les composants de l’image et de son texte.

1. Créez le composant texte dans votre projet AEM.
1. Ajoutez le `resourceType` correspondant du projet dans le noeud `editConfig` du composant.

   ```text
    resourceType: 'wknd-spa/components/text' 
   ```

1. Utilisez l’`withMappable` aide pour activer la modification du composant.

   ```text
   export const AEMText = withMappable(Text, TextEditConfig); 
   ```

Le composant de texte sera similaire à ce qui suit.

```javascript
import React from 'react';
import { withMappable } from '@adobe/aem-react-editable-components';

export const TextEditConfig = {
  emptyLabel: 'Text',
  isEmpty: function(props) {
    return !props || !props.text || props.text.trim().length < 1;
  },
  resourceType: 'wknd-spa/components/text'
};

export const Text = ({ cqPath, richText, text }) => {
  const richTextContent = () => (
    <div className="aem_text"
      id={cqPath.substr(cqPath.lastIndexOf('/') + 1)}
      data-rte-editelement
      dangerouslySetInnerHTML={{__html: text}} />
  );
  return richText ? richTextContent() : (
     <div className="aem_text">{text}</div>
  );
};

export const AEMText = withMappable(Text, TextEditConfig);
```

Si vous créez un composant d’image de la même manière, vous pouvez le combiner avec le composant `AEMText` dans un nouveau composant de carte, en utilisant les composants d’image et de texte comme composants enfants.

```javascript
import React from 'react';
import { AEMText } from './AEMText';
import { AEMImage } from './AEMImage';

export const AEMCard = ({ pagePath, itemPath}) => (
  <div>
    <AEMText
       pagePath={pagePath}
       itemPath={`text`} />
    <AEMImage
       pagePath={pagePath}
       itemPath={`image`} />
   </div>
);
```

Ce composant composite obtenu peut désormais être placé n’importe où dans l’application et le ajoute des espaces réservés pour un composant de texte et d’image dans l’éditeur de SPA. Dans l’exemple ci-dessous, le composant de carte est ajouté au composant principal sous le titre.

```javascript
function Home() {
  return (
    <div className="Home">
      <h2>Current Adventures</h2>
      <AEMCard
        pagePath='/content/wknd-spa/home' />
    </div>
  );
}
```

Un espace réservé vide s’affiche alors pour un texte et une image dans l’éditeur. Lors de la saisie de valeurs pour celles-ci à l’aide de l’éditeur, elles sont stockées au chemin de page spécifié, c’est-à-dire `/content/wknd-spa/home` au niveau racine avec les noms spécifiés dans `itemPath`.

![Composant de carte composite dans l’éditeur](assets/composite-card.png)

### Le composant existe dans votre projet AEM, mais son contenu requis ne l’est pas. {#content-does-not-exist}

Dans ce cas, le composant de carte est déjà créé dans votre projet AEM contenant les noeuds de titre et d’image. Les noeuds enfants (texte et image) possèdent les types de ressources correspondants.

![Structure de noeud du composant Carte](assets/composite-node-structure.png)

Vous pouvez ensuite l’ajouter à votre SPA et récupérer son contenu.

1. Créez un composant correspondant dans le SPA pour cela. Assurez-vous que les composants enfants sont mappés à leurs types de ressources AEM correspondants dans le projet SPA. Dans cet exemple, nous utilisons les mêmes composants `AEMText` et `AEMImage` que décrit [dans le cas précédent.](#component-does-not-exist)

   ```javascript
   import React from 'react';
   import { Container, withMappable, MapTo } from '@adobe/aem-react-editable-components';
   import { Text, TextEditConfig } from './AEMText';
   import Image, { ImageEditConfig } from './AEMImage';
   
   export const AEMCard = withMappable(Container, {
     resourceType: 'wknd-spa/components/imagecard'
   });
   
   MapTo('wknd-spa/components/text')(Text, TextEditConfig);
   MapTo('wknd-spa/components/image')(Image, ImageEditConfig);
   ```

1. Comme il n’y a pas de contenu pour le composant `imagecard` , ajoutez la carte à la page. Incluez le conteneur existant à partir d’AEM dans le SPA.
   * S’il existe déjà un conteneur dans le projet AEM, nous pouvons l’inclure dans le SPA à la place et ajouter le composant au conteneur à partir d’AEM à la place.
   * Assurez-vous que le composant de carte est mappé sur le type de ressource correspondant dans le SPA.

   ```javascript
   <ResponsiveGrid
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid' />
   ```

1. Ajoutez le composant `wknd-spa/components/imagecard` créé aux composants autorisés pour le composant de conteneur [dans le modèle de page.](/help/sites-cloud/authoring/features/templates.md)

Désormais, le composant `imagecard` peut être directement ajouté au conteneur dans l’éditeur d’AEM.

![Carte composite dans l’éditeur](assets/composite-card.gif)

### Le composant et son contenu requis existent tous deux dans votre projet AEM. {#both-exist}

Si le contenu existe dans AEM, il peut être directement inclus dans le SPA en fournissant le chemin d’accès au contenu.

```javascript
<AEMCard
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid/imagecard' />
```

![Chemin composite dans la structure de noeud](assets/composite-path.png)

Le composant `AEMCard` est identique à la valeur [définie dans le cas d’utilisation précédent.](#content-does-not-exist) Ici, le contenu défini à l’emplacement ci-dessus dans le projet AEM est inclus dans le SPA.
