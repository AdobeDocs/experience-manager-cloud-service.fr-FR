---
title: Concepts de création
description: Découvrez les concepts de création dans AEM, à l’aide des environnements de création, de prévisualisation et de publication.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 53d4e22805774c0b994ee2bba429c19506639014
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 40%

---


# Concepts de création {#authoring-concepts}

Une installation AEM se compose généralement d’au moins deux environnements :

* Création
* Publication

Ces environnements interagissent pour vous permettre de rendre le contenu disponible sur votre site web afin que vos visiteurs puissent y accéder.

L’environnement de création fournit les mécanismes de création, de mise à jour et de révision de ce contenu avant de le publier :

* Un auteur crée et examine le contenu. Le contenu peut être de différents types, y compris des pages, des ressources et des publications.
* Ce contenu sera, à un moment donné, publié sur votre site web.

![Diagramme de l’auteur, de l’éditeur et des dispatchers](/help/sites-cloud/authoring/assets/author-publish.png)

Dans l’environnement de création, les fonctionnalités d’AEM sont disponibles via AEM interface utilisateur de création. Pour l’environnement de publication, vous concevez l’aspect de l’interface proposée aux utilisateurs.

{{edge-delivery-authoring}}

## Environnement de création {#author-environment}

L’auteur travaille dans ce que l’on appelle **environnement de création**. Cet environnement fournit une interface conviviale (interface utilisateur graphique) pour la création de contenu. L’auteur doit se connecter à l’aide d’un compte auquel les droits d’accès appropriés sont attribués.

>[!NOTE]
>
>Votre compte doit disposer des droits d’accès appropriés pour créer, modifier ou publier du contenu.

Selon la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer de nombreuses tâches sur votre contenu, notamment :

* la génération d’un nouveau contenu ou modification du contenu existant sur une page ;
* Utilisation de modèles prédéfinis pour créer des pages de contenu
* la création, la modification et la gestion de vos ressources et collections ;
* Déplacement, copie et suppression de pages de contenu et de ressources.
* Publication (ou annulation de la publication) de pages et de ressources.

Il existe également des tâches administratives pour vous aider à gérer votre contenu :

* Workflows qui déterminent le mode de gestion des modifications, par exemple, appliquer une révision avant une publication
* Projets qui coordonnent des tâches individuelles

>[!NOTE]
>
>AEM est également administré à partir de l’environnement de création.

## Prévisualisation du contenu {#previewing-content}

AEM propose également un service de prévisualisation de sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Voir [Prévisualisation du contenu](/help/sites-cloud/authoring/fundamentals/previewing-content.md) pour plus de détails.

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu de votre site est publié dans l’**environnement de publication**. Ici, vos pages sont mises à la disposition de l’audience prévue, en fonction de l’aspect global de l’interface que vous avez conçue.

Pour plus d’informations sur la publication et la dépublication de pages, consultez le document [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Pour optimiser les performances des visiteurs de votre site Web, la variable **[Dispatcher](/help/implementing/dispatcher/overview.md)** met en oeuvre l’équilibrage de charge et la mise en cache.
