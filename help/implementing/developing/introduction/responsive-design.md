---
title: Responsive Design
description: Avec le responsive design, les mêmes expériences peuvent être affichées efficacement sur plusieurs appareils dans plusieurs orientations.
exl-id: be645062-d6d6-45a2-97dc-d8aa235539b8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 57%

---

# Responsive Design {#responsive-design}

Concevez vos expériences afin qu’elles s’adaptent à la fenêtre dans laquelle elles sont affichées. Le Responsive Design permet d’afficher efficacement les mêmes pages sur plusieurs appareils dans les deux orientations. L’image suivante montre certaines façons dont une page peut répondre aux modifications de la taille de la fenêtre d’affichage :

* Mise en page : utilisez des mises en page à une seule colonne pour les fenêtres d’affichage plus petites et des mises en page à plusieurs colonnes pour les fenêtres d’affichage plus grandes.
* Taille du texte : utilisez une taille de texte plus grande (le cas échéant, comme des en-têtes) dans les fenêtres d’affichage plus grandes.
* Contenu : incluez uniquement le contenu le plus important lors de l’affichage sur des appareils plus petits.
* Navigation : des outils spécifiques à l’appareil sont fournis pour accéder à d’autres pages.
* Images : diffusion de rendus d’image adaptés à la fenêtre d’affichage client en fonction des dimensions de la fenêtre.

![Exemples de Responsive Design](assets/responsive-example.png)

Développez des applications Adobe Experience Manager (AEM) qui génèrent du code HTML5 s’adaptant à plusieurs tailles de fenêtre et orientations. Par exemple, les plages de largeurs de fenêtre d’affichage suivantes correspondent à divers types d’appareils et orientations :

* Largeur maximale de 480 pixels (téléphone, portrait)
* Largeur maximale de 767 pixels (téléphone, paysage)
* Largeur entre 768 pixels et 979 pixels (tablette, portrait)
* Largeur entre 980 pixels et 1 199 pixels (tablette, paysage)
* Largeur de 1 200 px ou plus (ordinateur de bureau)

Consultez les rubriques suivantes pour en savoir plus sur l’implémentation du comportement Responsive Design :

* [Requêtes de média](#using-media-queries)
* [Grilles fluides](#developing-a-fluid-grid)
* [Images adaptatives](#using-adaptive-images)

Lors de la phase de conception, utilisez la barre d’outils **Émulateur** afin d’afficher un aperçu de vos pages pour différents formats d’écran.

## Avant Le Développement {#before-you-develop}

Avant de développer l’application AEM qui prend en charge vos pages web, plusieurs décisions de conception doivent être prises. Par exemple, vous devez disposer des informations suivantes :

* Appareils ciblés
* Tailles de fenêtre d’affichage ciblées
* Mises en page de chacune des tailles de fenêtre d’affichage ciblées

### Structure d’application {#application-structure}

La structure d’application AEM type prend en charge toutes les implémentations de Responsive Design :

* Les composants de page résident sous `/apps/<application_name>/components`
* Les modèles résident sous `/apps/<application_name>/templates`

## Utilisation de requêtes de média {#using-media-queries}

Les requêtes de média permettent l’utilisation sélective de styles CSS pour le rendu des pages. Les outils et fonctionnalités de développement AEM vous permettent d’implémenter de manière efficace et efficiente des requêtes de média dans vos applications.

Le groupe W3C fournit la recommandation [Media Queries](https://www.w3.org/TR/css3-mediaqueries/) (Requêtes de média) qui décrit cette fonctionnalité CSS3, ainsi que la syntaxe.

### Création du fichier CSS {#creating-the-css-file}

Dans votre fichier CSS, définissez des requêtes de média en fonction des propriétés des appareils que vous ciblez. La stratégie d’implémentation suivante est efficace pour gérer les styles pour chaque requête de média :

* Utilisez un [dossier de bibliothèques clientes](clientlibs.md) pour définir le CSS qui est assemblé lors du rendu de la page.
* Définissez chaque requête de média et les styles associés dans des fichiers CSS distincts. Il est conseillé d’utiliser des noms de fichier qui représentent les fonctionnalités de périphérique de la requête de média.
* Définissez des styles communs à tous les appareils dans un fichier CSS distinct.
* Dans le fichier css.txt du dossier Bibliothèque cliente, classez les fichiers CSS comme l’exige le fichier CSS assemblé.

Le [tutoriel WKND](develop-wknd-tutorial.md) utilise cette stratégie pour définir des styles dans la conception du site. Le fichier CSS utilisé par WKND se trouve dans `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.

### Utiliser des requêtes de média avec des pages AEM {#using-media-queries-with-aem-pages}

[L’exemple de projet WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) et [l’archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) utilisent le [composant principal Page](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/page.html), qui inclut les bibliothèques clientes via la politique de page.

Si votre propre composant de page n’est pas basé sur le composant principal Page, vous pouvez également inclure le dossier de bibliothèque cliente dans son script HTL ou JSP. Cela génère et référence le fichier CSS avec les requêtes de média nécessaires au fonctionnement de la grille réactive.

#### HTL {#htl}

```html
<sly data-sly-use.clientlib="${'/libs/granite/sightly/templates/clientlib.html'}">
<sly data-sly-call="${clientlib.all @ categories='apps.weretail.all'}"/>
```

#### JSP {#jsp}

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

Le script JSP génère le code HTML suivant qui référence les feuilles de style :

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## Prévisualisation pour des appareils spécifiques {#previewing-for-specific-devices}

L’émulateur vous permet de prévisualiser vos pages dans différentes tailles de fenêtre d’affichage afin de tester le comportement de votre conception en Responsive Design. Lors de la modification d’une page dans la console Sites, vous pouvez appuyer ou cliquer sur l’icône **Émulateur** pour afficher l’émulateur.

![Icône Émulateur de la barre d’outils](assets/emulator-icon.png)

Dans la barre d’outils de l’émulateur, vous pouvez appuyer ou cliquer sur l’icône **Appareils** pour afficher un menu déroulant dans lequel vous pouvez sélectionner un appareil. Lorsque vous sélectionnez un appareil, la page change afin de s’adapter à la taille de la fenêtre d’affichage.

![Barre d’outils de l’émulateur](assets/emulator.png)

### Spécification de groupes d’appareils {#specifying-device-groups}

Pour spécifier les groupes d’appareils qui apparaissent dans la liste **Appareils**, ajoutez une propriété `cq:deviceGroups` au nœud `jcr:content` de la page de modèle de votre site. La valeur de la propriété est un tableau de chemins d’accès pointant vers les nœuds du groupe d’appareils.

Par exemple, la page de modèle du site WKND est `/conf/wknd/settings/wcm/template-types/empty-page/structure`. Et le nœud de `jcr:content` sous-jacent inclut la propriété suivante :

* Nom : `cq:deviceGroups`
* Type : `String[]`
* Valeur : `mobile/groups/responsive`

Les nœuds du groupe d’appareils sont situés dans le dossier `/etc/mobile/groups`.

## Images réactives {#responsive-images}

Les pages réactives s’adaptent dynamiquement au périphérique sur lequel elles sont rendues, offrant ainsi une meilleure expérience à l’utilisateur. Cependant, il est également important que les ressources soient optimisées au point d’arrêt et sur l’appareil afin de réduire le temps de chargement de la page.

[le composant Image des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=fr) comporte des fonctionnalités telles que la sélection d’images adaptatives.

* Par défaut, le composant d’image utilise le [ servlet d’image adaptative ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/adaptive-image-servlet.html) pour fournir le rendu approprié.
* La [ Diffusion d’images optimisées pour le web ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html?lang=fr) est également disponible par le biais d’une simple case à cocher dans sa politique, qui diffuse des ressources d’image à partir de la gestion des ressources numériques au format WebP et peut réduire la taille de téléchargement d’une image d’environ 25 % en moyenne.

## Conteneur de disposition {#layout-container}

Le conteneur de disposition AEM permet d’implémenter efficacement une disposition réactive pour adapter les dimensions de la page à la fenêtre d’affichage cliente.

Consultez le document [Configuration du conteneur de dispositions et du mode de disposition](/help/sites-cloud/administering/responsive-layout.md) pour plus d’informations sur le fonctionnement du conteneur de dispositions et sur la manière d’activer les dispositions réactives pour votre contenu.
