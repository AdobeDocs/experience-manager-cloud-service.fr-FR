---
title: Modification d’une SPA externe dans AEM
description: Ce document décrit les étapes recommandées pour charger une SPA autonome vers une instance AEM, ajouter des sections de contenu modifiables et permettre la création.
exl-id: 7978208d-4a6e-4b3a-9f51-56d159ead385
feature: Developing
role: Admin, Developer
index: false
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2370'
ht-degree: 97%

---


# Modification d’une SPA externe dans AEM {#editing-external-spa-within-aem}

Lorsque vous décidez du [niveau d’intégration](/help/implementing/developing/headful-headless.md) à appliquer entre votre SPA externe et AEM, pensez que vous aurez souvent à modifier et à afficher la SPA dans AEM.

{{ue-over-spa}}

## Vue d’ensemble {#overview}

Ce document décrit les étapes recommandées pour charger une SPA autonome vers une instance AEM, ajouter des sections de contenu modifiables et permettre la création.

## Prérequis {#prerequisites}

Les conditions préalables sont simples.

* Assurez-vous que l’instance d’AEM s’exécute localement.
* Créez un projet de base de SPA AEM à l’aide de [l’archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr?#available-properties).
   * Il s’agit de la base du projet AEM qui est mis à jour pour inclure la SPA externe.
   * Pour les exemples de ce document, nous utilisons [le projet SPA WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=fr#spa-editor) comme point de départ.
* Disposez de la SPA React externe opérationnelle que vous souhaitez intégrer.

## Chargement de la SPA vers le projet AEM {#upload-spa-to-aem-project}

Vous devez tout d’abord charger la SPA externe vers votre projet AEM.

1. Remplacez `src` dans le dossier de projet `/ui.frontend` par le dossier `src` de votre application React.
1. Incluez toutes les dépendances supplémentaires dans le `package.json` de l’application dans le fichier `/ui.frontend/package.json`.
   * Vérifiez que les versions des dépendances du SDK de la SPA font partie des [versions recommandées](/help/implementing/developing/hybrid/getting-started-react.md#dependencies).
1. Incluez toutes les personnalisations dans le dossier `/public`.
1. Incluez tous les scripts ou styles intégrés ajoutés dans le fichier `/public/index.html`.

## Configuration de la SPA distante {#configure-remote-spa}

Maintenant que la SPA externe fait partie de votre projet AEM, vous devez la configurer dans AEM.

### Inclusion des packages du SDK SPA Adobe {#include-spa-sdk-packages}

Pour tirer parti des fonctionnalités de SPA AEM, vous pouvez utiliser les dépendances des trois packages suivants.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/login?next=/package/@adobe/aem-spa-model-manager)

Le package `@adobe/aem-spa-page-model-manager` fournit l’API permettant d’initialiser un gestionnaire de modèle et de récupérer le modèle à partir de l’instance AEM. Ce modèle peut ensuite être utilisé pour effectuer le rendu des composants AEM à l’aide d’API provenant de `@adobe/aem-react-editable-components` et `@adobe/aem-spa-component-mapping`.

#### Installation {#installation}

Exécutez la commande `npm` suivante pour pouvoir installer les packages requis.

```shell
npm install --save @adobe/aem-spa-component-mapping @adobe/aem-spa-page-model-manager @adobe/aem-react-editable-components
```

### Initialisation de ModelManager {#model-manager-initialization}

Avant le rendu de l’application, [`ModelManager`](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager) doit être initialisé pour gérer la création du `ModelStore` AEM.

Cette initialisation doit être effectuée dans le fichier `src/index.js` de votre application ou à l’endroit où la racine de l’application est générée.

Pour effectuer cette initialisation, vous pouvez utiliser l’API `initializationAsync` fournie par le `ModelManager`.

La capture d’écran suivante montre comment activer l’initialisation de `ModelManager` dans une application React simple. La seule contrainte est que `initializationAsync` doit être appelée avant `ReactDOM.render()`.

![Initialiser ModelManager](assets/external-spa-initialize-modelmanager.png)

Dans cet exemple, `ModelManager` est initialisé et un `ModelStore` vide est créé.

`initializationAsync` peut éventuellement accepter un objet `options` comme paramètre :

* `path` – Lors de l’initialisation, le modèle au niveau du chemin d’accès défini est récupéré et stocké dans le `ModelStore`. Ce chemin peut être utilisé pour récupérer le `rootModel` à l’initialisation, le cas échéant.
* `modelClient` – Permet de fournir un client personnalisé chargé de récupérer le modèle.
* `model` – Un objet `model` transmis en tant que paramètre généralement renseigné lors de l’utilisation du rendu côté serveur.

### Composants feuille AEM modifiables {#authorable-leaf-components}

1. Créez/identifiez un composant AEM pour lequel un composant React modifiable est créé. Dans cet exemple il utilise le composant texte du projet WKND.

   ![Composant texte WKND](assets/external-spa-text-component.png)

1. Créez un simple composant texte React dans la SPA. Dans cet exemple, un nouveau fichier `Text.js` a été créé avec le contenu suivant.

   ![Text.js](assets/external-spa-textjs.png)

1. Créez un objet de configuration pour spécifier les attributs requis pour activer la modification AEM.

   ![Création d’un objet de configuration](assets/external-spa-config-object.png)

   * `resourceType` est nécessaire pour pouvoir mapper le composant React au composant AEM et activer la modification lors de l’ouverture dans l’éditeur AEM.

1. Utilisez la fonction Wrapper `withMappable`.

   ![Utiliser withMappable](assets/external-spa-withmappable.png)

   Cette fonction Wrapper mappe le composant React au `resourceType` AEM spécifié dans la configuration et active les capacités de modification en l’ouvrant dans l’éditeur AEM. Pour les composants autonomes, cette fonction récupère également le contenu du modèle pour le nœud spécifique.

   >[!NOTE]
   >
   >Dans cet exemple, il existe des versions distinctes du composant : les composants AEM encapsulés et les composants React non encapsulés. La version encapsulée doit être utilisée lors de l’utilisation explicite du composant. Lorsque le composant fait partie d’une page, vous pouvez continuer à utiliser le composant par défaut comme dans l’éditeur de SPA.

1. Générez le contenu dans le composant.

   Les propriétés JCR du composant texte apparaissent comme suit dans AEM.

   ![Propriétés du composant texte](assets/external-spa-text-properties.png)

   Ces valeurs sont transmises en tant que propriétés au composant React `AEMText` créé et peuvent être utilisées pour effectuer le rendu du contenu.

   ```javascript
   import React from 'react';
   import { withMappable } from '@adobe/aem-react-editable-components';
   
   export const TextEditConfig = {
       // Empty component placeholder label
       emptyLabel:'Text', 
       isEmpty:function(props) {
          return !props || !props.text || props.text.trim().length < 1;
       },
       // resourcetype of the AEM counterpart component
       resourceType:'wknd-spa-react/components/text'
   };
   
   const Text = ({ text }) => (<div>{text}</div>);
   
   export default Text;
   
   export const AEMText = withMappable(Text, TextEditConfig);
   ```

   C’est ainsi que le composant apparaît une fois que les configurations AEM sont terminées.

   ```javascript
   const Text = ({ cqPath, richText, text }) => {
      const richTextContent = () => (
         <div className="aem_text" id={cqPath.substr(cqPath.lastIndexOf('/') + 1)} data-rte-editelement dangerouslySetInnerHTML={{__html: text}}/>
      );
      return richText ? richTextContent() : (<div className="aem_text">{text}</div>);
   };
   ```

   >[!NOTE]
   >
   >Dans cet exemple, d’autres personnalisations ont été apportées au composant rendu pour correspondre au composant de texte existant. Cette personnalisation n’est toutefois pas liée à la création dans AEM.

#### Ajouter des composants modifiables à la page {#add-authorable-component-to-page}

Une fois les composants React modifiables créés, vous pouvez les utiliser dans toute l’application.

Prenons un exemple de page dans lequel vous devez ajouter un texte du projet SPA WKND. Pour cet exemple, vous voulez afficher le texte « Hello World! » à `/content/wknd-spa-react/us/en/home.html`.

1. Déterminez le chemin d’accès du nœud à afficher.

   * `pagePath` : page qui contient le nœud, dans cet exemple, `/content/wknd-spa-react/us/en/home`
   * `itemPath` : chemin d’accès au nœud dans la page, dans cet exemple, `root/responsivegrid/text`
      * Il s’agit des noms des éléments contenants sur la page.

   ![Chemin du nœud](assets/external-spa-path.png)

1. Ajoutez le composant à la position requise sur la page.

   ![Ajouter des composants à la page](assets/external-spa-add-component.png)

   Le composant `AEMText` peut être ajouté à la position requise sur la page avec les valeurs `pagePath` et `itemPath` définies en tant que propriétés. `pagePath` est une propriété obligatoire.

#### Vérification de la modification du contenu texte dans AEM {#verify-text-edit}

Testez maintenant le composant sur l’instance AEM en cours d’exécution.

1. Exécutez la commande Maven suivante à partir du répertoire `aem-guides-wknd-spa` pour générer et déployer le projet sur AEM.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Sur votre instance AEM, accédez à `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`.

![Modification de la SPA dans AEM](assets/external-spa-edit-aem.png)

Le composant `AEMText` est désormais modifiable sur AEM.

### Pages AEM modifiables {#aem-authorable-pages}

1. Identifiez une page à ajouter pour la création dans la SPA. Cet exemple utilise `/content/wknd-spa-react/us/en/home.html`.
1. Créez un fichier (par exemple, `Page.js`) pour le composant de page modifiable. Utilisez le composant de page fourni dans `@adobe/cq-react-editable-components`.
1. Répétez l’étape 4 de la section [Composants feuille AEM modifiables](#authorable-leaf-components). Utilisez la fonction Wrapper `withMappable` sur le composant.
1. Comme précédemment, appliquez `MapTo` aux types de ressources AEM pour tous les composants enfants de la page.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >Dans cet exemple, le composant de texte React non encapsulé est utilisé à la place de l’élément encapsulé `AEMText` créé précédemment. En effet, lorsque le composant fait partie d’une page/d’un conteneur et qu’il n’est pas autonome, le conteneur s’occupe de mapper récursivement le composant. De plus, l’activation des fonctionnalités de création et du wrapper supplémentaire n’est pas nécessaire pour chaque enfant.

1. Pour ajouter une page autorisée dans la SPA, suivez les mêmes étapes de la section [Ajout de composants modifiables à la page](#add-authorable-component-to-page). Ici, vous pouvez ignorer la propriété `itemPath`.

#### Vérifier le contenu de la page sur AEM {#verify-page-content}

Pour vérifier que la page peut être modifiée, suivez les mêmes étapes que dans la section [Vérification de la modification du contenu texte dans AEM](#verify-text-edit).

![Modification d’une page dans AEM](assets/external-spa-edit-page.png)

La page est désormais modifiable dans AEM avec un conteneur de disposition et un composant texte enfant.

### Composants feuille virtuels {#virtual-leaf-components}

Dans les exemples précédents, vous avez ajouté des composants à la SPA avec le contenu AEM existant. Toutefois, il arrive que le contenu n’ait pas encore été créé dans AEM, mais qu’il doive être ajouté ultérieurement par l’auteur ou l’autrice du contenu. Pour ce faire, dans ce scénario, l’équipe de développement front-end peut ajouter des composants aux emplacements appropriés dans la SPA. Ces composants affichent des espaces réservés lorsqu’ils sont ouverts dans l’éditeur dans AEM. Une fois que le contenu est ajouté par l’auteur ou l’autrice du contenu dans ces espaces réservés, les nœuds sont créés dans la structure JCR et le contenu est conservé. Le composant créé permet le même ensemble d’opérations que les composants feuille autonomes.

Dans cet exemple, vous réutilisez le composant `AEMText` créé précédemment. Vous devez ajouter un nouveau texte sous le composant texte existant sur la page d’accueil WKND. L’ajout de composants est le même que pour les composants feuille normaux. Cependant, `itemPath` peut être mis à jour avec le chemin d’accès pour le nouveau composant.

Étant donné que le nouveau composant doit être ajouté sous le texte existant à l’adresse `root/responsivegrid/text`, le nouveau chemin est `root/responsivegrid/{itemName}`.

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

Le composant `TestPage` ressemble à ce qui suit après l’ajout du composant virtuel.

![Test du composant virtuel](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Assurez-vous que le composant `AEMText` a son `resourceType` défini dans la configuration pour activer cette fonctionnalité.

Vous pouvez maintenant déployer les modifications sur AEM en suivant les étapes de la section [Vérification de la modification du contenu texte dans AEM](#verify-text-edit). Un espace réservé s’affiche pour le nœud `text_20` encore non existant.

![Le nœud text_20 dans aem](assets/external-spa-text20-aem.png)

Lorsque l’auteur du contenu met à jour ce composant, un nœud `text_20` est créé sur `root/responsivegrid/text_20` dans `/content/wknd-spa-react/us/en/home`.

![Le nœud text20](assets/external-spa-text20-node.png)

#### Exigences et restrictions {#limitations}

Il existe plusieurs exigences pour ajouter des composants feuille virtuels et certaines limites.

* La propriété `pagePath` est obligatoire pour créer un composant virtuel.
* Le nœud de page fourni au chemin d’accès dans `pagePath` doit exister dans le projet AEM.
* Le nom du nœud à créer doit être fourni dans le `itemPath`.
* Le composant peut être créé à n’importe quel niveau.
   * Si vous indiquez `itemPath='text_20'` dans l’exemple précédent, le nœud est créé directement sous la page, à savoir `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Le chemin d’accès où le nœud doit être créé doit être valide lorsqu’il est fourni par `itemPath`.
   * Dans cet exemple, `root/responsivegrid` doit exister pour que le nœud `text_20` puisse y être créé.
* Seule la création de composants feuille est prise en charge. Les conteneurs et pages virtuels seront pris en charge dans les versions futures.

### Conteneurs virtuels {#virtual-containers}

La possibilité d’ajouter des conteneurs, même si le conteneur correspondant n’est pas encore créé dans AEM, est prise en charge. Le concept et l’approche sont semblables à celles des [composants feuille virtuels](#virtual-leaf-components).

L’équipe de développement front-end peut ajouter les composants de conteneur aux emplacements appropriés dans la SPA. Ces composants affichent des espaces réservés lorsqu’ils sont ouverts dans l’éditeur dans AEM. L’auteur ou l’autrice peut ensuite ajouter des composants et leur contenu au conteneur, ce qui crée les nœuds requis dans la structure JCR.

Par exemple, si un conteneur existe déjà à l’adresse `/root/responsivegrid` et que l’équipe de développement souhaite ajouter un nouveau conteneur enfant :

![Emplacement du conteneur](assets/container-location.png)

`newContainer` n’existe pas encore dans AEM.

Lors de la modification de la page contenant ce composant dans AEM, un espace réservé vide pour un conteneur s’affiche dans lequel l’auteur peut ajouter du contenu.

![Espace réservé du conteneur](assets/container-placeholder.png)

![Emplacement du conteneur dans JCR](assets/container-jcr-structure.png)

Une fois que l’auteur ajoute un composant enfant au conteneur, le nouveau nœud de conteneur est créé avec le nom correspondant dans la structure JCR.

![Conteneur avec contenu](assets/container-with-content.png)

![Conteneur avec contenu dans JCR](assets/container-with-content-jcr.png)

Vous pouvez désormais ajouter plus de composants et de contenu au conteneur en fonction des besoins de l’auteur pu l’autrice, et les modifications sont conservées.

#### Exigences et restrictions {#container-limitations}

Il existe plusieurs exigences pour ajouter des conteneurs virtuels et certaines limites.

* La politique permettant de déterminer les composants qui peuvent être ajoutés est héritée du conteneur parent.
* Le parent immédiat du conteneur à créer doit exister dans AEM.
   * Si le conteneur `root/responsivegrid` existe dans le conteneur AEM, un nouveau conteneur peut être créé en indiquant le chemin d’accès `root/responsivegrid/newContainer`.
   * Cependant, `root/responsivegrid/newContainer/secondNewContainer` n’est pas possible.
* Un seul nouveau niveau de composant peut être créé à la fois.

## Personnalisations supplémentaires {#additional-customizations}

Si vous avez suivi les exemples précédents, votre SPA externe est désormais modifiable dans AEM. Cependant, vous pouvez personnaliser encore davantage d’autres aspects de votre SPA externe.

### ID de nœud racine {#root-node-id}

Par défaut, vous pouvez supposer que l’application React est rendue dans un `div` de l’ID d’élément `spa-root`. Au besoin, cette syntaxe peut être personnalisée.

Par exemple, supposons que vous ayez une SPA dans laquelle l’application est rendue dans un `div` de l’ID d’élément `root`. Cette syntaxe doit se refléter dans trois fichiers.

1. Dans le fichier `index.js` de l’application React (ou à l’endroit où `ReactDOM.render()` est appelé)

   ![ReactDOM.render() dans le fichier index.js](assets/external-spa-root-index.png)

1. Dans le fichier `index.html` de l’application React

   ![Index.html de l’application](assets/external-spa-index.png)

1. Dans le corps du composant de page de l’application AEM, opération possible en deux étapes :

   1. Créez un fichier `body.html` pour le composant de page.

   ![Création d’un fichier body.html](assets/external-spa-update-body.gif)

   1. Ajoutez l’élément racine dans le nouveau fichier `body.html`.

   ![Ajout de l’élément racine à body.html.](assets/external-spa-add-root.png)

### Modification d’une SPA React avec le routage {#editing-react-spa-with-routing}

Si l’application SPA React externe comporte plusieurs pages, [elle peut utiliser le routage pour déterminer la page ou le composant à rendre](/help/implementing/developing/hybrid/routing.md). Le cas d’utilisation typique consiste à faire correspondre l’URL actuellement principale au chemin d’accès fourni pour un itinéraire. Pour permettre la modification sur de telles applications activées pour le routage, le chemin d’accès à comparer doit être modifié pour pouvoir s’adapter aux informations spécifiques à AEM.

Dans l’exemple suivant, vous avez une application React simple de deux pages. La page à rendre est déterminée en comparant le chemin d’accès fourni au routeur avec l’URL active. Par exemple, si vous utilisez `mydomain.com/test`, `TestPage` est rendue.

![Routage dans une SPA externe](assets/external-spa-routing.png)

Pour activer la modification dans AEM pour cet exemple de SPA, vous devez suivre les étapes suivantes.

1. Identifiez le niveau racine pour AEM.

   * Pour votre exemple, considérez wknd-spa-response/us/en comme la racine du SPA. Cette racine signifie que tout ce qui précède ce chemin ne concerne que des pages ou du contenu AEM.

1. Créez une page au niveau requis.

   * Dans cet exemple, la page à modifier est `mydomain.com/test`. `test` se trouve dans le chemin racine de l’application. Ce chemin racine doit également être conservé lors de la création de la page dans AEM. Par conséquent, vous pouvez créer une page au niveau racine défini à l’étape précédente.
   * La page créée doit porter le même nom que la page à modifier. Dans cet exemple, pour `mydomain.com/test`, la page créée doit être `/path/to/aem/root/test`.

1. Ajoutez des assistants pour le routage de la SPA.

   * La page créée ne peut pas encore générer le contenu attendu dans AEM. En effet, le routeur cherche le chemin d’accès `/test` alors que le chemin d’accès actif d’AEM est `/wknd-spa-react/us/en/test`. Pour prendre en compte la partie spécifique à AEM de l’URL, vous devez ajouter des fonctions d’aide côté SPA.

   ![Assistant de routage](assets/external-spa-router-helper.png)

   * L’assistant `toAEMPath` fourni par `@adobe/cq-spa-page-model-manager` peut être utilisé. Elle adapte le chemin d’accès fourni pour que le routage intègre les portions spécifiques à AEM lorsque l’application est ouverte sur une instance AEM. Elle accepte trois paramètres :
      * Le chemin d’accès requis pour le routage
      * L’URL d’origine de l’instance AEM dans laquelle la SPA est modifiée
      * La racine du projet sur AEM, telle que déterminée lors de la première étape

   * Ces valeurs peuvent être définies en tant que variables d’environnement pour plus de flexibilité.

1. Vérifiez la modification de la page dans AEM.

   * Déployez le projet dans AEM et accédez à la page de `test` créée. Le contenu de la page est désormais rendu et les composants AEM sont modifiables.

## Restrictions du framework {#framework-limitations}

Le composant RemotePage s’attend à ce que l’implémentation fournisse un manifeste de ressource tel que [webpack-manifest-plugin sur GitHub](https://github.com/shellscape/webpack-manifest-plugin). Le composant RemotePage, en revanche, a été testé uniquement pour fonctionner avec le framework React (et Next.js via le composant remote-page-next) et il ne prend donc pas en charge le chargement à distance d’applications à partir d’autres frameworks tels qu’Angular.

## Ressources supplémentaires {#additional-resources}

Les documents de référence suivants peuvent être utiles pour comprendre le fonctionnement des SPA dans le contexte d’AEM.

* [Couplage et découplage dans AEM](/help/implementing/developing/headful-headless.md)
* [Archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)
* [Projet de SPA WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=fr)
* [Prise en main des SPA dans AEM avec React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Documents de référence relatifs aux SPA (référence de l’API)](/help/implementing/developing/hybrid/reference-materials.md)
* [Plan directeur d’applications sur une seule page (SPA) et PageModelManager](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager)
* [Routage du modèle de SPA](/help/implementing/developing/hybrid/routing.md)
