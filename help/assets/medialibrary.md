---
title: Différence entre AEM Assets et AEM Media Library
description: Forum aux questions concernant AEM Assets et AEM Media Library, y compris les différences entre les deux.
contentOwner: AG
translation-type: ht
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Questions fréquentes sur la différence entre AEM Assets et AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM) Assets fait partie intégrante de la plateforme AEM. Cette intégration parfaite est vue comme un avantage important d’AEM et garantit une homogénéité de gestion de contenu et de productivité élevée pour les auteurs de contenu. 

## Qu’est-ce qu’AEM Assets ?{#what-is-aem-assets}

AEM Assets est une application de la plateforme AEM qui permet à nos clients de gérer leurs ressources numériques (images, documents, vidéos et clips audio) dans un référentiel basé sur le web. Les ressources AEM comprennent la prise en charge des métadonnées, les rendus, l’outil de recherche Digital Asset Management et l’administration via l’interface utilisateur.

## Qu’est-ce que la bibliothèque multimédia AEM ?{#what-is-the-aem-media-library}

La bibliothèque multimédia AEM est un élément désigné du référentiel de contenu de la gestion de contenu web d’AEM où les images et d’autres ressources partagées sont enregistrées. La bibliothèque multimédia utilise les fonctionnalités de gestion des actifs numériques de la gestion de contenu web d’AEM.

## Que m’offre AEM Assets qui ne soit pas déjà inclus dans la gestion de contenu web d’AEM ?   {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Les fonctionnalités uniques disponibles uniquement pour les clients AEM Assets sont : 

1. La possibilité d’extraire et de modifier des métadonnées autres que le titre, les balises et la description
1. L’administrateur d’AEM Assets, accessible via l’écran de bienvenue en cliquant sur le deuxième bouton à côté de siteadmin
1. Toutes les étapes de workflow associées à la gestion des ressources numériques, à savoir l’assimilation AEM Assets, la suppression AEM Assets, la gestion des sous-ressources d’AEM Assets et l’extraction de métadonnées d’AEM Assets
1. Les bibliothèques, y compris « dam » dans l’espace de modules

L’utilisation de ces fonctions nécessite une licence AEM Assets valide.

## AEM Assets est-il disponible en tant que module distinct ?   {#is-aem-assets-available-as-a-separate-package}

Non. Pour faciliter l’installation et le déploiement, toutes les applications et modules complémentaires d’AEM sont fournis dans un module unique dans lequel toutes les fonctionnalités sont incluses. Cela ne signifie pas que vous avez le droit d’utiliser toutes les fonctionnalités incluses dans le module.

## Je souhaite modifier les métadonnées des ressources numériques. Ai-je besoin d’AEM Assets ?   {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Si vous prévoyez de modifier les métadonnées autres que le titre, la description et les balises, vous aurez besoin d’une licence AEM Assets. 

## Je souhaite utiliser le prédicat de catégorie sur mon site web. Ai-je besoin d’AEM Assets ?   {#i-want-to-use-the-category-predicate-on-my-website-do-i-need-aem-assets}

Oui, le prédicat de catégorie ainsi que tous les autres composants utilisés avec le centre de presse Geometrixx font partie d’AEM Assets et nécessitent une licence AEM Assets.

## Je souhaite redimensionner automatiquement les images lors de l’importation. Ai-je besoin d’AEM Assets ?   {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Oui. Le redimensionnement d’image, la transformation automatisée lors du traitement et la possibilité de gérer les rendus sont des fonctionnalités d’AEM Assets et nécessitent une licence AEM Assets. 

## Je souhaite redimensionner des images à l’aide d’un composant image personnalisé. Ai-je besoin d’AEM Assets ?   {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

Le composant image fait partie de la gestion du contenu web d’AEM. La bibliothèque d’images utilisée par le composant image (et par AEM Assets) fait partie de la plateforme AEM et ne nécessite de licence AEM Assets. 

## Comment puis-je empêcher mes utilisateurs d’utiliser AEM Assets si je ne dispose pas d’une licence AEM Assets ?{#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Vous pouvez supprimer tous les workflows, composants, taxonomies et options d’AEM Assets, ainsi que l’administrateur AEM Assets à partir d’AEM. Cela empêche vos utilisateurs d’utiliser accidentellement des fonctionnalités d’AEM Assets pour lesquelles vous ne disposez pas de licence. 

## Je souhaite ajouter des images à une page et recadrer ou redimensionner ces images. Ai-je besoin d’AEM Assets ?   {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Pour ce cas d’utilisation, il n’est pas nécessaire d’acheter AEM Assets. Il n’est même pas nécessaire d’utiliser la bibliothèque multimédia pour les images d’un site web, car le composant d’image dynamique permet de transférer des images directement dans la page.

## Liste détaillée des fonctionnalités disponibles dans AEM Assets par rapport à Media Library   {#listoffeatures}

**AEM Assets**

* Collections et Lightbox
* Propriétés et gestion avancées des métadonnées
* Adobe Asset Link (connexion à Creative Cloud abonnement Entreprise)
* Application de bureau AEM
* Profils de traitement
* Intégration du serveur InDesign
* Modèles de ressources et infrastructure de producteur de catalogue
* Ressources liées Adobe Photoshop, Illustrator et InDesign
* Gestion des ressources multilingues
* Intégration PIM
* Gestion des droits
* Prise en charge de Camera RAW
* Gestion et configuration des facettes de recherche
* Workflows DAM préconfigurés (par exemple, séance photo)
* Rapports et analyses des ressources : statistiques sur les ressources
* Gestion des ressources 3D
* Ressources connectées
* Brand Portal
* Accès en libre-service
* Parcourir, rechercher et télécharger
* Partage de collections et de dossiers
* Outils d’administration
* Balises intelligentes
* Recherche visuelle
* Interface utilisateur d’administration Assets

**Media Library**

* Propriétés des métadonnées de base
* Gestion des balises
* Gestion de version
* Rendus statiques
* Projets, tâches, création de workflows
* Flux d’activités (chronologie)
* Query Builder (API)
* Intégration de Marketing Cloud
* Personnalisation et extension de l’interface utilisateur
* Commentaires et annotations