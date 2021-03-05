---
title: Composant RemotePage
description: Le composant RemotePage est un composant de page personnalisé permettant de modifier les SPA de réaction distantes dans AEM.
translation-type: tm+mt
source-git-commit: 9a1048f6d185d2d3229bab05b8e827845444d11c
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---

# Composant RemotePage {#remote-page-component}

Lorsque vous décidez de [quel niveau d&#39;intégration](/help/implementing/developing/headful-headless.md) vous souhaitez avoir entre votre SPA externe et votre AEM, il est souvent clair que vous devez être capable de vue et de modifier le SPA dans l&#39;. Le composant RemotePage est un composant de page personnalisé destiné uniquement à cette fin.

## Présentation {#overview}

Le composant RemotePage récupère toutes les ressources nécessaires à partir du `asset-manifest.json` généré par l&#39;application et l&#39;utilise pour effectuer le rendu des SPA dans AEM.

* La page distante vous permet d&#39;injecter les scripts et feuilles de style d&#39;un SPA dans le corps d&#39;un composant AEM Page.
* Les Composants Frontières virtuels permettent de marquer les sections comme modifiables dans AEM SPA Editor.
* Ensemble, un SPA hébergé sur un autre domaine peut être rendu modifiable dans AEM.

Voir l&#39;article [Modification d&#39;un SPA externe dans AEM](editing-external-spa.md) pour plus d&#39;informations sur les SPA externes modifiables dans l&#39;.

## Conditions préalables {#requirements}

* Activer CORS dans le développement
* Configuration de l’URL distante dans les propriétés de page
* Rendu du SPA en AEM

## Restrictions {#limitations}

* L&#39;implémentation actuelle du composant RemotePage ne prend en charge que les applications React distantes.
* La page CSS interne définie dans le fichier HTML racine de l’application ainsi que la page CSS intégrée sur le noeud DOM racine ne seront pas disponibles lors du rendu à distance dans AEM.

## Détails techniques {#technical-details}

Comme le reste du projet AEM SPA, le composant RemotePage est open source. Pour obtenir les détails techniques complets du composant RemotePage, [consultez le référentiel GitHub.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
