---
title: Surveillance des utilisateurs et utilisatrices en temps réel (RUM) pour AEM as a Cloud Service
description: Découvrez comment utiliser la surveillance de l’utilisation réelle (RUM) pour capturer et analyser l’expérience utilisateur numérique d’un site Web ou d’une application en temps réel.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 8ccef0103ae7fb75171431eeb36f7352f6467d56
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 0%

---

# Real Use Monitoring Service for AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Le service Real Use Monitoring, la collecte de données côté client, est un service automatisé. Aucune configuration client n’est requise.

>[!INFO]
>
>La surveillance côté client fonctionne uniquement pour les clients disposant de AEM Cloud Service version **2024.5.16461** et ultérieure.

## Vue d’ensemble {#overview}

Le service Real Use Monitoring (RUM) est une technologie de surveillance des performances qui capture et analyse les expériences utilisateur numériques d’un site Web ou d’une application en temps réel. Il offre une visibilité sur les performances en temps réel d’une application Web et fournit un aperçu plus approfondi de l’expérience de l’utilisateur final. Le service se concentre sur l’optimisation des performances en surveillant les engagements du site Web, plutôt que les utilisateurs eux-mêmes.

Avec RUM, les mesures de performance clés sont suivies dès le lancement de l’URL jusqu’à ce que la demande soit renvoyée au navigateur. Il aide les développeurs à améliorer l’application pour la rendre facile à utiliser pour les utilisateurs finaux.

>[!INFO]
>
>« Real User Monitoring » a été rebaptisé « Real Use Monitoring » car il reflète mieux la véritable essence du service.

## Qui peut bénéficier d’un service de supervision d’utilisation réelle ? {#who-can-benefit-from-rum-service}

Le service Real Use Monitoring est bénéfique pour tous les clients. Il offre un reflet représentatif des interactions des utilisateurs, assurant une mesure fiable de l’engagement du site Web en capturant le nombre de pages vues côté client.

Pour tous Adobe clients, ce service fournit des informations précieuses sur les interactions des utilisateurs. Les clients utilisant leur propre CDN peuvent bénéficier de rapports de trafic simplifiés, car Adobe intègre désormais directement la collecte de données, éliminant ainsi le besoin de rapports séparés pendant les cycles de renouvellement.

## Comprendre le fonctionnement du service de surveillance de l’utilisation réelle {#understand-how-the-rum-service-works}

Adobe Experience Manager (AEM) utilise la surveillance de l’utilisation réelle (RUM) pour aider les clients et les Adobe à comprendre comment les visiteurs interagissent avec AEM sites. Il les aide à diagnostiquer les problèmes de performances et à mesurer l’efficacité des expériences. RUM préserve la vie privée des visiteurs par échantillonnage - seule une petite partie de toutes les pages vues est surveillée - et aucune information personnellement identifiable (PII) n’est collectée.

## Service de surveillance de l’utilisation réelle et confidentialité {#rum-service-and-privacy}

Le service Real Use Monitoring de AEM est conçu pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie que le site que vous visitez ou mis à Adobe disposition ne recueille aucun renseignement personnel.

En tant qu’opérateur de site, aucun abonnement supplémentaire n’est requis pour activer la surveillance via cette fonctionnalité. Il n’existe pas de fenêtre contextuelle ou de formulaire de consentement supplémentaire que les utilisateurs finaux peuvent accepter pour activer RUM.

## Service de surveillance de l’utilisation réelle Échantillonnage des données {#rum-service-data-sampling}

Les solutions traditionnelles d’analyse Web tentent de collecter des données sur chaque visiteur. AEM service RUM ne capture les informations qu’à partir d’une petite fraction des pages vues. Le service est destiné à être échantillonné et anonymisé plutôt qu’à remplacer l’analyse. Par défaut, les pages ont un rapport d’échantillonnage de 1:100. Les exploitants de sites ne peuvent pas augmenter ou diminuer le taux d’échantillonnage pour le moment. Pour estimer le trafic total avec précision, pour 100 pages vues, les données sont collectées à partir de 1, ce qui vous donne une approximation fiable du trafic global.

En tant que décision de collecter ou non les données, elle est prise page vue par page vue, et il devient pratiquement impossible de suivre les interactions sur plusieurs pages. De par sa conception, RUM n’a pas de concept de visiteurs ou de sessions, seulement de pages vues.

## Quelles données sont collectées {#what-data-is-being-collected}

Le service Real Use Monitoring est conçu pour empêcher la collecte d’informations personnellement identifiables. L’ensemble des informations collectées par RUM est listé ci-dessous :

* Nom d’hôte du site visité, par exemple : `experienceleague.adobe.com`
* Type général d’agent utilisateur et système d’exploitation utilisés pour afficher la page, tels que : `desktop:windows` ou `mobile:ios`
* Moment de la collecte des données, par exemple : `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* L’URL de la page visitée, par exemple : `https://experienceleague.adobe.com/docs`
* L’URL de référence (l’URL de la page qui renvoie à la page actuelle, si l’utilisateur a suivi un lien)
* Identifiant de la page vue généré de façon aléatoire, dans un format similaire à : `2Ac6`
* Poids ou inverse de la fréquence d’échantillonnage, par exemple : `100`. Cela signifie que seulement une page vue sur cent est enregistrée
* Point de contrôle, ou nom, d’un événement particulier dans l’ordre de chargement de la page. Ou interagir avec lui en tant que visiteur
* Source ou identificateur de l’élément DOM avec lequel l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple, il peut s’agir d’une image
* La cible ou le lien vers une page ou une ressource externe avec laquelle l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple : `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Les mesures de performances CWV (Core Web Vitals), y compris la peinture contentieuse la plus volumineuse (LCP), le délai de première entrée (FID), le décalage cumulatif de la disposition (CLS) et le délai jusqu’au premier octet (TTFB) qui décrivent la qualité de l’expérience du visiteur.

## Comment fonctionne la surveillance de l’utilisation réelle pour un client {#how-rum-works-for-a-customer}

Real Use Monitoring surveille automatiquement le trafic côté client pour vous fournir des informations précieuses. En tant que client Adobe, vous n’avez pas besoin de prendre de mesures supplémentaires, car ce service est parfaitement intégré à votre configuration existante. Avec le déploiement de la disponibilité générale (GA), vous bénéficiez automatiquement de cette nouvelle fonctionnalité.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Comment les données du service de surveillance de l’utilisation réelle sont-elles utilisées {#how-rum-service-data-is-being-used}

Les données RUM sont utiles aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement des performances des sites clients
* Pour rationaliser la recherche automatisée du trafic incluant les pages vues.
* Pour comprendre comment AEM interagit avec d’autres scripts (tels que l’analyse, le ciblage ou les bibliothèques externes) sur la même page, afin d’augmenter la compatibilité.

## Limites et compréhension de l’écart des mesures de pages vues et de performances {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Lorsque vous analysez les données RUM, il peut y avoir des variations dans les pages vues et d’autres mesures de performance. Ces écarts peuvent être attribués à plusieurs facteurs inhérents à la surveillance en temps réel côté client. Voici les principales considérations que les clients doivent garder à l’esprit lors de l’interprétation de leurs données RUM :

1. **Bloqueurs de trackers**

   * Les utilisateurs finaux utilisant des bloqueurs de trackers ou des extensions de confidentialité peuvent entraver la collecte de données RUM, car ces outils limitent l’exécution des scripts de suivi. Cette restriction peut entraîner une sous-déclaration des pages vues et des interactions avec les utilisateurs, créant un écart entre l’activité réelle du site et les données capturées par RUM.

1. **Restrictions liées à la capture d’appels API/JSON sans tête**

   * Le service de données RUM se concentre sur l’expérience côté client et ne capture pas l’API backend ou les appels JSON effectués à partir d’une application sans tête non AEM pour le moment. L’exclusion de ces appels des données du service RUM crée des écarts par rapport aux demandes de contenu mesurées par les Analytics CDN.

## Questions fréquentes {#faq}


1. **Les clients peuvent-ils intégrer les scripts de service RUM à des systèmes tiers tels que Dynatrace ?**

   Oui.

1. **Les mesures vitales Web « Interaction avec la peinture suivante », « Temps jusqu’au premier octet » et « Première peinture litigieuse » sont-elles collectées ?**

   L’interaction avec la peinture suivante (INP) et le temps jusqu’au premier octet (TTFB) sont collectés.  La première peinture contente n’est pas collectée pour le moment.

1. **Le `/.rum` chemin est bloqué sur mon site, comment dois-je le corriger ?**

   Le `/.rum` chemin d’accès est requis pour que la collecte RUM fonctionne. Si vous disposez d’un CDN devant ce que Adobe fournit dans le cadre de AEM en tant que Cloud Service, assurez-vous que le chemin d’accès `/.rum` mène à la même origine AEM que le reste de votre contenu AEM. Et assurez-vous qu’il n’est pas ajusté de quelque façon que ce soit.

1. **La collecte de RUM est-elle prise en compte dans les demandes de contenu à des fins contractuelles ?**

   La bibliothèque RUM et la collection RUM ne comptent pas comme des demandes de contenu et n’augmentent pas le nombre de pages vues ou d’appels d’API signalés. En outre, pour les clients qui utilisent le CDN prêt à l’emploi avec AEM comme Cloud Service, [la collection](#serverside-collection) côté serveur est la base des demandes de contenu.

1. **Comment puis-je me désinscrire ?**

   Adobe recommande d’utiliser le Real Use Monitoring (RUM) en raison de ses avantages importants et qu’il peut vous permettre d’optimiser vos expériences numériques. Il peut offrir des informations précieuses qui peuvent aider à améliorer les performances du site Web. Le service est conçu pour être transparent et n’a aucun impact sur les performances de votre site Web.

   S’exclure signifie passer à côté de ces informations. Toutefois, si vous rencontrez des problèmes, contactez Adobe assistance.
