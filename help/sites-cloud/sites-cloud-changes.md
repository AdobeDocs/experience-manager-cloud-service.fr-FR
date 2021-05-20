---
title: Modifications notables apportées à AEM Sites dans AEM Cloud Service
description: Modifications notables apportées à AEM Sites dans AEM Cloud Service
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Modifications notables apportées à AEM Sites as a Cloud Service {#notable-changes}

AEM Sites as a Cloud Service offre des fonctionnalités de gestion de l’expérience intégrées de façon natives au cloud à la plate-forme AEM as a Cloud Service. Outre les principaux avantages d’AEM as a Cloud Service, tels que l’évolutivité native du cloud, le temps de disponibilité et la mise à jour permanente d’AEM Sites as a Cloud Service, vous pouvez également apporter un certain nombre de modifications et d’ajouts propres à AEM Sites.

>[!NOTE]
>Ce document met en évidence les modifications notables apportées à AEM Sites. Pour les modifications générales apportées à AEM as a Cloud Service et à d’autres modules, voir :
>
>* [Introduction à Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Présentation d’AEM as a Cloud Service – Nouveautés et différences](/help/overview/what-is-new-and-different.md)
* [Architecture](/help/core-concepts/architecture.md) d’Adobe Experience Manager as a Cloud Service
* [Modifications notables apportées à AEM as a Cloud Service (notes de mise à jour)](/help/release-notes/aem-cloud-changes.md)
* [Modifications notables apportées à AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Introduction à AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutoriels sur Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


Les modifications et ajouts dans AEM Sites as a Cloud Service sont les suivants :

* [Opérations de page asynchrones](#asynchronous-page-operations)
* [Nouveau site de référence et tutoriel](#new-reference-site-and-tutorial)

## Opérations de page asynchrones {#asynchronous-page-operations}

Dans AEM Cloud Service, les opérations qui bloquaient traditionnellement l’interface utilisateur ont été ventilées en tâches plus petites qui s’exécutent en arrière-plan.

* Déplacer des pages
* Déployer des pages

L’initiateur de ces actions peut vérifier leur état dans une nouvelle interface utilisateur sur `/mnt/overlay/dam/gui/content/asyncjobs.html`.

>[!NOTE]
L’utilisateur du système n’a pas besoin de modifier cette nouvelle fonctionnalité pour pouvoir l’utiliser. Cette modification est simplement consignée dans ce document, car elle constitue un changement de comportement par rapport aux versions sur site précédentes d’AEM.

## Nouveau site de référence et tutoriel{#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), le nouveau site de référence AEM, a été mis à jour et publié afin de présenter les bonnes pratiques de création d’un site web avec AEM, ainsi que l’ensemble complet des fonctionnalités, composants et modèles de déploiement disponibles dans AEM. Le nouveau site de référence et le tutoriel[](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) qui l’accompagne abordent des sujets fondamentaux tels que la configuration de projet, les composants principaux, les modèles modifiables, les bibliothèques client et le développement de composants avec Adobe Experience Manager Sites.

Auparavant, We.Retail était installé par défaut avec AEM (sauf lorsqu’il était démarré en mode de production). Désormais, aucun site de référence ne sera installé par défaut. Au lieu de cela, vous trouverez le [git repo](https://github.com/adobe/aem-guides-wknd/) et [le tutoriel associé](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) au code du site de référence WKND mis à jour.

## Fonctionnalités non disponibles lors de l’exécution {#capabilities-not-available-at-runtime}

AEM as a Cloud Service est toujours activé et toujours à jour. Il est nécessaire pour cela de séparer le référentiel AEM du contenu immuable et mutable et d’interdire l’accès au contenu immuable au moment de l’exécution. Pour plus d’informations sur le contenu mutable ou immuable, reportez-vous à la section Zones [mutables ou immuables du référentiel](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Du fait que le contenu immuable est inaccessible au moment de l’exécution, les opérations d’AEM Sites suivantes ne sont pas disponibles au moment de l’exécution :

* Traduction du dictionnaire i18n
* Mode développeur dans l’éditeur de page d’AEM Sites

Ces fonctionnalités peuvent être utilisées par le biais d’instances de développement locales autonomes d’AEM as a Cloud Service, pour la mise à jour du contenu et du code dans AEM en tant que référentiel GIT de Cloud Service, mais pas dans les instances d’exécution hébergées.
