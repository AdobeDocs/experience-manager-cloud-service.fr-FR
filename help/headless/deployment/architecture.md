---
title: Architecture d’AEM sans tête
description: Découvrez l’architecture de haut niveau d’Adobe Experience Manager en ce qui concerne un déploiement sans tête. Comprendre le rôle des services AEM Author, Preview et Publish et le modèle de déploiement recommandé pour les applications sans interface utilisateur graphique.
feature: Content Fragments,GraphQL API
exl-id: 5ba6921f-b06e-463d-b956-d1fb434090c9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 18%

---

# Architecture d’AEM sans tête

Un environnement d’AEM type est constitué d’un service de création, d’un service de publication et d’un service d’aperçu facultatif.

* **Le service Auteur** permet aux utilisateurs internes de créer, gérer et prévisualiser du contenu.

* **Le service de publication** est considéré comme l’environnement « En ligne » et est généralement celui avec lequel les utilisateurs finaux interagissent. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication. Le modèle de déploiement le plus courant avec les applications découplées AEM est de connecter la version de production de l’application à un service de publication AEM.

* **Le service Preview** est fonctionnellement identique au **Service de publication**. Toutefois, elle est mise à la disposition des utilisateurs internes uniquement. Cela en fait un système idéal pour que les approbateurs puissent passer en revue les modifications de contenu à venir avant d’être mis en ligne pour les utilisateurs finaux.

* **Le Dispatcher** est un serveur web statique qui est alimenté par le module Dispatcher d’AEM. Il fournit des fonctionnalités de mise en cache et une autre couche de sécurité. Le **Dispatcher** se trouve devant le **Publier** et **Aperçu** services.

Dans un programme as a Cloud Service AEM, vous pouvez avoir plusieurs environnements : développement, évaluation et production. Chaque environnement possède sa propre **Auteur**, **Publier**, et **Aperçu** services. Pour en savoir plus sur la gestion [environnements ici](/help/implementing/cloud-manager/manage-environments.md)

## Modèle de publication de création

Le modèle de déploiement le plus courant avec les applications découplées AEM est de connecter la version de production de l’application à un service de publication AEM.

![Architecture de publication de création](assets/autho-publish-architecture-diagram.png)

Le diagramme ci-dessus illustre ce schéma de déploiement commun.

1. A **Auteur de contenu** utilise le service AEM Author pour créer, modifier et gérer du contenu.
1. Le **Auteur de contenu** et d’autres utilisateurs internes peuvent prévisualiser le contenu directement sur le service de création. Une version Aperçu de l’application peut être configurée pour se connecter au service Auteur.
1. Une fois le contenu approuvé, il peut être publié sur le service AEM Publish.
1. Le **Dispatcher** est un calque devant la propriété **Publier** qui peut mettre en cache certaines requêtes et fournir une couche de sécurité.
1. Les utilisateurs finaux interagissent avec la version de production de l’application. L’application de production se connecte au service de publication via Dispatcher et utilise les API GraphQL pour demander et utiliser du contenu.

## Aperçu du déploiement de la publication par l’auteur

Une autre option pour les déploiements sans interface consiste à incorporer une **Aperçu AEM** service. Grâce à cette approche, le contenu peut d’abord être publié dans la variable **Aperçu** et une version d’aperçu de l’application sans interface utilisateur graphique peuvent s’y connecter. L’avantage de cette approche est que la variable **Aperçu** peut être configuré avec les mêmes exigences et autorisations d’authentification que le service **Publier** , ce qui facilite la simulation de l’expérience de production.

![Architecture de création d’aperçu et de publication](assets/author-preview-publish-architecture-diagram.png)

1. A **Auteur de contenu** utilise le service AEM Author pour créer, modifier et gérer du contenu.
1. Le contenu est d’abord publié sur le service d’aperçu AEM.
1. Il est possible de configurer une version Aperçu de l’application qui se connecte au service Aperçu.
1. Une fois que le contenu a été révisé et approuvé, il peut être publié sur le service AEM Publish.
1. Les utilisateurs finaux interagissent avec la version de production de l’application. L’application de production se connecte au service de publication via Dispatcher et utilise les API GraphQL pour demander et utiliser du contenu.
