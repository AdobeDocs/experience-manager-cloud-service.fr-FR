---
title: Sélecteur de fragment de contenu micro front-end pour Adobe Experience Manager as a Cloud Service
description: Utilisez le sélecteur de fragment de contenu micro front-end pour rechercher, rechercher et récupérer des fragments de contenu de votre application.
role: Admin, User
source-git-commit: 426e958444446174bf90a13ad831c8604fddecc4
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 11%

---


# Sélecteur de fragment de contenu micro front-end {#micro-frontend-content-fragment-selector}

Le sélecteur de fragment de contenu micro front-end fournit une interface utilisateur qui s’intègre facilement au référentiel as a Cloud Service Adobe Experience Manager (AEM). L’interface vous permet de parcourir ou de rechercher des fragments de contenu dans le référentiel et de les utiliser dans votre application.

L’interface utilisateur micro front-end est disponible dans votre application à l’aide du package Sélecteur de fragment de contenu. Toutes les mises à jour du package sont automatiquement importées et chargées dans votre application.

![Sélecteur de fragment de contenu micro front-end - Présentation](/help/headless/assets/content-fragment-selector-overview.png)

Le sélecteur de fragment de contenu offre de nombreux avantages, notamment :

* Facilité d’intégration avec n’importe quelle application Adobe.
* Facile à gérer, car les mises à jour du package du sélecteur de fragments de contenu sont automatiquement déployées vers le sélecteur de fragments de contenu disponible pour votre application. Cela signifie que votre application n’a pas besoin d’effectuer d’action pour charger les dernières modifications.
* Personnalisation facilitée grâce à l’utilisation de propriétés qui contrôlent l’affichage du sélecteur de fragments de contenu dans votre application.
* La recherche en texte intégral, associée à des filtres personnalisables, permet une navigation rapide dans les fragments de contenu au sein de l’expérience de création.
* Possibilité de changer de référentiels au sein d’une organisation IMS pour la sélection de fragments de contenu.
* Possibilité de trier les fragments de contenu et de les afficher dans l’affichage sélectionné.

## Prérequis {#prerequisites}

### Authentification IMS {#ims-authentication}

Si vous avez besoin du workflow d’authentification IMS, vous devez vous assurer que :

* L’application est en cours d’exécution sur `HTTPS`.
* L’URL de l’application figure dans la liste des URL de redirection autorisées pour le client IMS.
* Le flux de connexion IMS est configuré et rendu à l’aide d’une fenêtre contextuelle sur le navigateur web. Par conséquent, les fenêtres contextuelles doivent être activées ou autorisées sur le navigateur cible.

Si votre application est déjà authentifiée avec le workflow IMS, vous pouvez également ajouter les informations IMS appropriées à la place.

## Installation {#installation}

Utilisez le composant `ContentFragmentSelector` . Il existe plusieurs options d&#39;installation :

1. Registre NPM (registre Adobe privé)

   * Ajoutez le code suivant à `.npmrc` :

     ```html
     @aem-sites:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-sites-release/
     ```

   * Puis installer

     ```html
     npm install @aem-sites/content-fragment-selector
     ```

1. Référentiel Git

   * Ajoutez les éléments suivants aux dépendances `package.json` :

     ```html
     "@aem-sites/content-fragment-selector": "git+https://github.com/adobe/<your-private-repo-url>.git#version"
     ```

## Utilisation du sélecteur de fragment de contenu {#using-the-Content-Fragment-selector}

Une fois que le sélecteur de fragments de contenu est configuré et authentifié pour l’utiliser avec votre application AEM as a Cloud Service, vous pouvez sélectionner des fragments de contenu ou effectuer d’autres opérations pour rechercher vos fragments dans le référentiel :

![ Sélecteur de fragment de contenu ](/help/headless/assets/content-fragment-selector-using.png)

* Le sélecteur **Référentiel** en haut à droite permet de sélectionner le référentiel à utiliser
* Dans le panneau tout à gauche, vous pouvez :
   * Masquer ou afficher les dossiers du référentiel sélectionné
   * Sélectionnez un dossier spécifique pour afficher les fragments de contenu dans ce dossier.
* Dans le panneau principal, vous pouvez :
   * Sélectionner les fragments de contenu
   * Rechercher des fragments de contenu
   * Trie la liste en cours en fonction de différentes colonnes, à la fois ascendante et descendante
   * Afficher l’indicateur de format
   * Afficher, masquer et spécifier des filtres

### Masquer/Afficher le panneau {#hide-show-panel}

Pour masquer les dossiers dans le volet de navigation de gauche, cliquez sur l’icône **Masquer les dossiers**. Pour annuler les modifications, cliquez à nouveau sur l’icône **Masquer les dossiers**.

### Sélecteur de référentiels {#repository-switcher}

Le sélecteur de fragment de contenu vous permet de sélectionner un référentiel pour la sélection de fragment.

Vous pouvez sélectionner le référentiel de votre choix dans le menu déroulant **Référentiel** disponible dans la partie supérieure du panneau principal.

![ Sélecteur de fragment de contenu ](/help/headless/assets/content-fragment-repository-selector.png)

Les options de référentiel disponibles dans la liste déroulante reposent sur la propriété `repositoryId` définie dans le fichier `index.html`. Cette propriété est basée sur l’environnement de l’organisation IMS sélectionnée accessible par l’utilisateur actuellement connecté.

Les clientes et clients peuvent transmettre une `repositoryID` préférée pour effectuer le rendu de fragments à partir d’un référentiel spécifique et arrêter le rendu du sélecteur de référentiels.

### Dossiers de fragments de contenu {#content-fragments-folders}

Le référentiel de fragments de contenu est une collection de dossiers de fragments de contenu que vous pouvez utiliser pour effectuer des opérations.

### Filtres {#filters}

Le sélecteur de fragment de contenu fournit également des options de filtre prêtes à l’emploi pour affiner vos résultats de recherche. Différents filtres sont disponibles, notamment :

* **Modèle de fragment**
* **Localisation**
* **Statut** : état actuel du fragment ; `New`, `Draft`, `Published`, `Modified`, `Unpublished`
* Balises
* Utilisateurs et utilisatrices
* Heures et dates

![Options de filtre](/help/headless/assets/content-selector-filters.png)

Vous pouvez également créer un filtre de recherche par défaut à enregistrer pour une utilisation ultérieure. Pour créer des filtres de recherche personnalisés pour vos fragments de contenu, vous pouvez utiliser la propriété `filterSchema` .

### Barre de recherche {#search-bar}

Le sélecteur de fragments de contenu vous permet d’effectuer une recherche de texte intégral de fragments dans le référentiel sélectionné. Par exemple, si vous saisissez le mot-clé `wave` dans la barre de recherche, tous les fragments contenant le mot-clé `wave` dans l’une des propriétés de métadonnées s’affichent.

### Tri {#sorting}

Vous pouvez trier les fragments dans le sélecteur de fragments de contenu selon différentes propriétés. Vous pouvez également trier les fragments par ordre croissant ou décroissant.

### Type d&#39;affichage {#view-type}

Le sélecteur de fragment de contenu vous permet d’afficher le fragment dans :

* **Vue Tableau**
