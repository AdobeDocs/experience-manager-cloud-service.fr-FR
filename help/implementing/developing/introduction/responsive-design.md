---
title: Responsive Design
description: Le Responsive Design permet d’afficher les mêmes expériences sur plusieurs appareils selon différentes orientations.
source-git-commit: a3b2a66958fd8d3a68b450938c5c18053f00b998
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 50%

---


# Responsive Design {#responsive-design}

Concevez vos expériences afin qu’elles s’adaptent à la fenêtre dans laquelle elles sont affichées. Avec une conception réactive, les mêmes pages peuvent être affichées efficacement sur plusieurs appareils dans les deux orientations. L’image suivante montre certaines façons dont une page peut répondre aux modifications de la taille de la fenêtre d’affichage :

* Disposition : Utilisez des mises en page à une seule colonne pour les fenêtres d’affichage plus petites et des mises en page à plusieurs colonnes pour les fenêtres d’affichage plus grandes.
* Taille du texte : Utilisez une taille de texte plus grande (le cas échéant, comme des en-têtes) dans les fenêtres d’affichage plus grandes.
* Contenu : Inclure uniquement le contenu le plus important lors de l’affichage sur des appareils plus petits.
* Navigation : Des outils spécifiques à l’appareil sont fournis pour accéder à d’autres pages.
* Images : diffusion de rendus d’image adaptés à la fenêtre d’affichage client en fonction des dimensions de la fenêtre.

![Exemples de Responsive Design](assets/responsive-example.png)

Développez des applications Adobe Experience Manager (AEM) qui génèrent du code HTML5 s’adaptant à plusieurs tailles de fenêtre et orientations. Par exemple, les plages de largeurs de fenêtre d’affichage suivantes correspondent à divers types d’appareils et orientations :

* Largeur maximale de 480 pixels (téléphone, portrait)
* Largeur maximale de 767 pixels (téléphone, paysage)
* Largeur comprise entre 768 et 979 pixels (tablette, portrait)
* Largeur entre 980 pixels et 1 199 pixels (tablette, paysage)
* Largeur de 1 200 px ou plus (ordinateur de bureau)

Consultez les rubriques suivantes pour en savoir plus sur la mise en œuvre du comportement Responsive Design :

* [Requêtes de média](#using-media-queries)
* [Grilles fluides](#developing-a-fluid-grid)
* [Images adaptatives](#using-adaptive-images)

Lors de la phase de conception, utilisez la barre d’outils **Émulateur** afin d’afficher un aperçu de vos pages pour différents formats d’écran.

## Avant de procéder au développement {#before-you-develop}

Avant de développer l’application AEM qui prend en charge vos pages web, plusieurs décisions de conception doivent être prises. Par exemple, vous devez disposer des informations suivantes :

* Appareils ciblés
* Tailles de fenêtre d’affichage ciblées
* Mises en page de chacune des tailles de fenêtre d’affichage ciblées

### Structure d’application {#application-structure}

La structure d’application AEM type prend en charge toutes les implémentations de Responsive Design :

* Les composants de page résident sous `/apps/<application_name>/components`
* Les modèles résident sous `/apps/<application_name>/templates`

## Utilisation des requêtes de média {#using-media-queries}

Les requêtes de média permettent l’utilisation sélective de styles CSS pour le rendu des pages. AEM outils et fonctionnalités de développement vous permettent d’implémenter efficacement et efficacement des requêtes multimédias dans vos applications.

Le groupe W3C fournit la recommandation [Media Queries](https://www.w3.org/TR/css3-mediaqueries/) (Requêtes de média) qui décrit cette fonctionnalité CSS3, ainsi que la syntaxe.

### Création du fichier CSS {#creating-the-css-file}

Dans votre fichier CSS, définissez des requêtes de média en fonction des propriétés des appareils que vous ciblez. La stratégie d’implémentation suivante est efficace pour gérer les styles pour chaque requête multimédia :

* Utilisez un [dossier de bibliothèques clientes](clientlibs.md) pour définir le CSS qui est assemblé lors du rendu de la page.
* Définissez chaque requête de média et les styles associés dans des fichiers CSS distincts. Il est utile d’utiliser des noms de fichier qui représentent les fonctionnalités de périphérique de la requête multimédia.
* Définissez des styles communs à tous les appareils dans un fichier CSS distinct.
* Dans le fichier css.txt du dossier Bibliothèque cliente, classez les fichiers CSS comme l’exige le fichier CSS assemblé.

Le [tutoriel WKND](develop-wknd-tutorial.md) utilise cette stratégie pour définir des styles dans la conception du site. Le fichier CSS utilisé par WKND se trouve dans `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.
