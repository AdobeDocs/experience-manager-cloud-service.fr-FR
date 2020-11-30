---
title: Introduction et présentation des applications sur une seule page (SPA)
description: Cet article présente les concepts d’une SPA et décrit l’utilisation d’une SPA élémentaire à des fins de création, indiquant comment cette utilisation est liée à l’éditeur de SPA AEM sous-jacent.
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 100%

---


# Introduction et présentation des applications sur une seule page (SPA) {#spa-introduction}

Les applications sur une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

L’éditeur de SPA constitue une solution complète pour la prise en charge des SPA dans AEM. Cet article décrit l’utilisation d’une SPA élémentaire à des fins de création et indique comment cette utilisation est liée à l’éditeur de SPA AEM sous-jacent.

## Présentation {#introduction}

### Objectif de l’article {#article-objective}

Cet article présente les concepts de base des SPA, puis passe en revue l’éditeur de SPA en utilisant une SPA simple pour démontrer les fonctions de base de modification de contenu. Il détaille ensuite la construction de la page et indique comment la SPA est liée à l’éditeur de SPA AEM et interagit avec lui.

L’objectif de cette introduction et de cette présentation est de montrer aux développeurs AEM pourquoi les SPA sont pertinentes, comment elles fonctionnent, comment elles sont gérées par l’éditeur de SPA AEM et en quoi elles diffèrent d’une application AEM standard.

La présentation repose sur les fonctionnalités AEM standard et l’exemple d’application de projet SPA WKND. Pour suivre cette présentation, [téléchargez et installez l’exemple d’application de projet SPA WKND via GitHub ici.](https://github.com/adobe/aem-guides-wknd-spa)

>[!CAUTION]
>
>Ce document n’utilise l’[exemple d’application de projet SPA WKND](https://github.com/adobe/aem-guides-wknd-spa) qu’à des fins de démonstration. Ce dernier ne doit pas être utilisé dans le cadre d’un projet.

>[!TIP]
>
>Tout projet AEM doit exploiter l’[archétype de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html), qui prend en charge les projets SPA à l’aide de React ou d’Angular et exploite le SDK SPA.

### Qu’est-ce qu’une SPA ? {#what-is-a-spa}

Une application sur une seule page (SPA) diffère d’une page conventionnelle en cela qu’elle est rendue côté client et qu’elle est principalement pilotée par JavaScript, en utilisant les appels Ajax pour charger les données et mettre la page à jour dynamiquement. La plupart ou la totalité du contenu est récupérée une fois au chargement d’une seule page avec des ressources supplémentaires chargées de manière asynchrone, selon les besoins, en fonction de l’interaction de l’utilisateur avec la page.

Cela limite la nécessité d’actualiser la page et offre à l’utilisateur une expérience harmonieuse, rapide et rappelant davantage l’expérience d’une application native.

L’éditeur de SPA AEM permet aux développeurs front-end de créer des SPA qui peuvent être intégrées à un site AEM, ce qui permet aux créateurs de contenu de modifier le contenu SPA aussi facilement qu’un autre contenu AEM.

### Pourquoi une SPA ? {#why-a-spa}

Plus rapide, fluide et ressemblant davantage à une application native, une SPA, de par son fonctionnement, offre une expérience très attrayante, non seulement pour le visiteur de la page web, mais aussi pour les spécialistes du marketing et les développeurs.

![Avantages des SPA](assets/spa-benefits.png)

#### Visiteurs {#visitors}

* Lorsqu’ils interagissent avec du contenu, les visiteurs souhaitent des expériences similaires à l’expérience d’une application native.
* Il existe des données claires indiquant que plus une page est rapide, plus une conversion est probable.

#### Spécialistes du marketing {#marketers}

* Les spécialistes du marketing veulent offrir des expériences riches et similaires à l’expérience d’une application native pour inciter les visiteurs à interagir pleinement avec le contenu.
* La personnalisation peut rendre ces expériences encore plus attrayantes.

#### Développeurs {#developers}

* Les développeurs veulent une séparation nette entre les aspects liés au contenu et à la présentation.
* Une séparation nette rend le système plus extensible tout en autorisant un développement front-end indépendant.

### Comment fonctionne une SPA ? {#how-does-a-spa-work}

L’idée principale sous-jacente à une SPA est que les appels à un serveur et la dépendance envers un serveur sont réduits afin de minimiser les retards liés à la latence du serveur, de sorte que la SPA s’approche de la réactivité d’une application native.

Sur une page web séquentielle traditionnelle, seules les données nécessaires à la page immédiate sont chargées. Cela signifie que lorsque le visiteur passe à une autre page, le serveur est appelé pour que les ressources supplémentaires soient mises à disposition. Des appels supplémentaires peuvent s’avérer nécessaires lorsque le visiteur interagit avec les éléments de la page. Ces appels multiples peuvent donner une impression de retard ou de lenteur, car la page doit rattraper les requêtes du visiteur.

![Expériences séquentielles ou fluides](assets/spa-sequential-vs-fluid.png)

Pour offrir une expérience plus fluide, qui s’approche de ce qu’un visiteur attend des applications mobiles natives, une SPA charge toutes les données nécessaires pour le visiteur au premier chargement. Bien que cette opération puisse nécessiter au début un peu plus de temps, elle élimine ensuite la nécessité d’appels supplémentaires au serveur.

Parce que le rendu est effectué côté client, les éléments de la page réagissent plus rapidement et les interactions du visiteur avec la page sont immédiates. Toutes les données supplémentaires qui peuvent être nécessaires sont appelées de manière asynchrone afin d’optimiser la vitesse de la page.

>[!TIP]
>
>Pour obtenir des détails techniques sur le fonctionnement des SPA dans AEM, consultez les articles suivants :
>* [Prise en main des SPA dans AEM avec React](getting-started-react.md)
>* [Prise en main des SPA dans AEM avec Angular](getting-started-angular.md)

>
>
Pour observer de plus près la conception, l’architecture et le workflow technique de l’éditeur de SPA, consultez l’article :
>* [Présentation de l’éditeur de SPA](editor-overview.md).


## Modification de contenu avec une SPA {#content-editing-experience-with-spa}

Lorsqu’une SPA est créée pour exploiter l’éditeur de SPA AEM, le créateur de contenu ne remarque aucune différence lors de la modification et de la création de contenu. Des fonctionnalités AEM communes sont disponibles et aucune modification du workflow du créateur n’est requise.

1. Modifiez l’application de projet SPA WKND dans AEM.

   `http://localhost:4502/editor.html/content/wknd-spa-react/us/en/home.html`

   ![Page d’accueil du projet SPA WKND](assets/wknd-home.png)

1. Sélectionnez un composant de texte et notez qu’une barre d’outils s’affiche comme pour tout autre composant. Sélectionnez **Modifier**.

   ![Sélectionner le composant de texte](assets/wknd-text.png)

1. Modifiez le contenu normalement dans AEM et notez que les modifications sont conservées.

   ![Modifier du texte](assets/wknd-edit-text.png)

1. Utilisez l’explorateur de ressources pour faire glisser et déposer une nouvelle image dans un composant d’image.

   ![Dépôt d’une ressource d’image](assets/wkdn-drop-image.png)

1. La modification est conservée.

   ![Image conservée](assets/wknd-change-persisted.png)

D’autres outils de création, tels que le glisser-déposer de composants supplémentaires sur la page, la réorganisation des composants et la modification de la mise en page, sont pris en charge comme dans toute application AEM non SPA.

>[!NOTE]
>
>L’éditeur de SPA ne modifie pas le modèle objet de document (DOM) de l’application. La SPA elle-même est responsable du DOM.
>
>Pour découvrir le fonctionnement de cet aspect, passez à la section suivante de cet article, [Applications SPA et éditeur de SPA AEM](#spa-apps-and-the-aem-spa-editor).

## Applications SPA et éditeur de SPA AEM {#spa-apps-and-the-aem-spa-editor}

Expérimenter le comportement d’une SPA pour l’utilisateur final puis inspecter la page SPA permet de mieux comprendre le fonctionnement d’une SPA avec l’éditeur de SPA dans AEM.

### Utilisation d’une SPA {#using-an-spa-application}

1. Chargez l’application de projet SPA WKND sur le serveur de publication ou à l’aide de l’option **Afficher comme publié(e)** du menu **Informations sur la page** de l’éditeur de page.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Aperçu de la page d’accueil du projet SPA WKND](assets/wknd-preview.png)

   Notez la structure des pages, y compris la navigation vers les pages enfants, le menu et les fiches d’article.

1. Accédez à une page enfant à l’aide du menu et observez que la page se charge immédiatement sans qu’il faille procéder à une actualisation.

   ![Projet SPA WKND – page 1](assets/wknd-page1.png)

1. Ouvrez les outils de développement intégrés de votre navigateur et surveillez l’activité du réseau lorsque vous naviguez sur les pages enfants.

   ![Activité du réseau](assets/wknd-network-activity.png)

   Le trafic est très faible, car vous passez d’une page à l’autre dans l’application. La page n’est pas rechargée et seules les nouvelles images sont demandées.

   La SPA gère le contenu et le routage entièrement du côté client.

Aussi, si la page n’est pas rechargée lors de la navigation sur les pages enfants, comment est-elle chargée ?

La section suivante, [Chargement d’une SPA](#loading-a-spa-application), examine de plus près la procédure de chargement de la SPA et indique comment le contenu peut être chargé de façon synchrone et asynchrone.

### Chargement d’une SPA {#loading-a-spa-application}

1. Si ce n’est pas déjà fait, chargez l’application We.Retail Journal sur le serveur de publication ou à l’aide de l’option **Afficher comme publié(e)** du menu **Informations sur la page** de l’éditeur de page.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Aperçu du projet SPA WKND](assets/wknd-preview.png)

1. Utilisez l’outil intégré de votre navigateur pour afficher la source de la page.
1. Notez que le contenu de la source est limité.

   ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8"/>
        <title>WKND SPA React Home Page</title>
   
        <meta name="template" content="spa-page-template"/>
        <meta name="viewport" content="width=device-width, initial-scale=1"/>
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-base.min.css" type="text/css">
   
    <meta name="theme-color" content="#000000"/>
    <link rel="icon" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/favicon.ico"/>
    <link rel="apple-touch-icon" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/logo192.png"/>
    <link rel="manifest" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/manifest.json"/>
   
    <!-- AEM page model -->
    <meta property="cq:pagemodel_root_url" content="/content/wknd-spa-react/us/en.model.json"/>
    <link href="//fonts.googleapis.com/css?family=Source+Sans+Pro:400,600|Asar&display=swap" rel="stylesheet"/>
    <meta property="cq:datatype" content="JSON"/>
    <meta property="cq:wcmmode" content="edit"/>
   
    <link rel="stylesheet" href="/libs/cq/gui/components/authoring/editors/clientlibs/internal/page.min.css" type="text/css">
    <link rel="stylesheet" href="/etc.clientlibs/wcm/foundation/clientlibs/main.min.css" type="text/css">
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/messaging.min.js"></script>
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/utils.min.js"></script>
    <script type="text/javascript" src="/libs/granite/author/deviceemulator/clientlibs.min.js"></script>
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/page.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/wcm/foundation/clientlibs/main.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/jquery.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/utils.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/jquery/granite.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/foundation/clientlibs/jquery.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/foundation/clientlibs/shared.min.js"></script>
   
    <!--cq{"decorated":false,"type":"cq/cloudconfig/components/scripttags/header","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-header","structurePath":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-header","selectors":null,"servlet":"Script /libs/cq/cloudconfig/components/scripttags/header/header.html","totalTime":2,"selfTime":2}-->
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react.min.css" type="text/css">
   
    </head>
   
    <body class="page basicpage">
        <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="spa-root"></div>
   
    <script type="text/javascript" src="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react.min.js"></script>
   
    <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-base.min.js"></script>
   
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/pagemodel/messaging.min.js"></script>
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-author.min.css" type="text/css">
   
    <!--cq{"decorated":true,"type":"cq/cloudserviceconfigs/components/servicecomponents","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudservices","selectors":null,"servlet":"Script /libs/cq/cloudserviceconfigs/components/servicecomponents/servicecomponents.jsp","totalTime":2,"selfTime":2}-->
   
    <!--cq{"decorated":false,"type":"cq/cloudconfig/components/scripttags/footer","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-footer","structurePath":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-footer","selectors":null,"servlet":"Script /libs/cq/cloudconfig/components/scripttags/footer/footer.html","totalTime":2,"selfTime":2}-->
   
    </body>
    </html>
    <!--cq{"decorated":false,"type":"wknd-spa-react/components/page","path":"/content/wknd-spa-react/us/en/home/jcr:content","selectors":null,"servlet":"Script /apps/spa-project-core/components/page/page.html","totalTime":39,"selfTime":33}-->
   ```

   Le corps de la page ne renferme aucun contenu. La page est principalement composée de feuilles de styles et d’un appel à divers scripts tels que `clientlib-react.min.js`.

   Ces scripts sont les pilotes principaux de cette application et sont responsables du rendu de tout le contenu.

1. Utilisez les outils intégrés de votre navigateur pour inspecter la page. Affichez le contenu du DOM entièrement chargé.

   ![DOM du projet SPA WKND](assets/wknd-dom.png)

1. Accédez à l’onglet Réseau de l’Inspecteur et rechargez la page.

   Sans tenir compte des requêtes d’image, notez que les principales ressources chargées pour la page sont la page elle-même, le code CSS, le code JavaScript React, ses dépendances, ainsi que les données JSON de la page.

   ![Activité de réseau du projet SPA WKND](assets/wknd-network.png)

1. Chargez `home.model.json` dans un nouvel onglet.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![JSON de la page d’accueil du projet SPA WKND](assets/wknd-json.png)

   L’éditeur de SPA AEM exploite [AEM Content Services](/help/assets/content-fragments/content-fragments.md) pour diffuser l’intégralité du contenu de la page sous la forme d’un modèle JSON.

   En implémentant des interfaces spécifiques, les modèles Sling fournissent les informations nécessaires à la SPA. La diffusion des données JSON est déléguée vers le bas à chaque composant (de la page, au paragraphe, au composant, etc.).

   Chaque composant choisit les données qu’il expose et le mode de rendu de ces données (côté serveur avec HTL ou côté client avec React ou Angular). Cet article porte sur le rendu côté client avec React.

1. Le modèle peut également regrouper les pages afin qu’elles soient chargées de manière synchrone, ce qui réduit le nombre de rechargements de page nécessaires.

   Dans l’exemple de l’application We.Retail Journal, les pages `home`, `page-1`, `page-2` et `page-3` sont chargées de manière synchrone, car les visiteurs visitent généralement toutes ces pages.

   Ce comportement n’est pas obligatoire et est entièrement définissable.

   ![Regroupement d’éléments du projet SPA WKND](assets/wknd-pages.png)

1. Pour voir cette différence de comportement, rechargez la page `home` et effacez l’activité de réseau de l’Inspecteur. Accédez à la `page-1` dans le menu de page et vérifiez que la seule activité de réseau est une requête d’image de la `page-1`. La `page-1` elle-même n’a pas besoin de se charger.

   ![Activité de réseau du projet SPA WKND – page-1](assets/wknd-page1-network.png)

### Interaction avec l’éditeur de SPA {#interaction-with-the-spa-editor}

L’exemple d’application de projet SPA WKND montre clairement comment l’application se comporte et est chargée lorsqu’elle est publiée, en exploitant les services de contenu pour la diffusion de contenu JSON et le chargement asynchrone des ressources.

De plus, pour le créateur de contenu, la création de contenu à l’aide d’un éditeur de SPA est transparente dans AEM.

Dans la section suivante, nous allons examiner le contrat qui permet à l’éditeur de SPA de relier les composants de la SPA aux composants d’AEM et d’offrir cette expérience de modification transparente.

1. Chargez l’application de projet SPA WKND dans l’éditeur et passez en mode **Aperçu**.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. À l’aide des outils de développement intégrés de votre navigateur, inspectez le contenu de la page. À l’aide de l’outil de sélection, sélectionnez un composant modifiable sur la page et affichez le détail de l’élément.

   Notez que le composant possède un nouvel attribut de données `data-cq-data-path`.

   ![Inspection des éléments du projet SPA WKND](assets/wknd-inspector.png)

   Par exemple :

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

   Ce chemin d’accès permet de récupérer et d’associer l’objet de configuration de contexte de modification de chaque composant.

   Il s’agit du seul attribut de balisage nécessaire à l’éditeur pour reconnaître ce composant comme un composant modifiable dans la SPA. En fonction de cet attribut, l’éditeur de SPA détermine quelle configuration modifiable est associée au composant, de sorte que l’image, la barre d’outils correctes, etc., sont chargées.

   Certains noms de classe spécifiques sont également ajoutés en vue de marquer les espaces réservés, ainsi que pour la fonctionnalité de glisser-déposer des ressources.

   >[!NOTE]
   >
   >Ce comportement diffère des pages générées côté serveur dans AEM, où un élément `cq` est inséré pour chaque composant modifiable.
   >
   >Cette approche dans l’éditeur de SPA élimine la nécessité d’injecter des éléments personnalisés, en n’utilisant qu’un attribut de données supplémentaire, ce qui rend le balisage plus simple pour le développeur frontal.

## Étapes suivantes {#next-steps}

Maintenant que vous comprenez l’expérience de modification SPA dans AEM et savez comment une SPA est liée à l’éditeur de SPA, nous allons examiner de plus près la conception des SPA.

* La section [Prise en main des SPA dans AEM avec React](getting-started-react.md) indique comment une SPA de base est créée pour fonctionner avec l’éditeur de SPA dans AEM à l’aide de React
* La section [Prise en main des SPA dans AEM avec Angular](getting-started-angular.md) indique comment une SPA de base est créée pour fonctionner avec l’éditeur de SPA dans AEM à l’aide d’Angular
* La section [Présentation de l’éditeur de SPA](editor-overview.md) examine de plus près le modèle de communication entre AEM et la SPA.
* La section [Développement de SPA pour AEM](developing.md) décrit comment impliquer les développeurs front-end dans le développement d’une SPA pour AEM et décrit de quelle manière les SPA interagissent avec l’architecture d’AEM.
