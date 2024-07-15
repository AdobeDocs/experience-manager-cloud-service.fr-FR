---
title: Concepts de création et de publication
description: Découvrez les concepts de création dans AEM, à l’aide des environnements de création, de prévisualisation et de publication.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 30%

---


# Concepts de création et de publication {#authoring-publishing}

Pour un auteur de contenu, une installation AEM as a Cloud Service peut être considérée comme trois niveaux principaux à son niveau le plus élémentaire.

* Niveau de création
* Niveau d’aperçu
* Niveau de publication

Ces niveaux interagissent pour vous permettre de rendre le contenu disponible sur votre site web afin que vos visiteurs puissent y accéder. Le workflow de base est le suivant :

1. Les auteurs de contenu créent leur contenu à l’aide du niveau Auteur.
1. Les auteurs de contenu mettent leur contenu à la disposition des réviseurs pour la prévisualisation à l’aide du niveau d’aperçu.
1. Une fois que le contenu est prêt pour une utilisation publique, les auteurs le publient à l’aide du niveau de publication.

Le contenu peut être de différents types, y compris des pages, des ressources et des publications. L’aperçu du contenu peut être ignoré à la discrétion de l’auteur.

![Diagramme de l’auteur, de l’éditeur et des dispatchers](assets/author-publish.jpg)

Pour plus d’informations sur l’architecture technique d’AEM as a Cloud Service, consultez le document [Introduction à l’architecture d’Adobe Experience Manager as a Cloud Service.](/help/overview/architecture.md)

{{edge-delivery-authoring}}

## Création de contenu {#author-environment}

L’environnement de création du niveau Auteur offre une interface utilisateur graphique conviviale pour créer du contenu. L’auteur ou l’autrice doit se connecter en utilisant un compte auquel les droits d’accès appropriés sont attribués.

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

Consultez le document [Guide de démarrage rapide de la création](/help/sites-cloud/authoring/quick-start.md) pour une présentation du processus de création.

## Prévisualisation du contenu {#previewing-content}

AEM propose également un service de prévisualisation qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Pour plus d’informations, consultez le document [Aperçu du contenu](/help/sites-cloud/authoring/sites-console/previewing-content.md) .

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu de votre site est publié dans l’environnement de publication du niveau de publication. Ici, les pages du site web sont mises à la disposition de l’audience prévue, conformément à l’apparence de votre modèle de contenu.

Pour plus d’informations sur la publication et l’annulation de la publication de pages, voir le document [Publication de pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md) .

## Dispatcher {#dispatcher}

Pour optimiser les performances des visiteurs de votre site web, **[Dispatcher](/help/implementing/dispatcher/overview.md)** met en oeuvre l’équilibrage de charge et la mise en cache pour les niveaux de publication et de prévisualisation.
