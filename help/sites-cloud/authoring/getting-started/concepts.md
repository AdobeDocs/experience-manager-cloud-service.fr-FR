---
title: Concepts de création
description: Concepts de création dans AEM
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création   Concepts {#authoring-concepts}

Une installation AEM se compose généralement d’au moins deux environnements :

* Création
* Publication

Ces environnements interagissent afin que vous puissiez rendre le contenu disponible sur votre site web, pour que vos visiteurs puissent y accéder.

L’environnement de création fournit les mécanismes de création, de mise à jour et de révision de ce contenu avant de le publier :

* Un auteur crée et examine le contenu. Le contenu peut être de différents types, tels que des pages, des ressources, des publications, etc.
* Ce contenu sera, à un moment donné, publié sur votre site web.

![Diagramme de l’auteur, de l’éditeur et des dispatchers](/help/sites-cloud/authoring/assets/author-publish.png)

Dans l’environnement de création, les fonctions d’AEM sont accessibles dans l’interface utilisateur d’AEM. Dans l’environnement de publication, vous concevez l’aspect de l’interface proposée aux utilisateurs.

>[!NOTE]
>
>La documentation d’AEM est elle-même publiée grâce à AEM.

## Environnement de création {#author-environment}

L’auteur travaille dans ce qu’on appelle l’**environnement de création**. Il s’agit d’une interface facile à utiliser (interface utilisateur graphique) pour créer le contenu. L’auteur doit se connecter en utilisant un compte auquel les droits d’accès appropriés ont été attribués.

>[!NOTE]
>
>Votre compte doit disposer des droits d’accès appropriés pour la création, la modification ou la publication de contenu.

En fonction de la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer diverses tâches sur votre contenu, par exemple :

* la génération d’un nouveau contenu ou modification du contenu existant sur une page ;
* l’utilisation de modèles prédéfinis pour créer des pages de contenu ;
* la création, la modification et la gestion de vos ressources et collections ;
* le déplacement, la copie et la suppression de pages de contenu, de ressources, etc. ;
* la publication (ou l’annulation de la publication) de pages, de ressources, etc.

Certaines tâches administratives peuvent aussi vous aider à gérer votre contenu :

* Workflows qui déterminent le mode de gestion des modifications, par exemple, appliquer une révision avant une publication
* Projets qui coordonnent des tâches individuelles

>[!NOTE]
>
>AEM est également administré à partir de l’environnement de création.

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu de votre site est publié dans l’**environnement de publication**. Ici, vos pages sont mises à la disposition de l’audience prévue, en fonction de l’aspect global de l’interface que vous avez conçue.

Pour plus d’informations sur la publication et l’annulation de la publication de pages, consultez le document [Publication de pages.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

## Dispatcher {#dispatcher}

Afin que les visiteurs de votre site web bénéficient de performances optimales, le **[dispatcher](/help/implementing/dispatcher/overview.md)**met en œuvre des mécanismes de mise en cache et d’équilibrage de la charge.
