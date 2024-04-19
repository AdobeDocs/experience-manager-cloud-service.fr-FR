---
title: Concepts de création
description: Découvrez les concepts de création dans AEM, à l’aide des environnements de création, de prévisualisation et de publication.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 96%

---


# Concepts de création {#authoring-concepts}

Une installation AEM se compose généralement d’au moins deux environnements :

* Création
* Publication

Ces environnements interagissent afin que vous puissiez rendre le contenu disponible sur votre site web, pour que vos visiteurs et visiteuses puissent y accéder.

L’environnement de création fournit les mécanismes de création, de mise à jour et de révision de ce contenu avant de le publier :

* Un auteur crée et examine le contenu. Le contenu peut être de différents types, comme des pages, des ressources et des publications.
* Ce contenu sera, à un moment donné, publié sur votre site web.

![Diagramme de l’auteur, de l’éditeur et des dispatchers](/help/sites-cloud/authoring/assets/author-publish.png)

Dans l’environnement de création, les fonctions d’AEM sont accessibles dans l’interface utilisateur de création d’AEM. Dans l’environnement de publication, vous concevez l’aspect de l’interface proposée aux utilisateurs et utilisatrices.

{{edge-delivery-authoring}}

## Environnement de création {#author-environment}

L’auteur ou l’autrice travaille dans l’**environnement de création**. Cet environnement fournit une interface conviviale (interface utilisateur graphique) pour la création de contenu. L’auteur ou l’autrice doit se connecter en utilisant un compte auquel les droits d’accès appropriés sont attribués.

>[!NOTE]
>
>Votre compte doit disposer des droits d’accès appropriés pour créer, modifier ou publier du contenu.

Selon la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer de nombreuses tâches sur votre contenu, notamment (entre autres) :

* la génération d’un nouveau contenu ou la modification du contenu existant sur une page ;
* l’utilisation de modèles prédéfinis pour créer des pages de contenu ;
* la création, la modification et la gestion de vos ressources et collections ;
* le déplacement, la copie et la suppression de pages de contenu et de ressources ;
* la publication (ou l’annulation de la publication) de pages et de ressources.

Certaines tâches administratives peuvent aussi vous aider à gérer votre contenu :

* Workflows qui déterminent le mode de gestion des modifications, par exemple, appliquer une révision avant une publication
* Projets qui coordonnent des tâches individuelles

>[!NOTE]
>
>AEM est également administré à partir de l’environnement de création.

## Prévisualisation du contenu {#previewing-content}

AEM propose également un service de prévisualisation Sites qui permet aux développeurs, aux développeuses et aux personnes créant du contenu de prévisualiser l’expérience finale d’un site web avant qu’elle n’atteigne l’environnement de publication et qu’elle ne soit disponible publiquement.

Voir [Prévisualisation du contenu](/help/sites-cloud/authoring/fundamentals/previewing-content.md) pour plus de détails.

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu de votre site est publié dans l’**environnement de publication**. Ici, vos pages sont mises à la disposition de l’audience prévue, en fonction de l’aspect global de l’interface que vous avez conçue.

Pour plus d’informations sur la publication et la dépublication de pages, consultez le document [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Afin que les visiteurs et visiteuses de votre site web bénéficient de performances optimales, le **[Dispatcher](/help/implementing/dispatcher/overview.md)** met en œuvre des mécanismes de mise en cache et d’équilibrage de la charge.
