---
title: Repository Modernizer
description: Découvrez comment restructurer les packages de projets existants et les rendre compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
feature: Migration
role: Admin
source-git-commit: 6920651420da9b427510518b7add0637479adef5
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 82%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer est un utilitaire conçu pour restructurer les packages de projets existants en séparant le contenu et le code en packages discrets compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Maven Adobe Experience Manager soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du **contenu** et du **code** en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Pour plus d’informations sur la nouvelle structure de projet AEM pour Cloud Service, reportez-vous à [Structure de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=fr).

Repository Modernizer crée une structure de projet AEM Cloud Service compatible en créant la structure de déploiement suivante :

* Le package `ui.apps` se déploie sur `/apps` et contient l’intégralité du code.

* Le package `ui.content` se déploie sur des zones pouvant être écrites à l’exécution (par exemple, `/content`, `/conf`, `/home` ou toute zone autre que `/apps`) et contient l’ensemble du contenu et de la configuration.

* Le package `all` est un package de conteneur qui contient les sous-packages `ui.apps` et `ui.content`.

>[!NOTE]
>
>La structure de projet est basée sur *Archetype 24* pour les packages et leurs `pom.xml/filter.xml files`. Pour plus d’informations, voir [Archetype 24](https://github.com/adobe/aem-project-archetype).

## Utilisation de Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Par le biais de l’interface de ligne de commande Adobe I/O : Adobe recommande d’utiliser Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (plug-in de refactorisation du code AEM as a Cloud Service pour l’interface de ligne de commande Adobe I/O).

  Consultez **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour apprendre à installer et à utiliser le plug-in.

* En tant qu’utilitaire autonome : Repository Modernizer peut également être exécuté en tant qu’utilitaire autonome.

  Voir **[Ressource Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** pour apprendre à utiliser cet outil.

  >[!NOTE]
  >
  >Repository Modernizer est développé à l’aide de NodeJS. Il est recommandé de disposer de NodeJS 10.0+.
