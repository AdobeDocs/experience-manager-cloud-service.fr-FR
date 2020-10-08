---
title: Repository Modernizer
description: Repository Modernizer
translation-type: tm+mt
source-git-commit: 5da0d4cc8c6d8781dd7cce8bbbde207568a6d10b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# Repository Modernizer {#repo-modernizer}

Repository Modernizer est un utilitaire conçu pour restructurer les paquets de projets existants en séparant le contenu et le code en paquets distincts afin d&#39;être compatible avec la structure de projet définie pour Adobe Experience Manager en tant que Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager en tant que Cloud Service apporte de nombreuses nouvelles fonctionnalités et possibilités dans vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. A un niveau élevé, AEM exige une séparation du **contenu** et du **code** en sous-packages distincts pour respecter la division entre contenu mutable et contenu immuable. Pour plus d&#39;informations sur la nouvelle structure [de projet AEM pour Cloud Service, veuillez consulter la Structure](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) AEM projet.

Repository Modernizer crée une structure de projet Cloud Service compatible AEM en créant la structure de déploiement suivante :

* `ui.apps` se déploie sur `/apps` et contient tout le code

* `ui.content` se déploie sur des zones pouvant être écrites à l’exécution (par ex. `/content`, `/conf`, `/home``/apps`ou autre) et contient tout le contenu et la configuration.

* `all` est un package de conteneur qui contient les sous-packages `ui.apps` et `ui.content`.

>[!NOTE]
>La structure du projet est basée sur l&#39; *Archétype 24* pour les paquets et leurs `pom.xml/filter.xml files`paquets. Refer to [Archetype 24](https://github.com/adobe/aem-project-archetype) for more details.

## Utilisation de Repository Modernizer {#using-repo-modernizer}

* Par l&#39;intermédiaire de l&#39;interface de ligne de commande des E/S d&#39;Adobe : Il est recommandé d&#39;utiliser Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (AEM en tant que module externe de refactorisation du code Cloud Service pour l&#39;interface de ligne de commande des E/S d&#39;Adobe).

   Reportez-vous à la ressource **[Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser le module externe.

* En tant qu&#39;utilitaire autonome : Repository Modernizer peut également être exécuté en tant qu&#39;utilitaire autonome.

   Reportez-vous à la ressource **[Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** pour apprendre à utiliser cet outil.

   >[!NOTE]
   >
   >Repository Modernizer est développé à l’aide de NodeJS. Il est recommandé d’installer NodeJS 10.0+.
