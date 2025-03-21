---
title: Surveillance des utilisateurs et utilisatrices en temps réel (RUM) pour AEM as a Cloud Service
description: Découvrez Real Use Monitoring (RUM) , un service automatisé qui permet de surveiller la collecte de données côté client.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: e6a610c56b9ad7a684ea9f5ef72199d3bed28cc0
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---

# Service de surveillance d’utilisation réelle pour AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Le service de surveillance de l’utilisation réelle, la collecte de données côté client, est un service automatisé. Aucune configuration client n’est requise.

>[!INFO]
>
>La surveillance côté client ne fonctionne que pour les clients et clientes disposant de la version **2024.5.16461** et ultérieure d’AEM (Adobe Experience Manager) Cloud Service.

## Vue d’ensemble {#overview}

Le service RUM (Real Use Monitoring) est une technologie de surveillance des performances qui surveille en temps réel le trafic côté client sur un site web ou une application. Ce service se concentre sur la collecte de mesures et de données essentielles pour optimiser les performances en surveillant les engagements des sites web, plutôt que sur les utilisateurs eux-mêmes. Avec RUM, les mesures de performances clés sont suivies depuis le lancement de l’URL jusqu’à ce que la requête soit renvoyée au navigateur.

## Qui peut bénéficier d&#39;un service de surveillance de l&#39;utilisation réelle ? {#who-can-benefit-from-rum-service}

La surveillance de l’utilisation réelle permet aux clients et à Adobe de comprendre comment les utilisateurs finaux interagissent avec les sites AEM. La surveillance de l’utilisation réelle diagnostique les problèmes de performances et mesure l’efficacité des expériences. La surveillance de l’utilisation réelle préserve la confidentialité des visiteurs par le biais de l’échantillonnage (seule une petite partie de toutes les pages vues est surveillée) et aucune information d’identification personnelle n’est collectée.

## Service de surveillance de l&#39;utilisation réelle et confidentialité {#rum-service-and-privacy}

Le service de surveillance de l’utilisation réelle d’AEM préserve la confidentialité des visiteurs et réduit la collecte de données. En tant que visiteur, cela signifie que le site que vous visitez ou que vous mettez à la disposition d’Adobe ne collecte aucune information personnelle.

En tant qu’opérateur de site, aucun accord préalable supplémentaire n’est nécessaire pour activer la surveillance via cette fonctionnalité. Il n’existe aucun formulaire de consentement ou de pop-up supplémentaire que les utilisateurs finaux peuvent accepter pour activer RUM.

## Échantillonnage des données du service de surveillance d&#39;utilisation réelle {#rum-service-data-sampling}

Les solutions d’analyse web traditionnelles tentent de collecter des données sur chaque visiteur. Le service de surveillance d’utilisation réelle (RUM) d’AEM ne capture les informations qu’à partir d’une petite fraction des pages vues. Le service est destiné à être échantillonné et anonymisé plutôt qu’à remplacer les analyses. Par défaut, les pages ont un rapport d’échantillonnage de 1:100. Les exploitants de sites ne peuvent pas augmenter ou diminuer le taux d&#39;échantillonnage pour le moment. Pour estimer avec précision le trafic total, pour chaque centaine de pages vues, les données sont collectées à partir de 1, ce qui vous donne une approximation fiable du trafic global.

Lorsque vous décidez si les données sont collectées, elles le sont page par page vue. Il devient ainsi pratiquement impossible d’effectuer le suivi des interactions entre plusieurs pages. Par défaut, RUM ne connaît pas les visiteurs ni les sessions, seulement les pages vues.

## Quelles données sont collectées ? {#what-data-is-being-collected}

Le service de surveillance de l&#39;utilisation réelle est conçu pour empêcher la collecte d&#39;informations d&#39;identification personnelle. L’ensemble complet des informations collectées par RUM est répertorié ci-dessous :

* Nom d’hôte du site visité, par exemple : `experienceleague.adobe.com`
* Type d’agent utilisateur général et système d’exploitation utilisés pour afficher la page, par exemple : `desktop:windows` ou `mobile:ios`
* Heure à laquelle les données ont été collectées, par exemple : `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* URL de la page visitée ; par exemple : `https://experienceleague.adobe.com/docs`
* URL du référent (URL de la page qui a été liée à la page active, si l’utilisateur a suivi un lien)
* Identifiant de la page vue généré de manière aléatoire, dans un format similaire à : `2Ac6`
* Poids ou inverse du taux d’échantillonnage, tel que : `100`. Cela signifie que seule une page vue sur cent est enregistrée
* Point de contrôle ou nom d’un événement particulier dans la séquence de chargement de la page. Ou, en interagissant avec lui en tant que visiteur
* Source, ou identifiant, de l’élément DOM avec lequel l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple, il peut s’agir d’une image
* Cible ou lien vers une page ou une ressource externe avec laquelle l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple : `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Les mesures de performances [Core Web Vitals (CWV)](https://web.dev/articles/lcp) [Largest Contentful Paint (LCP)](https://web.dev/articles/lcp), [Interaction to Next Paint (INP)](https://web.dev/articles/inp) et [Cumulative Layout Shift (CLS)](https://web.dev/articles/cls) qui décrivent la qualité d’expérience du visiteur.

## Fonctionnement de la surveillance d’utilisation réelle pour un client {#how-rum-works-for-a-customer}

Real Use Monitoring surveille automatiquement le trafic côté client. En tant que client Adobe, vous n’avez pas besoin de prendre des mesures supplémentaires, car ce service est intégré de manière transparente à votre configuration existante. Le service de surveillance de l’utilisation réelle (RUM) étant généralement disponible , vous bénéficiez automatiquement de cette nouvelle fonctionnalité. Le service de surveillance d’utilisation réelle n’expose aucune mesure destinée aux clients aujourd’hui à surveiller. Nous nous efforçons de vous fournir cette fonctionnalité dès que possible.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Comment Adobe utilise la surveillance en utilisation réelle {#how-rum-data-is-being-used}

Les données de surveillance d’utilisation réelle sont utilisées aux fins suivantes :

* Pour identifier et corriger les goulots d’étranglement en termes de performances des sites clients
* comprendre comment AEM interagit avec d’autres scripts (tels que les bibliothèques d’analyse, de ciblage ou externes) sur la même page, afin d’accroître la compatibilité ;
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

1. **Les mesures « Interaction avec la peinture suivante », « Temps jusqu’au premier octet » et « Première peinture contentante » sont-elles collectées ?**

   L&#39;interaction avec la peinture suivante (INP) et le temps jusqu&#39;au premier octet (TTFB) sont collectés.  La première peinture contentante n&#39;est pas collectée pour le moment.

1. **Le chemin d’accès `/.rum` est bloqué sur mon site, comment dois-je le corriger ?**

   Le chemin d’accès `/.rum` est requis pour que la collecte RUM fonctionne. Si vous utilisez un réseau CDN en amont d’Adobe AEM as a Cloud Service, assurez-vous que le chemin d’accès au `/.rum` est transféré vers la même origine AEM que vos autres contenus AEM. Et assurez-vous qu’il n’est pas ajusté d’une manière ou d’une autre.

1. **La collecte RUM est-elle prise en compte dans les demandes de contenu à des fins contractuelles ?**

   La bibliothèque RUM et la collection RUM ne sont pas comptées comme des requêtes de contenu et n’augmentent pas le nombre signalé de pages vues ou d’appels d’API. En outre, pour les clients qui utilisent le réseau CDN prêt à l’emploi avec AEM as a Cloud Service, la [collecte côté serveur](#serverside-collection) est la base des demandes de contenu.

1. **Comment puis-je me désinscrire ?**

   Adobe recommande d’utiliser la surveillance de l’utilisation réelle (RUM) en raison de ses avantages significatifs et du fait qu’elle permettra à Adobe de vous aider à optimiser vos expériences digitales en améliorant les performances des sites web. Le service est conçu pour être transparent et n’a aucun impact sur les performances de votre site web.

   Se désinscrire peut signifier rater une chance d’améliorer l’engagement du trafic sur votre site web. Cependant, si vous rencontrez des problèmes, contactez l’assistance Adobe.