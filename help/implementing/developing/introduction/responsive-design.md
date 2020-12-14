---
title: Responsive Design
description: Le Responsive Design permet d’afficher les mêmes expériences sur plusieurs appareils selon différentes orientations.
translation-type: tm+mt
source-git-commit: a3b2a66958fd8d3a68b450938c5c18053f00b998
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---


# Responsive Design {#responsive-design}

Concevez vos expériences afin qu’elles s’adaptent à la fenêtre dans laquelle elles sont affichées. Le Responsive Design permet d’afficher les mêmes pages sur plusieurs appareils dans les deux orientations. L’image suivante présente différentes méthodes par lesquelles une page peut s’adapter aux changements de taille de la fenêtre d’affichage :

* Mise en page : utilisez des mises en page à une seule colonne pour les fenêtres d’affichage plus petites et des mises en page à plusieurs colonnes pour les fenêtres d’affichage plus grandes.
* Taille du texte : utilisez un texte plus grand (pour les titres, par exemple) dans les fenêtres d’affichage de plus grande taille.
* Contenu : n’insérez que le contenu le plus important en cas de visualisation sur des appareils de petite taille.
* Navigation : des outils spécifiques à l’appareil sont fournis pour accéder à d’autres pages.
* Images : diffusion de rendus d’image adaptés à la fenêtre d’affichage client en fonction des dimensions de la fenêtre.

![Exemples de Responsive Design](assets/responsive-example.png)

Développez des applications Adobe Experience Manager (AEM) qui génèrent du code HTML5 s’adaptant à plusieurs tailles de fenêtre et orientations. À titre d’exemple, les plages de largeurs de fenêtre d’affichage suivantes correspondent à divers types d’appareil et à diverses orientations :

* Largeur maximale de 480 pixels (téléphone, portrait)
* Largeur maximale de 767 pixels (téléphone, paysage)
* Largeur entre 768 pixels et 979 pixels (tablette, portrait)
* Largeur entre 980 pixels et 1 199 pixels (tablette, paysage)
* Largeur de 1 200 px ou plus (ordinateur de bureau)

Consultez les rubriques suivantes pour en savoir plus sur la mise en œuvre du comportement Responsive Design :

* [Requête de média](#using-media-queries)
* [Grilles fluides](#developing-a-fluid-grid)
* [Images adaptatives](#using-adaptive-images)

Lors de la phase de conception, utilisez la barre d’outils **Émulateur** afin d’afficher un aperçu de vos pages pour différents formats d’écran.

## Avant de procéder au développement {#before-you-develop}

Avant de développer l’application AEM prenant en charge vos pages web, il convient de prendre plusieurs décisions en matière de conception. Vous devez, par exemple, disposer des informations suivantes :

* Appareils ciblés
* Tailles de fenêtre d’affichage ciblées
* Mises en page de chacune des tailles de fenêtre d’affichage ciblées

### Structure d’application {#application-structure}

La structure d’application AEM type prend en charge toutes les implémentations de Responsive Design :

* Les composants de page résident sous `/apps/<application_name>/components`
* Les modèles résident sous `/apps/<application_name>/templates`

## Utilisation des requêtes de média {#using-media-queries}

Les requêtes de média permettent une utilisation sélective des styles CSS pour le rendu des pages. Les fonctionnalités et outils de développement AEM vous permettent d’implémenter efficacement des requêtes de média dans vos applications.

Le groupe W3C fournit la recommandation [Media Queries](https://www.w3.org/TR/css3-mediaqueries/) (Requêtes de média) qui décrit cette fonctionnalité CSS3, ainsi que la syntaxe.

### Création du fichier CSS {#creating-the-css-file}

Dans votre fichier CSS, définissez les requêtes de média en fonction des propriétés des appareils que vous ciblez. La stratégie d’implémentation suivante se révèle particulièrement utile pour gérer des styles pour chaque requête de média :

* Utilisez un [dossier de bibliothèques clientes](clientlibs.md) pour définir le CSS qui est assemblé lors du rendu de la page.
* Définissez chaque requête de média et les styles associés dans des fichiers CSS distincts. Il s’avère utile d’utiliser des noms de fichier qui représentent les fonctions de périphérique de la requête de média.
* Définissez des styles communs à tous les périphériques dans un fichier CSS distinct.
* Dans le fichier css.txt du dossier Bibliothèque cliente, classez les fichiers CSS comme l’exige le fichier CSS assemblé.

Le [tutoriel WKND](develop-wknd-tutorial.md) utilise cette stratégie pour définir des styles dans la conception du site. Le fichier CSS utilisé par WKND se trouve dans `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.
