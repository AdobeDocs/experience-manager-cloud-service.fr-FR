---
title: Création et publication de concepts
description: Découvrez les concepts de création dans AEM, à l’aide des environnements de création, de prévisualisation et de publication.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 30%

---


# Création et publication de concepts {#authoring-publishing}

Pour un auteur de contenu, une installation AEM as a Cloud Service peut être considérée comme trois niveaux principaux à son niveau le plus élémentaire

* Niveau de création
* Niveau de prévisualisation
* Niveau de publication

Ces niveaux interagissent pour vous permettre de rendre le contenu disponible sur votre site web afin que vos visiteurs puissent y accéder. Le workflow de base est le suivant :

1. Les auteurs de contenu créent leur contenu à l’aide du niveau Auteur.
1. Les auteurs de contenu mettent leur contenu à la disposition des réviseurs pour un aperçu au niveau Aperçu.
1. Une fois que le contenu est prêt pour la consommation publique, les auteurs publient le contenu à l’aide du niveau de publication.

Le contenu peut être de nombreux types différents, notamment des pages, des ressources et des publications. À la discrétion de l’auteur, l’aperçu du contenu peut être ignoré.

![Diagramme de l’auteur, de l’éditeur et des dispatchers](assets/author-publish.jpg)

Pour plus d’informations sur l’architecture technique d’AEM as a Cloud Service, consultez le document [Introduction à l’architecture d’Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md).

{{edge-delivery-authoring}}

## Création de contenu {#author-environment}

L’environnement de création du niveau Auteur fournit une interface utilisateur graphique facile à utiliser pour créer du contenu. L’auteur ou l’autrice doit se connecter en utilisant un compte auquel les droits d’accès appropriés sont attribués.

Selon la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer de nombreuses tâches sur votre contenu, notamment (entre autres) :

* la génération d’un nouveau contenu ou la modification du contenu existant sur une page ;
* l’utilisation de modèles prédéfinis pour créer des pages de contenu ;
* la création, la modification et la gestion de vos ressources et collections ;
* le déplacement, la copie et la suppression de pages de contenu et de ressources ;
* la publication (ou l’annulation de la publication) de pages et de ressources.

Certaines tâches administratives peuvent aussi vous aider à gérer votre contenu :

* Workflows qui déterminent le mode de gestion des modifications, par exemple, appliquer une révision avant une publication
* Projets qui coordonnent des tâches individuelles

AEM est également administré à partir de l’environnement de création.

Consultez le document [Guide de démarrage rapide pour la création](/help/sites-cloud/authoring/quick-start.md) pour obtenir un aperçu du processus de création.

## Prévisualisation du contenu {#previewing-content}

AEM propose également un service d’aperçu qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Consultez le document [Prévisualisation du contenu](/help/sites-cloud/authoring/sites-console/previewing-content.md) pour plus d’informations.

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu de votre site est publié dans l’environnement de publication du niveau de publication. Ici, les pages du site web sont mises à la disposition de l’audience prévue, en fonction de l’aspect de votre modèle de contenu.

Consultez le document [Publication de pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md) pour plus d’informations sur la publication et la dépublication de pages.

## Dispatcher {#dispatcher}

Pour optimiser les performances des visiteurs de votre site web, le **[Dispatcher](/help/implementing/dispatcher/overview.md)** implémente l’équilibrage de charge et la mise en cache pour les niveaux de publication et de prévisualisation.
