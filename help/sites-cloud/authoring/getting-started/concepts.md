---
title: Concepts de création
description: Concepts de création dans AEM
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création Concepts {#authoring-concepts}

Une installation AEM se compose généralement d’au moins deux environnements :

* Création
* Publication

Elles interagissent pour vous permettre de rendre le contenu disponible sur votre site Web afin que vos visiteurs puissent y accéder.

L’environnement de création fournit les mécanismes permettant de créer, de mettre à jour et de revoir ce contenu avant de le publier :

* Un auteur crée et examine le contenu. Le contenu peut être de différents types, tels que des pages, des ressources, des publications, etc.
* Ce contenu sera, à un moment donné, publié sur votre site Web.

![Diagramme de l’auteur, de l’éditeur et des répartiteurs](/help/sites-cloud/authoring/assets/author-publish.png)

Dans l’environnement de création, la fonctionnalité d’AEM est rendue disponible par l’interface utilisateur de création d’AEM. Dans l’environnement de publication, vous concevez l’aspect de l’interface proposée aux utilisateurs.

>[!NOTE]
>
>AEM lui-même est utilisé pour publier la documentation AEM.

## Environnement de création {#author-environment}

L’auteur travaille dans ce qu’on appelle l’environnement **d’auteur**. Il s’agit d’une interface facile à utiliser (interface utilisateur graphique (interface utilisateur graphique ou interface utilisateur)) pour créer le contenu. L’auteur doit se connecter en utilisant un compte auquel les droits d’accès appropriés ont été attribués.

>[!NOTE]
>
>Votre compte doit disposer des droits d’accès appropriés pour la création, la modification ou la publication de contenu.

En fonction de la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer diverses tâches sur votre contenu, par exemple :

* Génération d’un nouveau contenu ou modification d’un contenu existant sur une page
* Utilisation de modèles prédéfinis pour créer des pages de contenu
* Création, modification et gestion de vos ressources et collections
* Déplacement, copie et suppression de pages de contenu, de ressources, etc.
* Publication (ou annulation de publication) de pages, de ressources, etc.

Certaines tâches administratives peuvent aussi vous aider à gérer votre contenu :

* Processus qui contrôlent la gestion des modifications, par exemple l’application d’une révision avant publication
* Projets qui coordonnent des tâches individuelles

>[!NOTE]
>
>AEM est également administré à partir de l’environnement de création.

## Environnement de publication {#publish-environment}

When ready, your site&#39;s content is published to the **publish environment**. Ici, vos pages sont mises à la disposition de l’audience prévue, en fonction de l’aspect global de l’interface que vous avez conçue.

Pour plus d’informations sur la publication et l’annulation de publication de pages, voir le document [Publication de pages.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

## Répartiteur {#dispatcher}

To optimize performance for visitors to your website, the **[dispatcher](/help/implementing/dispatcher/overview.md)**implements load balancing and caching.
