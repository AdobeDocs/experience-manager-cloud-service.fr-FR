---
title: Guide de référence des composants
description: Guide de référence du développeur pour les détails des composants et de leur structure
translation-type: tm+mt
source-git-commit: 3f31ced24ab8af942b848a8c9ac6bd53ceb5f3b1
workflow-type: tm+mt
source-wordcount: '3390'
ht-degree: 34%

---


# Guide de référence des composants {#components-reference-guide}

Les composants sont au coeur de la création d&#39;une expérience en AEM. Les [Composants de base](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) et l&#39;archétype de projet [AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) facilitent la prise en main d&#39;un ensemble d&#39;outils de composants robustes et prêts à l&#39;emploi. Le [didacticiel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) explique au développeur comment utiliser ces outils et comment créer des composants personnalisés afin de créer un nouveau site AEM.

>[!TIP]
>
>Avant de faire référence à ce document, assurez-vous d&#39;avoir suivi le [tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) et de connaître ainsi les [composants de base](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) et l&#39;archétype de projet [AEM.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

Étant donné que le tutoriel WKND couvre la plupart des cas d&#39;utilisation, ce document n&#39;est destiné qu&#39;à titre de supplément à ces ressources. Il fournit des détails techniques détaillés sur la manière dont les composants sont structurés et configurés dans AEM et n&#39;est pas conçu comme un guide de prise en main.

## Présentation {#overview}

Cette section décrit les concepts et les problèmes majeurs et sert d’introduction aux informations dont vous avez besoin pour développer vos propres composants.

### Planification {#planning}

Avant de commencer à configurer ou coder réellement votre composant, vous devez vous demander :

* de quoi avez-vous besoin exactement pour le nouveau composant ?
* Devez-vous créer votre composant de toutes pièces ou pouvez-vous hériter des bases d’un composant existant ?
* Votre composant demande-t-il une logique pour sélectionner/manipuler le contenu ?
   * La logique doit rester distincte de la couche de l’interface utilisateur. HTL est conçu pour faciliter cette distinction.
* Votre composant a-t-il besoin d’une mise en forme CSS ?
   * La mise en forme CSS doit rester distincte des définitions de composants. Définissez des conventions pour nommer vos éléments HTML afin de pouvoir les modifier au moyen de fichiers CSS externes.
* Quelles implications de sécurité votre nouveau composant peut-il introduire ?

### Réutilisation des composants existants {#reusing-components}

Avant d’investir du temps dans la création d’un composant entièrement nouveau, pensez à personnaliser ou à étendre les composants existants. [Les ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) composants principaux offrent une suite de composants flexibles, robustes et bien testés prêts à la production.

#### Extension des composants principaux {#extending-core-components}

Les composants principaux offre également [des modèles de personnalisation clairs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html) que vous pouvez utiliser pour les adapter aux besoins de votre propre projet.

#### Composants de superposition {#overlying-components}

Les composants peuvent également être redéfinis avec une superposition [](/help/implementing/developing/introduction/overlays.md) en fonction de la logique du chemin de recherche. Cependant, dans ce cas, la fusion de ressources [Sling](/help/implementing/developing/introduction/sling-resource-merger.md) ne sera pas déclenchée et `/apps` doit définir l&#39;ensemble de l&#39;incrustation.

#### Étendre les boîtes de dialogue des composants {#extending-component-dialogs}

Il est également possible de remplacer une boîte de dialogue de composant en utilisant le Sling Resource Merger et en définissant la propriété `sling:resourceSuperType`.

Cela signifie que vous n&#39;avez qu&#39;à redéfinir les différences requises, au lieu de redéfinir la boîte de dialogue dans son ensemble.

### Logique de contenu et balisage de rendu  {#content-logic-and-rendering-markup}

Votre composant est rendu dans le langage [HTML.](https://www.w3schools.com/htmL/html_intro.asp) Votre composant doit définir les balises HTML nécessaires pour réaliser le rendu du contenu selon les besoins, dans les environnements de création et de publication.

Il est recommandé de garder le code responsable du balisage et du rendu distinct de celui qui contrôle la logique utilisée pour sélectionner le contenu du composant.

Cette approche est compatible avec [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html), un langage de modèle intentionnellement limité pour s’assurer qu’un vrai langage de programmation est utilisé afin de définir la logique métier sous-jacente. Ce mécanisme met en évidence le code appelé pour une vue donnée et, si nécessaire, autorise une logique spécifique pour différentes vues du même composant.

Cette logique (facultative) peut être implémentée de différentes manières et est appelée à partir de HTL avec des commandes spécifiques :

* L’utilisation de Java - [L’API d’utilisation Java HTML](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html) permet à un fichier HTML d’accéder aux méthodes d’assistance dans une classe Java personnalisée. Cela permet d’utiliser le code Java pour implémenter la logique de sélection et de configuration du contenu du composant.
* Utilisation de JavaScript - [L&#39;API d&#39;utilisation JavaScript HTML](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/use-api-javascript.html) permet à un fichier HTML d&#39;accéder au code d&#39;assistance écrit en JavaScript. Cela permet d’utiliser le code JavaScript pour implémenter la logique de sélection et de configuration du contenu du composant.
* Utilisation des bibliothèques côté client - Les sites Web modernes dépendent fortement du traitement côté client piloté par du code JavaScript et CSS complexe. Pour plus d&#39;informations, consultez le document [Utilisation de bibliothèques côté client sur AEM en tant que Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

### Développer ses propres composants {#developing-your-own-components}

Dév du contenu ici ?

## Structure de composants {#structure}

La structure d&#39;un composant AEM est puissante et flexible. Les principaux éléments sont les suivants :

* [Type de ressource](#resource-type)
* [Définition du composant](#component-definition)
* [Propriétés et nœuds enfants d’un composant](#properties-and-child-nodes-of-a-component)
* [Boîtes de dialogue](#dialogs)
* [Boîtes de dialogue de conception](#design-dialogs)

### Type de ressource {#resource-type}

Le type de ressource est un élément clé de la structure.

* La structure de contenu déclare les intentions.
* Le type de ressource les implémente.

Il s&#39;agit d&#39;une abstraction qui permet de s&#39;assurer que même lorsque l&#39;apparence et le ressenti changent au fil du temps, l&#39;intention reste le temps.

### Définition d&#39;un composant {#component-definition}

La définition d’un composant peut être décomposée comme suit :

* Les composants AEM sont basés sur [Sling.](https://sling.apache.org/documentation.html)
* aem composants sont situés sous `/libs/core/wcm/components`.
* Les composants spécifiques au projet/site sont situés sous `/apps/<myApp>/components`.
* Les composants standard d’AEM sont définis comme `cq:Component` et possèdent les éléments clés suivants :
   * Propriétés jcr - liste des propriétés jcr. Il s&#39;agit de variables et certaines peuvent être facultatives par l&#39;intermédiaire de la structure de base d&#39;un noeud de composant, de ses propriétés et de ses sous-noeuds, définies par la définition `cq:Component`.
   * Ressources - Ces ressources définissent les éléments statiques utilisés par le composant.
   * Scripts : ils sont utilisés pour implémenter le comportement de l&#39;instance résultante du composant.

#### Propriétés vitales {#vital-properties}

* **Nœud racine** :
   * `<mycomponent> (cq:Component)` - Noeud de hiérarchie du composant.
* **Propriétés vitales** :
   * `jcr:title` - Titre du composant ; par exemple, utilisé comme étiquette lorsque le composant est répertorié dans le  [navigateur de ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) composants et la console  [de composants](/help/sites-cloud/authoring/features/components-console.md)
   * `jcr:description` - Description du composant ; utilisé comme indicateur de survol de la souris dans le navigateur de composants et la console de composants
   * Voir la section [Icône de composant](#component-icon) pour plus de détails.
* **Nœuds enfants essentiels** :
   * `cq:editConfig (cq:EditConfig)` - Définit les propriétés de modification du composant et permet au composant d&#39;apparaître dans l&#39;explorateur de composants
      * Si le composant comporte une boîte de dialogue, elle s’affiche automatiquement dans le navigateur de composants ou le sidekick, même si cq:editConfig n’existe pas.
   * `cq:childEditConfig (cq:EditConfig)` - Contrôle les aspects de l&#39;interface utilisateur de création pour les composants enfants qui ne définissent pas leurs propres  `cq:editConfig`.
   * `cq:dialog (nt:unstructured)` - Boîte de dialogue pour ce composant. Définit l’interface permettant à l’utilisateur de configurer le composant et/ou de modifier le contenu.
   * `cq:design_dialog (nt:unstructured)` - Modification de la conception pour ce composant

#### Icône de composant {#component-icon}

L’icône ou l’abréviation du composant est définie au moyen des propriétés JCR du composant lorsque celui-ci est créé par le développeur. Ces propriétés sont évaluées dans l’ordre suivant, la première propriété valide trouvée étant utilisée.

1. `cq:icon` - Propriété de chaîne pointant vers une icône standard dans la  [bibliothèque d&#39;interface utilisateur ](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) Coral pour s&#39;afficher dans le navigateur de composants
   * Utilisez la valeur de l’attribut HTML de l’icône Coral.
1. `abbreviation` - Propriété de chaîne servant à personnaliser l’abréviation du nom du composant dans le navigateur de composants
   * L’abréviation devrait être limitée à deux caractères.
   * Une chaîne vide crée l&#39;abréviation à partir des deux premiers caractères de la propriété `jcr:title`.
      * Par exemple « Im » pour Image
      * Le titre localisé sera utilisé pour construire l’abréviation.
   * L’abréviation n’est traduite que si le composant possède une propriété `abbreviation_commentI18n`, qui est ensuite utilisée comme indice de traduction.
1. `cq:icon.png` ou  `cq:icon.svg` - Icône pour ce composant, qui s&#39;affiche dans l&#39;explorateur de composants
   * La taille des icônes des composants standard est de 20 x 20 pixels.
      * Les icônes plus grandes sont réduites (côté client).
   * La couleur recommandée est rgb(112, 112, 112) > #707070
   * L’arrière-plan des icônes de composants standard est transparent.
   * Seuls les fichiers `.png` et `.svg` sont pris en charge.
   * Si vous effectuez une importation à partir du système de fichiers via le module externe Eclipse, les noms de fichier doivent être ignorés sous la forme `_cq_icon.png` ou `_cq_icon.svg`, par exemple.
   * `.png` prend le dessus  `.svg` si les deux sont présents.

Si aucune des propriétés ci-dessus (`cq:icon`, `abbreviation`, `cq:icon.png` ou `cq:icon.svg`) n&#39;est trouvée sur le composant :

* Le système recherche les mêmes propriétés sur les super-composants selon la propriété `sling:resourceSuperType`.
* Si aucune abréviation ou une abréviation vide n&#39;est trouvée au niveau du super-composant, le système crée l&#39;abréviation à partir des premières lettres de la propriété `jcr:title` du composant actif.

Pour annuler l’héritage des icônes à partir de super-composants, la définition d’une propriété `abbreviation` vide sur le composant rétablit le comportement par défaut.

La [console de composants](/help/sites-cloud/authoring/features/components-console.md#component-details) affiche la manière dont l&#39;icône d&#39;un composant particulier est définie.

#### Exemple d’icône SVG {#svg-icon-example}

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" id="Layer_1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink" x="0px" y="0px"
     width="20px" height="20px" viewBox="0 0 20 20" enable-background="new 0 0 20 20" xml:space="preserve">
    <ellipse cx="5" cy="5" rx="3" ry="3" fill="#707070"/>
    <ellipse cx="15" cy="5" rx="4" ry="4" fill="#707070"/>
    <ellipse cx="5" cy="15" rx="5" ry="5" fill="#707070"/>
    <ellipse cx="15" cy="15" rx="4" ry="4" fill="#707070"/>
</svg>
```

### Propriétés et nœuds enfants d’un composant {#properties-and-child-nodes-of-a-component}

La plupart des nœuds/propriétés nécessaires pour définir un composant sont communs aux deux interfaces utilisateur, les différences restant indépendantes pour que votre composant puisse fonctionner dans les deux environnements.

Un composant est un nœud de type `cq:Component` et possède les propriétés et les nœuds enfants suivants :

| Nom | Type | Description |
|---|---|---|
| `.` | `cq:Component` | Ceci représente le composant actuel. Un composant est de type de noeud `cq:Component`. |
| `componentGroup` | `String` | Il s&#39;agit du groupe sous lequel le composant peut être sélectionné dans l&#39;[Explorateur de composants.](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) Une valeur commençant par  `.` est utilisée pour les composants qui ne peuvent pas être sélectionnés dans l’interface utilisateur, tels que les composants de base dont héritent d’autres composants. |
| `cq:isContainer` | `Boolean` | Cela indique si le composant est un composant de conteneur et peut donc contenir d’autres composants tels qu’un système de paragraphe. |
| `cq:dialog` | `nt:unstructured` | Il s&#39;agit de la définition de la boîte de dialogue de modification du composant. |
| `cq:design_dialog` | `nt:unstructured` | Il s’agit de la définition de la boîte de dialogue de conception du composant. |
| `cq:editConfig` | `cq:EditConfig` | Ceci définit la configuration de [modification du composant.](#edit-behavior) |
| `cq:htmlTag` | `nt:unstructured` | Cette opération renvoie d’autres attributs de balise qui sont ajoutés à la balise HTML environnante. Active l’ajout d’attributs aux divs générés automatiquement. |
| `cq:noDecoration` | `Boolean` | Si la valeur est true, le composant n’est pas rendu avec les classes div et css générées automatiquement. |
| `cq:template` | `nt:unstructured` | S’il est trouvé, ce noeud sera utilisé comme modèle de contenu lorsque le composant est ajouté à partir de l’explorateur de composants. |
| `jcr:created` | `Date` | Il s’agit de la date de création du composant. |
| `jcr:description` | `String` | Description du composant. |
| `jcr:title` | `String` | Titre du composant. |
| `sling:resourceSuperType` | `String` | Lorsqu’il est défini, le composant hérite de ce composant. |
| `component.html` | `nt:file` | Il s’agit du fichier de script HTML du composant. |
| `cq:icon` | `String` | Cette valeur pointe vers l’icône [du composant](#component-icon) et s’affiche dans l’explorateur de composants. |

Si nous examinons le composant **Texte**, nous voyons plusieurs de ces éléments :

![Structure du composant de texte](assets/components-text.png)

Les propriétés d’intérêt particulier sont les suivantes :

* `jcr:title` - Titre du composant utilisé pour identifier le composant dans l&#39;explorateur de composants.
* `jcr:description` - Description du composant.
* `sling:resourceSuperType` - Indique le chemin d&#39;héritage lors de l&#39;extension d&#39;un composant (en remplaçant une définition).

Les nœuds d’enfant d’un intérêt particulier sont les suivants :

* `cq:editConfig` - Contrôle les aspects visuels du composant lors de la modification.
* `cq:dialog` - Définit la boîte de dialogue de modification du contenu de ce composant.
* `cq:design_dialog` - Indique les options de modification de la conception pour ce composant.

### Boîtes de dialogue {#dialogs}

Les boîtes de dialogue constituent un élément clé de votre composant, car elles offrent une interface permettant aux auteurs de configurer le composant sur une page de contenu et fournissent des entrées pour ce composant. Voir la [documentation de création](/help/sites-cloud/authoring/fundamentals/editing-content.md) pour en savoir plus sur la façon dont les auteurs de contenu interagissent avec les composants.

Selon la complexité du composant, votre boîte de dialogue peut nécessiter un ou plusieurs onglets.

Boîtes de dialogue pour les composants AEM :

* Sont des noeuds `cq:dialog` de type `nt:unstructured`.
* Se trouvent sous leurs noeuds `cq:Component` et à côté de leurs définitions de composants.
* Définissez la boîte de dialogue de modification du contenu de ce composant.
* Sont définis à l’aide des composants de l’interface utilisateur Granite.
* sont rendus côté serveur (en tant que composants Sling), en fonction de leur structure de contenu et de la propriété `sling:resourceType`.
* Contient une structure de noeud décrivant les champs dans la boîte de dialogue
   * Ces noeuds sont `nt:unstructured` avec la propriété `sling:resourceType` requise.

![Définition de boîte de dialogue du composant Titre](assets/components-title-dialog.png)

Dans la boîte de dialogue, des champs individuels sont définis :

![Champs de la définition de boîte de dialogue du composant Titre](assets/components-title-dialog-items.png)

### Boîtes de dialogue de conception {#design-dialogs}

Les boîtes de dialogue de conception sont similaires aux boîtes de dialogue utilisées pour modifier et configurer le contenu, mais elles offrent aux auteurs de modèles l’interface leur permettant de procéder à une préconfiguration et de fournir des détails de conception pour ce composant sur un modèle de page. Les modèles de page sont ensuite utilisés par les auteurs de contenu pour créer des pages de contenu. Consultez la [documentation sur les modèles](/help/sites-cloud/authoring/features/templates.md) pour plus d&#39;informations sur la façon dont les modèles sont créés.

[Les boîtes de dialogue de création sont utilisées lors de la modification d’un modèle](/help/sites-cloud/authoring/features/templates.md) de page, bien qu’elles ne soient pas nécessaires pour tous les composants. Par exemple, les composants **Titre** et **Image** ont tous deux des boîtes de dialogue de conception, contrairement au composant **Partage sur les réseaux sociaux**.

### IU Coral et IU Granite {#coral-and-granite}

L’interface utilisateur de Coral et l’interface utilisateur de Granite définissent l’aspect de l’AEM.

* [Coral ](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) UIfournit une interface utilisateur cohérente pour toutes les solutions de cloud.
* [Granite ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) UIfournit des annotations Coral UI encapsulées dans des composants Sling pour la création de consoles et de boîtes de dialogue d’interface utilisateur.

L’interface utilisateur Granite fournit une large gamme de widgets de base nécessaires à la création de votre boîte de dialogue dans l’environnement de création. Si nécessaire, vous pouvez étendre cette sélection et créer votre propre widget.

Pour plus d&#39;informations, consultez les ressources suivantes :

* [Guide de l’IU Coral](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html)
* [Documentation relative à l’interface utilisateur Granite](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
* [Structure de l’interface utilisateur d’AEM](/help/implementing/developing/introduction/ui-structure.md)

### Personnalisation des champs de boîte de dialogue {#customizing-dialog-fields}

>[!TIP]
>
>Consultez la [session AEM Gems](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html) sur la personnalisation des champs de dialogue.

Pour créer un widget à utiliser dans une boîte de dialogue de composant, vous devez créer un nouveau composant de champ d’interface utilisateur Granite.

Si vous configurez votre boîte de dialogue comme un conteneur simple pour un élément de formulaire, vous pouvez également voir le contenu principal du contenu de la boîte de dialogue sous la forme de champs de formulaire. La création d’un champ de formulaire nécessite la création d’un type de ressource. Cela équivaut à créer un composant. Pour vous aider dans cette tâche, l’IU Granite propose un composant de champ générique duquel hériter (en utilisant `sling:resourceSuperType`) :

`/libs/granite/ui/components/coral/foundation/form/field`

Plus précisément, l&#39;interface utilisateur Granite fournit une gamme de composants de champ qui peuvent être utilisés dans les boîtes de dialogue ou, plus généralement, dans les [formulaires.](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)

Une fois que vous avez créé votre type de ressource, vous pouvez instancier le champ en ajoutant un nouveau nœud dans la boîte de dialogue, avec la propriété `sling:resourceType` faisant référence au type de ressource que vous venez d’introduire.

#### Accès aux champs de boîte de dialogue {#access-to-dialog-fields}

Vous pouvez également utiliser les conditions de rendu (`rendercondition`) pour contrôler qui a accès à des onglets/champs spécifiques dans votre boîte de dialogue. Par exemple :

```text
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

## Utilisation des composants {#using-components}

Une fois que vous avez créé un composant, vous devez l’activer pour pouvoir l’utiliser. Son utilisation montre comment la structure du composant se rattache à la structure du contenu résultant dans le référentiel.

### Ajouter votre composant au modèle {#adding-your-component-to-the-template}

Une fois qu’un composant a été défini, il doit être disponible pour utilisation. Pour rendre un composant disponible pour utilisation dans un modèle, vous devez activer le composant dans la stratégie du conteneur de mise en page du modèle.

Consultez la [documentation sur les modèles](/help/sites-cloud/authoring/features/templates.md) pour plus d&#39;informations sur la façon dont les modèles sont créés.

### Composants et contenu qu’ils créent {#components-and-the-content-they-create}

Si nous créons et configurons une instance du composant **Title** sur la page : `/content/wknd/language-masters/en/adventures/extreme-ironing.html`

![Boîte de dialogue Modifier le titre](assets/components-title-dialog.png)

Ensuite, nous pouvons voir la structure du contenu créé dans le référentiel :

![Structure du noeud de composant de titre](assets/components-title-content-nodes.png)

En particulier, si vous regardez le texte réel d&#39;un **composant de titre** :

* Le contenu contient une propriété `jcr:title` contenant le texte réel du titre saisi par l’auteur.
* Il contient également une référence `sling:resourceType` à la définition du composant.

Les propriétés définies dépendent des définitions individuelles. Bien qu’elles puissent être plus complexes que dans les exemples ci-dessus, elles suivent toujours les mêmes principes simples.

## Hiérarchie et héritage des composants  {#component-hierarchy-and-inheritance}

Les composants de l&#39;AEM sont soumis à la **Hiérarchie du type de ressource**. Il est utilisé pour étendre les composants à l&#39;aide de la propriété `sling:resourceSuperType`. Cela permet au composant d’hériter d’un autre composant.

Pour plus d&#39;informations, consultez la section [Réutilisation des composants](#reusing-components).

## Comportement de modification {#edit-behavior}

Cette section explique comment configurer le comportement de modification d’un composant. Cela inclut des attributs tels que les actions disponibles pour le composant, les caractéristiques de l’éditeur in.place et les écouteurs liés aux événements du composant.

Le comportement de modification d’un composant est configuré en ajoutant un nœud `cq:editConfig` de type `cq:EditConfig` en dessous du nœud de composant (de type `cq:Component`) et en ajoutant des propriétés spécifiques et des nœuds enfants. Les propriétés et les nœuds enfants suivants sont disponibles :

* `cq:editConfig` propriétés de noeud
* [`cq:editConfig` noeuds](#configuring-with-cq-editconfig-child-nodes) enfants :
   * `cq:dropTargets` (type de noeud  `nt:unstructured`) : définit une liste de cibles de dépôt qui peut accepter une goutte à partir d’une ressource de l’outil de recherche de contenu (une seule cible de dépôt est autorisée).
   * `cq:inplaceEditing` (type de noeud  `cq:InplaceEditingConfig`) : définit une configuration de modification statique pour le composant.
   * `cq:listeners` (type de noeud  `cq:EditListenersConfig`) : définit ce qui se produit avant ou après une action sur le composant.

Il existe de nombreuses configurations en AEM. Vous pouvez facilement rechercher des propriétés spécifiques ou des noeuds enfants à l’aide de l’outil de Requête dans **CRXDE Lite**.

### Configuration avec des nœuds enfants cq:EditConfig {#configuring-with-cq-editconfig-child-nodes}

#### Déposer des ressources dans une boîte de dialogue - cq:dropTargets {#cq-droptargets}

Le noeud `cq:dropTargets` (type de noeud `nt:unstructured`) définit la cible de dépôt qui peut accepter une goutte d’un fichier glissé depuis l’outil de recherche de contenu. Il s’agit d’un noeud de type `cq:DropTargetConfig`.

Le noeud enfant de type `cq:DropTargetConfig` définit une cible de dépôt dans le composant.

### Modification sur place - cq:inplaceEditing {#cq-inplaceediting}

Un éditeur statique permet à l’utilisateur de modifier le contenu directement dans le flux de contenu, sans avoir à ouvrir de boîte de dialogue. Par exemple, les composants standard **Texte** et **Titre** ont tous deux un éditeur d’entrelacs.

Un éditeur statique n’est pas nécessaire/significatif pour chaque type de composant.

Le noeud `cq:inplaceEditing` (type de noeud `cq:InplaceEditingConfig`) définit une configuration de modification statique pour le composant. Il peut posséder les propriétés suivantes :

| Nom de la propriété | Type de propriété | Valeur de la propriété |
|---|---|---|
| `active` | `Boolean` | `true` pour activer la modification statique du composant. |
| `configPath` | `String` | Chemin d’accès de la configuration de l’éditeur, qui peut être spécifié par un noeud de configuration |
| `editorType` | `String` | Les types disponibles sont les suivants : `plaintext` pour le contenu non HTML, `title` convertit les titres graphiques en texte brut avant le début de la modification et `text` utilise l’éditeur de texte enrichi |

La configuration suivante active la modification inp-lace du composant et définit `plaintext` comme type d’éditeur :

```text
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### Gestion des Événements de champ - cq:écouteurs {#cq-listeners}

La méthode de gestion des événements sur les champs de boîte de dialogue s&#39;effectue avec les écouteurs dans une [bibliothèque cliente personnalisée.](/help/implementing/developing/introduction/clientlibs.md)

Pour injecter une logique dans votre champ, vous devez :

* Faire marquer votre champ avec une classe CSS donnée (le hook).
* Définissez dans votre bibliothèque cliente un écouteur JS associé à ce nom de classe CSS (afin de vous assurer que votre logique personnalisée est étendue à votre champ uniquement et n’affecte pas les autres champs du même type).

Pour ce faire, vous devez connaître la bibliothèque de widgets sous-jacente avec laquelle vous souhaitez interagir. [Consultez la documentation relative à l’IU Coral](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) pour identifier l’événement auquel vous voulez réagir.

Le noeud `cq:listeners` (type de noeud `cq:EditListenersConfig`) définit ce qui se produit avant ou après une action sur le composant. Le tableau suivant définit ses propriétés possibles.

| Nom de la propriété | Valeur de la propriété |
|---|---|
| `beforedelete` | Le gestionnaire est déclenché avant que le composant ne soit supprimé. |
| `beforeedit` | Le gestionnaire est déclenché avant la modification du composant. |
| `beforecopy` | Le gestionnaire est déclenché avant la copie du composant. |
| `beforeremove` | Le gestionnaire est déclenché avant le déplacement du composant. |
| `beforeinsert` | Le gestionnaire est déclenché avant l&#39;insertion du composant. |
| `beforechildinsert` | Le gestionnaire est déclenché avant que le composant ne soit inséré dans un autre composant (conteneurs uniquement). |
| `afterdelete` | Le gestionnaire est déclenché après la suppression du composant. |
| `afteredit` | Le gestionnaire est déclenché après la modification du composant. |
| `aftercopy` | Le gestionnaire est déclenché après la copie du composant. |
| `afterinsert` | Le gestionnaire est déclenché après l&#39;insertion du composant. |
| `aftermove` | Le gestionnaire est déclenché après le déplacement du composant. |
| `afterchildinsert` | Le gestionnaire est déclenché après l’insertion du composant dans un autre composant (conteneurs uniquement). |

>[!NOTE]
>
>Dans le cas des composants imbriqués, il existe certaines restrictions sur les actions définies comme propriétés sur le noeud `cq:listeners`. Pour les composants imbriqués, les valeurs des propriétés **doivent** être `REFRESH_PAGE` :
>
>* `aftermove`
>* `aftercopy`


Le gestionnaire d’événements peut être mis en œuvre avec une implémentation personnalisée. Par exemple (où `project.customerAction` est une méthode statique) :

`afteredit = "project.customerAction"`

L&#39;exemple suivant équivaut à la configuration `REFRESH_INSERTED` :

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

Avec la configuration suivante, la page est actualisée après la suppression, la modification, l’insertion ou le déplacement du composant :

```text
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```

### Validation de champ {#field-validation}

La validation des champs dans l’interface utilisateur Granite et les widgets d’interface Granite s’effectue à l’aide de l’API `foundation-validation`. Voir la [`foundation-valdiation` documentation Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html) pour plus de détails.

## Comportement de la prévisualisation {#preview-behavior}

Le cookie [WCM Mode ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html)est défini lors du passage en mode Aperçu même lorsque la page n’est pas rafraîchie.

Pour les composants dont le rendu est sensible au mode WCM, ils doivent être définis de manière à s’actualiser eux-mêmes, puis s’appuyer sur la valeur du cookie.

## Documentation des composants {#documenting-components}

En tant que développeur, vous souhaitez accéder facilement à la documentation des composants afin de pouvoir comprendre rapidement les éléments suivants :

* Description
* leur utilisation prévue ;
* la structure de contenu et les propriétés ;
* les API exposées et les points d’extension.
* etc.

Pour cette raison, il est assez simple de mettre à disposition toute la documentation existante dans le composant lui-même.

Il suffit de placer un fichier `README.md` dans la structure du composant.

![README.md dans la structure de composants](assets/components-documentation.png)

Cette annotation s&#39;affichera ensuite dans la [console de composants.](/help/sites-cloud/authoring/features/components-console.md)

![README.md visible dans la console de composants](assets/components-documentation-console.png)

Le balisage pris en charge est identique à celui des fragments de contenu [.](/help/assets/content-fragments/content-fragments.md)