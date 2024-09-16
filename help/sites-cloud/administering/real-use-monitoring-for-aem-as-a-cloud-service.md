---
title: Surveillance des utilisateurs et utilisatrices en temps réel (RUM) pour AEM as a Cloud Service
description: Découvrez la surveillance de l’utilisation réelle (RUM) , un service automatisé qui permet de surveiller la collecte de données côté client.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: ed52bac52618e23b9bcbe7c6767501c6711aff00
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 1%

---

# Service de surveillance d’utilisation réelle pour AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Le service de surveillance de l’utilisation réelle, la collecte de données côté client, est un service automatisé. Aucune configuration de client n’est requise.

>[!INFO]
>
>La surveillance côté client ne fonctionne que pour les clients ayant AEM version de Cloud Service (Adobe Experience Manager) **2024.5.16461** et supérieure.

## Vue d’ensemble {#overview}

Le service de surveillance de l’utilisation réelle (RUM) est une technologie de surveillance des performances qui contrôle le trafic côté client sur un site web ou une application en temps réel. Ce service se concentre sur la collecte de mesures et de données essentielles à l’optimisation des performances en surveillant les engagements des sites web, plutôt que sur les utilisateurs eux-mêmes. Avec RUM, les mesures de performances clés sont suivies dès le lancement de l’URL jusqu’à ce que la demande soit renvoyée au navigateur.

## Qui peut bénéficier d’un service de surveillance à usage réel ? {#who-can-benefit-from-rum-service}

AEM a développé la surveillance de l’utilisation réelle pour aider les clients et les Adobes à comprendre comment les utilisateurs finaux interagissent avec AEM sites. La surveillance de l’utilisation réelle diagnostique les problèmes de performance et mesure l’efficacité des expériences. La surveillance de l’utilisation réelle préserve la confidentialité des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues est surveillée) et aucune information d’identification personnelle (PII) n’est collectée.

## Service de surveillance de l’utilisation réelle et confidentialité {#rum-service-and-privacy}

Le service de surveillance de l’utilisation réelle dans AEM préserve la confidentialité des visiteurs et minimise la collecte de données. En tant que visiteur, cela signifie que le site que vous visitez ou que vous rendez disponible pour l’Adobe ne collecte aucune information personnelle.

En tant qu’opérateur de site, aucune inscription supplémentaire n’est requise pour activer la surveillance par le biais de cette fonctionnalité. Il n’existe pas de fenêtre contextuelle ni de formulaire de consentement supplémentaire que les utilisateurs finaux peuvent accepter pour activer RUM.

## Tirage des données du service de surveillance de l’utilisation réelle {#rum-service-data-sampling}

Les solutions d’analyse web traditionnelles tentent de collecter des données sur chaque visiteur. AEM service de surveillance de l’utilisation réelle (RUM) ne capture que les informations provenant d’une petite fraction des pages vues. Le service est censé être échantillonné et rendu anonyme plutôt qu’un remplacement pour les analyses. Par défaut, le ratio d’échantillonnage des pages est de 1:100. Pour l’instant, les opérateurs du site ne peuvent ni augmenter ni diminuer le taux d’échantillonnage. Pour estimer précisément le trafic total, pour chaque 100 pages vues, les données sont collectées à partir de 1, ce qui vous donne une approximation fiable du trafic global.

Lorsque vous décidez si les données sont collectées, elles sont effectuées page vue par page vue et il devient pratiquement impossible de suivre les interactions sur plusieurs pages. Par conception, RUM n’a aucun concept de visiteurs ou de sessions, uniquement des pages vues.

## Quelles données sont collectées ? {#what-data-is-being-collected}

Le service de surveillance de l’utilisation réelle est conçu pour empêcher la collecte d’informations d’identification personnelle. L&#39;ensemble complet des informations collectées par RUM est répertorié ci-dessous :

* Nom d’hôte du site visité, par exemple : `experienceleague.adobe.com`
* Le type d’agent utilisateur large et le système d’exploitation utilisé pour afficher la page, par exemple : `desktop:windows` ou `mobile:ios`
* Heure de la collecte des données, par exemple : `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* URL de la page visitée, par exemple : `https://experienceleague.adobe.com/docs`
* URL du référent (URL de la page qui a lié à la page active, si l’utilisateur a suivi un lien)
* Un identifiant généré de manière aléatoire de la page vue, dans un format similaire à : `2Ac6`
* Poids ou inverse du taux d’échantillonnage, par exemple : `100`. Cela signifie que seulement une page vue sur cent est enregistrée.
* Point de contrôle, ou nom, d’un événement particulier dans la séquence de chargement de la page. Ou interagir avec lui en tant que visiteur
* Source, ou identifiant, de l’élément DOM avec lequel l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple, il peut s’agir d’une image.
* La cible, ou le lien vers une page ou une ressource externe avec laquelle l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple : `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Les mesures de performances des principales caractéristiques du web (CWV), notamment la plus grande peinture de contenu (LCP), le premier délai d’entrée (FID), le changement de mise en page cumulée (CLS) et le délai de premier octet (TTF) qui décrivent la qualité de l’expérience du visiteur.

## Fonctionnement de la surveillance des utilisations réelles pour un client {#how-rum-works-for-a-customer}

La surveillance de l’utilisation réelle surveille automatiquement le trafic côté client. En tant que client Adobe, vous n’avez pas besoin d’effectuer d’autres étapes, car ce service est parfaitement intégré à votre configuration existante. La surveillance de l’utilisation réelle (RUM) étant la disponibilité générale (GA) , vous bénéficiez automatiquement de cette nouvelle fonctionnalité. Le service de surveillance de l’utilisation réelle n’expose aucune mesure aujourd’hui via un outil de visualisation. Nous nous efforçons de vous fournir cette fonctionnalité dès que possible.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Utilisation de la surveillance de l’utilisation réelle par Adobe {#how-rum-data-is-being-used}

Les données de surveillance d’utilisation réelle sont utilisées aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement en termes de performances pour les sites clients
* Pour mieux comprendre comment AEM interagit avec d’autres scripts (tels que les analyses, le ciblage ou les bibliothèques externes) sur la même page, afin d’améliorer la compatibilité.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their RUM data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede RUM data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by RUM.

1. **Limitations in capturing headless API/JSON calls**

   * RUM data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from RUM service data creates variances from the content requests measured by CDN Analytics.
-->

## Questions fréquentes {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the RUM service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **Les mesures &quot;Interaction vers la prochaine peinture&quot;, &quot;Temps jusqu’au premier octet&quot; et &quot;Première peinture contentée&quot; sont-elles collectées ?**

   L’interaction avec la peinture suivante (INP) et le temps jusqu’au premier octet (TTF) sont collectés.  La première peinture contentée n’est pas collectée pour le moment.

1. **Le chemin d’accès `/.rum` est bloqué sur mon site. Comment dois-je le corriger ?**

   Le chemin d’accès `/.rum` est requis pour que la collection RUM fonctionne. Si vous utilisez un réseau de diffusion de contenu devant AEM as a Cloud Service de l’Adobe, assurez-vous que le chemin d’accès `/.rum` vers la même origine AEM que votre autre contenu AEM. Assurez-vous également qu’il n’est pas ajusté.

1. **La collection RUM est-elle comptabilisée dans les demandes de contenu à des fins contractuelles ?**

   La bibliothèque RUM et la collection RUM ne sont pas comptabilisées comme des requêtes de contenu et n’augmentent pas le nombre de pages vues signalé ou d’appels API. De plus, pour les clients qui utilisent un réseau de diffusion de contenu prêt à l’emploi avec AEM as a Cloud Service, la [collection côté serveur](#serverside-collection) est la base des demandes de contenu.

1. **Comment puis-je me désinscrire ?**

   Adobe recommande d’utiliser la surveillance de l’utilisation réelle (RUM) en raison de ses avantages significatifs et qu’elle permettra à l’Adobe de vous aider à optimiser vos expériences numériques en améliorant les performances du site web. Le service est conçu pour être transparent et n’a aucun impact sur les performances de votre site web.

   S’exclure peut signifier manquer une chance d’améliorer l’engagement du trafic sur votre site web. Toutefois, si vous rencontrez des problèmes, contactez l’assistance Adobe.
