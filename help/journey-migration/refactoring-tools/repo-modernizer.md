---
title: Repository Modernizer
description: Repository Modernizer
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 62%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer est un utilitaire conçu pour restructurer les packages de projets existants en séparant le contenu et le code en packages discrets compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM requiert une séparation des **content** et **code** en sous-modules discrets afin de respecter la division entre contenu modifiable et non modifiable. Voir [AEM structure de projet](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=fr) pour plus d’informations sur la nouvelle structure de projet AEM pour Cloud Service.

Repository Modernizer crée une structure de projet AEM Cloud Service compatible en créant la structure de déploiement suivante :

* Le package `ui.apps` se déploie sur `/apps` et contient l’intégralité du code.

* Le package `ui.content` se déploie sur des zones pouvant être écrites à l’exécution (par exemple, `/content`, `/conf`, `/home` ou toute zone autre que `/apps`) et contient l’ensemble du contenu et de la configuration.

* `all` Le module est un module conteneur qui contient les sous-modules. `ui.apps` et `ui.content`.

>[!NOTE]
>La structure de projet est basée sur *Archetype 24* pour les packages et leurs `pom.xml/filter.xml files`. Voir [Archétype 24](https://github.com/adobe/aem-project-archetype) pour plus d’informations.

## Utilisation de Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Par Adobe I/O, l’interface de ligne de commande : Il est recommandé d’utiliser Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (AEM module externe de refactorisation du code as a Cloud Service pour l’interface de ligne de commande d’Adobe I/O).

  Voir **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** vous pouvez ainsi apprendre à installer et à utiliser le module externe.

* En tant qu’utilitaire autonome : Repository Modernizer peut également être exécuté en tant qu’utilitaire autonome.

  Voir **[Ressource Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** vous pouvez apprendre à utiliser cet outil.

  >[!NOTE]
  >
  >Repository Modernizer est développé à l’aide de NodeJS. Il est recommandé de disposer de NodeJS 10.0+.
