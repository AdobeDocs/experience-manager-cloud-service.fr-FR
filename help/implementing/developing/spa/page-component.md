---
title: Composant de page SPA
description: Dans une application d’une seule page, le composant de page ne fournit pas les éléments HTML de ses composants enfants, mais les délègue au cadre d’application d’une seule page. Ce document explique comment cela rend le composant de page d’une application monopage unique.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 11%

---


# Composant de page SPA {#spa-page-component}

Le composant de page d’un SPA ne fournit pas les éléments HTML de ses composants enfants via un fichier JSP ou HTL et des objets de ressources. Cette opération est déléguée à la structure SPA. La représentation des composants enfants est récupérée sous la forme d’une structure de données JSON (c’est-à-dire le modèle). Les composants d’application d’une seule page sont ensuite ajoutés à la page conformément au modèle JSON fourni. La composition initiale du corps du composant de page diffère donc de celle du code HTML prérendu.

## Gestion du modèle de page {#page-model-management}

The resolution and the management of the page model is delegated to a provided [`PageModelManager`](blueprint.md#pagemodelmanager) module. L’application d’une seule page doit interagir avec le `PageModelManager` module lorsqu’elle s’initialise pour récupérer le modèle de page initial et s’enregistrer pour les mises à jour du modèle. Cette opération est principalement réalisée lorsque l’auteur modifie la page via l’éditeur de page. Le `PageModelManager` est accessible par le projet SPA sous la forme d&#39;un package npm. En tant qu&#39;interprète entre AEM et le SPA, le `PageModelManager` est destiné à accompagner le SPA.

Pour autoriser la création de la page, une bibliothèque cliente nommée `cq.authoring.pagemodel.messaging` doit être ajoutée pour fournir un canal de communication entre l’application d’une seule page et l’éditeur de page. Si le composant de page de l’application d’une seule page hérite du composant wcm/core de la page, il existe les options suivantes pour rendre la catégorie de bibliothèque `cq.authoring.pagemodel.messaging` cliente disponible :

* Si le modèle est modifiable, ajoutez la catégorie de bibliothèque cliente à la stratégie de page.
* ajoutez la catégorie de bibliothèque cliente à l’aide `customfooterlibs.html` du composant de page.

N&#39;oubliez pas de limiter l&#39;inclusion de la `cq.authoring.pagemodel.messaging` catégorie au contexte de l&#39;éditeur de page.

## Type de données de communication {#communication-data-type}

Le type de données de communication est défini comme un élément HTML dans le composant AEM Page à l’aide de l’ `data-cq-datatype` attribut. Lorsque le type de données de communication est défini sur JSON, les demandes de GET atteignent les points de terminaison du modèle Sling d’un composant. À la suite d’une mise à jour dans l’éditeur de page, la représentation JSON du composant mis à jour est envoyée à la bibliothèque modèle de page. La bibliothèque Modèle de page avertit ensuite l’application d’une seule page des mises à jour.

**Composant de page SPA -`body.html`**

```
<div id="page"></div>
```

En plus d’être une bonne pratique pour ne pas retarder la génération du modèle DOM, la structure SPA exige que les scripts soient ajoutés à la fin du corps.

**Composant de page SPA -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

Propriétés des ressources de métadonnées décrivant le contenu de l’application d’une seule page :

**Composant de page SPA -`customheaderlibs.html`**

```
<meta property="cq:datatype" data-sly-test="${wcmmode.edit || wcmmode.preview}" content="JSON"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.edit}" content="edit"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.preview}" content="preview"/>
<meta property="cq:pagemodel_root_url" data-sly-use.page="com.adobe.cq.sample.spa.journal.models.AppPage" content="${page.rootUrl}"/>
<sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <sly data-sly-call="${clientlib.css @ categories='we-retail-journal-react'}"/>
</sly>
```

>[!NOTE]
>
>Le sélecteur de modèle par défaut est défini de manière statique lors de la demande de la représentation du modèle Sling d’un composant.

## Propriétés des métadonnées {#meta-properties}

* `cq:wcmmode`: Mode WCM des éditeurs (par exemple, page, modèle)
* `cq:pagemodel_root_url`: URL du modèle racine de l’application. Important lors de l’accès direct à une page enfant, car le modèle de page enfant est un fragment du modèle racine de l’application. Le modèle initial de l’application est `PageModelManager` ensuite recomposé de manière systématique en entrant dans l’application à partir de son point d’entrée racine.
* `cq:pagemodel_router`: Activation ou désactivation [`ModelRouter`](routing.md) de la `PageModelManager` bibliothèque
* `cq:pagemodel_route_filters`: Liste séparée par des virgules ou expressions régulières pour fournir des itinéraires que les [`ModelRouter`](routing.md) doivent ignorer.

## Synchronisation des incrustations de l’éditeur de page {#page-editor-overlay-synchronization}

La synchronisation des recouvrements est assurée par le même Mutation Observer que celui fourni par la `cq.authoring.page` catégorie.

## Configuration de la structure exportée JSON du modèle Sling {#sling-model-json-exported-structure-configuration}

Lorsque les fonctionnalités de routage sont activées, l’hypothèse est que l’exportation JSON de l’application d’une seule page contient les différents itinéraires de l’application grâce à l’exportation JSON du composant de navigation AEM. La sortie JSON du composant de navigation AEM peut être configurée dans la stratégie de contenu de page racine de l’application sur une seule page au moyen des deux propriétés suivantes :

* `structureDepth` : nombre correspondant à la profondeur de l’arborescence exportée
* `structurePatterns`: Regex de tableau de index correspondant à la page à exporter
