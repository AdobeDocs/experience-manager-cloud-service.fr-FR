---
title: Repository Modernizer
description: Repository Modernizer
translation-type: tm+mt
source-git-commit: 5da0d4cc8c6d8781dd7cce8bbbde207568a6d10b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 100%

---


# Repository Modernizer {#repo-modernizer}

Repository Modernizer est un utilitaire conçu pour restructurer les modules de projets existants en séparant le contenu et le code en modules discrets compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du **contenu** et du **code** en sous-modules discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Pour plus d’informations sur la nouvelle structure de projet AEM pour Cloud Service, reportez-vous à [Structure de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html).

Repository Modernizer crée une structure de projet AEM Cloud Service compatible en créant la structure de déploiement suivante :

* Le module `ui.apps` se déploie sur `/apps` et contient l’intégralité du code.

* Le module `ui.content` se déploie sur des zones pouvant être écrites à l’exécution (par ex., `/content`, `/conf`, `/home` ou toute zone autre que `/apps`) et contient l’ensemble du contenu et de la configuration.

* Le module `all` est un module de conteneur qui contient les sous-modules `ui.apps` et `ui.content`.

>[!NOTE]
>La structure de projet est basée sur *Archetype 24* pour les modules et leurs `pom.xml/filter.xml files`. Pour plus d’informations, consultez [Archetype 24](https://github.com/adobe/aem-project-archetype).

## Utilisation de Repository Modernizer {#using-repo-modernizer}

* Par l’intermédiaire de la ligne de commande d’Adobe I/O : Il est recommandé d’utiliser Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (module externe de refactorisation de code AEM as a Cloud Service pour la ligne de commande d’Adobe I/O).

   Reportez-vous à **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser le module externe.

* En tant qu’utilitaire autonome : Repository Modernizer peut également être exécuté en tant qu’utilitaire autonome.

   Reportez-vous à **[Ressource Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** pour savoir comment utiliser cet outil.

   >[!NOTE]
   >
   >Repository Modernizer est développé à l’aide de NodeJS. Il est recommandé d’installer NodeJS 10.0+.
