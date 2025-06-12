---
title: Composant RemotePage
description: Le composant RemotePage est un composant de page personnalisé permettant de modifier les SPA React distantes dans AEM.
exl-id: d3465592-0392-49b0-b49d-de93983c1d6e
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 86%

---


# Composant RemotePage {#remote-page-component}

Lorsque vous décidez du [niveau d’intégration](/help/implementing/developing/headful-headless.md) vous souhaitez avoir entre votre SPA externe et votre instance AEM, il est souvent évident que vous devez être capable d’afficher et de modifier la SPA dans AEM. Le composant RemotePage est un composant de page personnalisé destiné uniquement à cette fin.

{{ue-over-spa}}

## Vue d’ensemble {#overview}

Le composant RemotePage récupère toutes les ressources nécessaires à partir du `asset-manifest.json` généré par l’application et l’utilise pour effectuer le rendu des SPA dans AEM.

* Le composant RemotePage vous permet d’injecter les scripts et feuilles de style d’un SPA dans le corps d’un composant Page AEM.
* Les composants virtuels en front-end permettent d’indiquer les sections qui sont modifiables dans l’éditeur d’application monopage d’AEM.
* Grâce à cela, un SPA hébergé sur un autre domaine peut être rendu modifiable dans AEM.

Consultez l’article [Modification d’un SPA externe dans AEM](editing-external-spa.md) pour plus d’informations sur les SPA externes modifiables dans AEM.

## Conditions requises {#requirements}

* Activer CORS en développement
* Configurer l’URL distante dans les propriétés de page
* Effectuer le rendu de la SPA dans AEM
* L’application web doit utiliser un des manifestes de ressource de bundle suivants et exposer un fichier `asset-manifest.json` à la racine du domaine qui répertorie dans un `entrypoints property` tous les fichiers CSS et JS à charger :
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest

     ![Exemple de propriété entrypoints](assets/asset-manifest-entrypoints.png)
* L’application doit pouvoir être initialisée dans un `<div id="root"></div>` sous l’élément `body`. Si une balise différente est attendue pour l’application, elle doit être ajustée en conséquence dans les scripts HTL du composant proxy avec `sling:resourceSuperType="spa-project-core/components/remotepage`.

## Limites {#limitations}

* Le composant RemotePage s’attend à ce que l’implémentation fournisse un manifeste de ressource comme [celui-ci](https://github.com/shellscape/webpack-manifest-plugin). Le composant RemotePage, en revanche, a été testé uniquement pour fonctionner avec le framework React (et Next.js par le biais du composant remote-page-next) et il ne prend donc pas en charge le chargement à distance d’applications à partir d’autres frameworks tels qu’Angular.
* La page CSS interne définie dans le fichier HTML racine de l’application ainsi que la page CSS intégrée sur le nœud DOM racine ne seront pas disponibles lors du rendu à distance dans AEM.

## Détails techniques {#technical-details}

Comme le reste du projet de SPA AEM, le composant RemotePage est disponible en open source. Pour obtenir des détails techniques complets sur le composant RemotePage, [consultez le référentiel GitHub](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage).
