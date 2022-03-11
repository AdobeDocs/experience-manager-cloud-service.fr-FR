---
title: Composant RemotePage
description: Le composant RemotePage est un composant de page personnalisé permettant de modifier les SPA React distantes dans AEM.
exl-id: d3465592-0392-49b0-b49d-de93983c1d6e
source-git-commit: eaa59b6ecfa50c4a6b4e316e5e305e48cb3d5676
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Composant RemotePage {#remote-page-component}

Lorsque vous décidez du [niveau d’intégration](/help/implementing/developing/headful-headless.md) vous souhaitez avoir entre votre SPA externe et votre instance AEM, il est souvent évident que vous devez être capable d’afficher et de modifier la SPA dans AEM. Le composant RemotePage est un composant de page personnalisé destiné uniquement à cette fin.

## Présentation {#overview}

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

## Restrictions {#limitations}

* L’implémentation actuelle du composant RemotePage ne prend en charge que les applications React distantes.
* La page CSS interne définie dans le fichier HTML racine de l’application ainsi que la page CSS intégrée sur le nœud DOM racine ne seront pas disponibles lors du rendu à distance dans AEM.

## Détails techniques {#technical-details}

Comme le reste du projet de SPA AEM, le composant RemotePage est disponible en open source. Pour obtenir les détails techniques complets concernant le composant RemotePage, [consultez le référentiel GitHub.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
