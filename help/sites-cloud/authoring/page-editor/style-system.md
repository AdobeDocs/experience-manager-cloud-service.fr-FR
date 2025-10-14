---
title: Système de style
description: Le système de style permet à un auteur de modèles de définir des classes de style dans la politique de contenu d’un composant, de façon à pouvoir sélectionner ces classes lors de la modification du composant sur une page. Ces styles peuvent être des variantes visuelles d’un composant, le rendant ainsi plus flexible.
exl-id: 224928dd-e365-4f3e-91af-4d8d9f47efdd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: d2cd112de034ca6ea22590245fb480622acf258a
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 88%

---


# Système de style {#style-system}

Le système de style permet à un auteur de modèles de définir des classes de style dans la politique de contenu d’un composant, de façon à pouvoir sélectionner ces classes lors de la modification du composant sur une page. Ces styles peuvent être des variantes visuelles d’un composant, le rendant ainsi plus flexible.

Cela évite d’avoir à développer un composant personnalisé pour chaque style ou à personnaliser la boîte de dialogue du composant pour activer cette fonctionnalité de style. Elle génère des composants mieux réutilisables qui peuvent être rapidement et facilement adaptés aux besoins des auteurs et autrices de contenu sans développement back-end AEM.

>[!NOTE]
>
>Le système de style s’applique uniquement aux pages créées avec l’éditeur de page.
>
>Il est possible de mettre en forme des pages créées avec l’[éditeur universel](/help/implementing/universal-editor/introduction.md) et diffusées avec [Edge Delivery Services](/help/edge/overview.md) entièrement via votre projet GitHub.

## Cas d’utilisation {#use-case}

Les créateurs et créatrices de modèles doivent non seulement pouvoir configurer le fonctionnement des composants pour les créateurs et créatrices de contenu, mais aussi configurer un certain nombre de variantes visuelles d’un composant.

De même, les créateurs et créatrices de contenu doivent non seulement pouvoir structurer et organiser leur contenu, mais aussi sélectionner la manière dont il est présenté visuellement.

Le système de style constitue une solution unifiée pour répondre à la fois aux exigences des auteurs de contenus et de modèles :

* Les créateurs et créatrices de modèles peuvent définir des classes de style dans la stratégie de contenu des composants.
* Les créateurs et créatrices de contenu peuvent ensuite sélectionner ces classes dans une liste déroulante lors de la modification du composant sur une page afin qu’ils puissent appliquer les styles correspondants.

La classe de style est ensuite insérée sur l’élément wrapper du composant, de sorte que le développeur ou la développeuse de composants n’ait pas à gérer les styles au-delà de la fourniture de leurs règles CSS.

## Vue d’ensemble {#overview}

L’utilisation du système de style se passe généralement comme suit.

1. Le concepteur web crée différentes variantes visuelles d’un composant.

1. Le développeur HTML dispose de la sortie HTML des composants et des variantes visuelles à mettre en œuvre.

1. Le développeur HTML définit les classes CSS qui correspondent à chaque variante visuelle et qui doivent être insérées sur l’élément qui enveloppe les composants.

1. Le développeur HTML met en œuvre le code CSS correspondant (et, éventuellement, le code JS) pour que chaque variante visuelle ait l’apparence définie.

1. Le développeur AEM place le code CSS (et en option, JS) fourni dans une [bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md) et le déploie.

1. Le développeur AEM ou l’auteur de modèles configure les modèles de page et modifie la politique de chaque composant stylisé, en ajoutant les classes CSS définies, en attribuant des noms conviviaux à chaque style et en indiquant les styles qui peuvent être combinés.

1. L’auteur des pages AEM peut alors choisir les styles conçus dans l’éditeur de page via le menu de style de la barre d’outils du composant.

Seules les trois dernières étapes sont réellement effectuées dans AEM. Cela signifie que l’ensemble du développement des codes CSS et JavaScript peut être réalisé sans AEM.

En fait, la mise en œuvre des styles ne nécessite que le déploiement sur AEM et la sélection dans les composants des modèles souhaités.

Le diagramme suivant illustre l’architecture du système de style.

![aem-style-system](/help/sites-cloud/authoring/assets/style-system-architecture.png)

## Utilisez {#use}

Pour démontrer la fonctionnalité, nous utiliserons comme exemple l’implémentation de [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr), [composant de titre](https://www.adobe.com/go/aem_cmp_title_v2_fr) des composants principaux.

Les sections suivantes, [En tant qu’auteur de contenu](#as-a-content-author) et [En tant qu’auteur de modèles](#as-a-template-author), décrivent comment tester les fonctionnalités du système de style à l’aide du système de style de WKND.

Si vous souhaitez utiliser le système de style pour vos propres composants, procédez comme suit :

1. Installez le CSS en tant que bibliothèques clientes, comme décrit dans la section [Vue d’ensemble](#overview).
1. Configurez les classes CSS que vous souhaitez mettre à la disposition des auteurs de contenu, comme décrit dans la section [&#x200B; En tant qu’auteur de modèle &#x200B;](#as-a-template-author).
1. Les créateurs et créatrices de contenu peuvent alors utiliser les styles comme décrit dans la section [En tant que créateur ou créatrice de contenu](#as-a-content-author).

### En tant qu’auteur de contenu {#as-a-content-author}

1. Après avoir installé le projet WKND, accédez à la page d’accueil principale de WKND `http://<host>:<port>/sites.html/content/wknd/language-masters/en` (en anglais) et modifiez la page.
1. Sélectionnez un composant **Titre** plus bas dans la page

   ![Système de style pour l’auteur](/help/sites-cloud/authoring/assets/style-system-author1.png)

1. Sélectionnez le bouton **Styles** dans la barre d’outils du composant **Liste** pour ouvrir le menu de style et modifier l’aspect du composant.

   ![Sélection de styles](/help/sites-cloud/authoring/assets/style-system-author2.png)

   >[!NOTE]
   >
   >Dans cet exemple, les styles **Couleurs** (**Noir**, **Blanc** et **Gris**) s’excluent mutuellement, tandis que les options **Style** (**Souligné**, **Aligner à droite** et **Mini Espacement**) peuvent être combinées. Vous pouvez [configurer ce paramètre dans le modèle en tant qu’auteur du modèle](#as-a-template-author).

### En tant qu’auteur de modèles {#as-a-template-author}

1. Alors que vous modifiez la page d’accueil de WKND (`http://<host>:<port>/sites.html/content/wknd/language-masters/en`) (en anglais), modifiez le modèle de la page via **Informations sur la page -> Modifier le modèle**.

   ![Modifier le modèle](/help/sites-cloud/authoring/assets/style-system-edit-template.png)

1. Modifiez la police du composant **Titre** en appuyant ou en cliquant sur le bouton **Politique** du composant.

   ![Modifier la politique](/help/sites-cloud/authoring/assets/style-system-edit-policy.png)

1. Dans l’onglet Styles des propriétés, vous pouvez voir comment les styles ont été configurés.

   ![Modification des propriétés](/help/sites-cloud/authoring/assets/style-system-properties.png)

   * **Nom du groupe :** les styles peuvent être regroupés dans le menu de style que le créateur de contenu voit lors de la configuration du style du composant.
   * **Les styles peuvent être combinés :** permet de sélectionner simultanément plusieurs styles au sein de ce groupe.
   * **Nom du style :** description du style qui s’affichera à l’auteur ou à l’autrice du contenu lors de la configuration du style du composant.
   * **Classes CSS :** nom réel de la classe CSS associée au style.

   Utilisez les poignées de glissement pour organiser l’ordre des groupes et les styles au sein des groupes. Utilisez les icônes d’ajout ou de suppression pour ajouter ou supprimer des groupes ou des styles au sein des groupes.

>[!CAUTION]
>
>Pour pouvoir fonctionner, les classes CSS, ainsi que toute classe JavaScript nécessaire, configurées en tant que propriétés de style d’une politique de composants doivent être déployées comme [bibliothèques clientes](/help/implementing/developing/introduction/clientlibs.md).

## Configuration {#setup}

La version 2 ou supérieure des composants principaux est entièrement équipée pour tirer parti du système de style. Elle ne nécessite aucune configuration supplémentaire.

Les étapes suivantes ne sont nécessaires que pour activer le système de style pour vos propres composants personnalisés ou pour [activer l’onglet Styles facultatif dans la boîte de dialogue Modifier](#enable-styles-tab-edit).

### Activer l’onglet Style dans la boîte de dialogue Conception {#enable-styles-tab-design}

Pour qu’un composant fonctionne avec le système de style d’AEM et affiche l’onglet Style dans sa boîte de dialogue de conception, le développeur ou la développeuse de composants doit inclure cet onglet avec les paramètres suivants sur le composant :

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Cette méthode utilise des [recouvrements](/help/implementing/developing/introduction/overlays.md) en faisant appel à [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md).

Une fois le composant configuré, les styles configurés par les personnes créant les pages sont automatiquement insérés par AEM sur l’élément décoratif qu’AEM encapsule automatiquement autour de chaque composant modifiable. Le composant lui-même n’a besoin d’effectuer aucune autre action pour que cela se produise.

### Activer l’onglet Styles dans la boîte de dialogue Modifier {#enable-styles-tab-edit}

La boîte de dialogue Modifier comporte également un onglet facultatif Styles. Contrairement à l’onglet de la boîte de dialogue Conception, celui de la boîte de dialogue Modifier n’est pas essentiel pour le fonctionnement du système de style. Il s’agit d’une autre interface facultative, utilisable par un auteur de contenu pour définir des styles.

L’onglet de la boîte de dialogue Modifier peut être inclus de la même manière que celui de la boîte de dialogue Conception :

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Cette méthode utilise des [recouvrements](/help/implementing/developing/introduction/overlays.md) en faisant appel à [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md).

>[!NOTE]
>
>L’onglet Styles de la boîte de dialogue Modifier n’est pas activé par défaut.

### Styles avec noms d’éléments {#styles-with-element-names}

Les développeurs peuvent aussi configurer une liste de noms d’éléments autorisés pour les styles du composant avec la propriété de table de chaînes `cq:styleElements`. Ensuite, dans l’onglet Styles de la politique, dans la boîte de dialogue de conception, l’auteur de modèles peut aussi choisir un nom d’élément pour chaque style. Cela définit le nom de l’élément wrapper.

Cette propriété est définie sur le nœud `cq:Component`. Par exemple :

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Évitez de définir des noms d’éléments pour les styles pouvant être combinés. Lorsque plusieurs noms d’éléments sont définis, l’ordre de priorité est le suivant :
>
>1. HTL est prioritaire sur tout le reste : `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Ensuite, au sein de plusieurs styles actifs, le premier style de la liste des styles configurés dans la politique du composant est sélectionné.
>1. Enfin, le nom `cq:htmlTag`/`cq:tagName` du composant est considéré comme une valeur de repli.
>

Cette capacité à définir des noms de styles est utile pour les composants génériques, tels que le conteneur de mise en page ou le composant Fragment de contenu. Cela permet de leur donner davantage de sens.

Cela permet, par exemple, d’attribuer au conteneur de disposition des sémantiques telles que `<main>`, `<aside>`, `<nav>`, etc.
