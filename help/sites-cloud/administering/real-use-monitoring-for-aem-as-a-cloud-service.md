---
title: Surveillance des utilisateurs et utilisatrices en temps réel (RUM) pour AEM as a Cloud Service
description: Découvrez comment utiliser la surveillance de l’utilisation réelle (RUM) pour capturer et analyser en temps réel l’expérience utilisateur numérique d’un site web ou d’une application.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 2515bc51fd54b014ffb701a8aef38cd08d6725b3
workflow-type: tm+mt
source-wordcount: '1274'
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

Le service RUM (Real Use Monitoring) est une technologie de surveillance des performances qui capture et analyse en temps réel les expériences utilisateur numériques d’un site web ou d’une application. Il offre une visibilité sur les performances en temps réel d’une application web et fournit des informations plus approfondies sur l’expérience de l’utilisateur final. Le service se concentre sur l’optimisation des performances en surveillant les engagements des sites web, plutôt que sur les utilisateurs eux-mêmes.

Avec RUM, les mesures de performances clés sont suivies dès le lancement de l’URL jusqu’à ce que la demande soit renvoyée au navigateur. Il aide les développeurs à améliorer l’application afin qu’elle soit facile à utiliser pour les utilisateurs finaux.

>[!INFO]
>
>&quot;Surveillance des utilisateurs réels&quot; a été renommé &quot;Surveillance de l’utilisation réelle&quot;, car elle reflète mieux l’essence réelle du service.

## Qui peut bénéficier d’un service de surveillance à usage réel ? {#who-can-benefit-from-rum-service}

AEM a développé RUM pour aider les clients et les Adobes à comprendre comment les visiteurs interagissent avec AEM sites. Le RUM peut être utilisé pour aider à diagnostiquer les problèmes de performance et mesurer l’efficacité des expériences. RUM protège la confidentialité des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues est surveillée) et aucune information d’identification personnelle n’est collectée.


## Comprendre le fonctionnement du service de surveillance d’utilisation réelle {#understand-how-the-rum-service-works}

AEM utilise RUM pour aider les clients et les Adobes à comprendre comment les visiteurs interagissent avec AEM sites. Cela les aide à diagnostiquer les problèmes de performance et à mesurer l’efficacité des expériences. RUM protège la confidentialité des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues est surveillée) et aucune information d’identification personnelle n’est collectée.

## Service de surveillance de l’utilisation réelle et confidentialité {#rum-service-and-privacy}

Le service de surveillance de l’utilisation réelle dans AEM est conçu pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie que le site que vous visitez ou que vous rendez disponible pour l’Adobe ne collecte aucune information personnelle.

En tant qu’opérateur de site, aucune inscription supplémentaire n’est requise pour activer la surveillance par le biais de cette fonctionnalité. Il n’existe pas de fenêtre contextuelle ni de formulaire de consentement supplémentaire que les utilisateurs finaux peuvent accepter pour activer RUM.

## Tirage des données du service de surveillance de l’utilisation réelle {#rum-service-data-sampling}

Les solutions d’analyse web traditionnelles tentent de collecter des données sur chaque visiteur. AEM service RUM  capture uniquement les informations provenant d’une petite fraction de pages vues. Le service est censé être échantillonné et rendu anonyme plutôt qu’un remplacement pour les analyses. Par défaut, le ratio d’échantillonnage des pages est de 1:100. Pour l’instant, les opérateurs du site ne peuvent ni augmenter ni diminuer le taux d’échantillonnage. Pour estimer précisément le trafic total, pour chaque 100 pages vues, les données sont collectées à partir de 1, ce qui vous donne une approximation fiable du trafic global.

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

La surveillance de l’utilisation réelle surveille automatiquement le trafic côté client pour vous fournir des informations précieuses. En tant que client Adobe, vous n’avez pas besoin d’effectuer d’autres étapes, car ce service est parfaitement intégré à votre configuration existante. Grâce au déploiement de la disponibilité générale (GA), vous bénéficiez automatiquement de cette nouvelle fonctionnalité.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Utilisation des données Real Use Monitoring Service {#how-rum-service-data-is-being-used}

Les données RUM sont bénéfiques aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement en termes de performances pour les sites clients
* Pour rationaliser la recherche automatisée de trafic qui inclut les pages vues.
* Pour mieux comprendre comment AEM interagit avec d’autres scripts (tels que les analyses, le ciblage ou les bibliothèques externes) sur la même page, afin d’améliorer la compatibilité.

## Limites et compréhension des écarts dans les pages vues et les mesures de performances {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Lorsque vous analysez les données RUM, il peut y avoir des écarts dans les pages vues et d’autres mesures de performances. Ces écarts peuvent être attribués à plusieurs facteurs inhérents à la surveillance en temps réel côté client. Voici les points essentiels à prendre en compte par les clients lors de l’interprétation de leurs données RUM :

1. **Tracker blockers**

   * Les utilisateurs finaux qui utilisent des bloqueurs de suivi ou des extensions de confidentialité peuvent empêcher la collecte de données RUM, car ces outils limitent l’exécution des scripts de suivi. Cette restriction peut entraîner des pages vues et des interactions utilisateur sous-estimées, ce qui crée une incohérence entre l’activité réelle du site et les données capturées par RUM.

1. **Limites de la capture d’appels API/JSON sans interface**

   * Le service de données RUM se concentre sur l’expérience côté client et ne capture pas pour l’instant les appels d’API principal ou JSON effectués à partir d’une application sans interface AEM. L’exclusion de ces appels des données de service RUM crée des écarts par rapport aux demandes de contenu mesurées par CDN Analytics.

## Questions fréquentes {#faq}


1. **Les clients peuvent-ils intégrer les scripts de service RUM à des systèmes tiers tels que Dynatrace ?**

   Oui.

1. **Les mesures de vitales Web collectées sont-elles &quot;Interaction vers la prochaine peinture&quot;, &quot;Temps jusqu’au premier octet&quot; et &quot;Première peinture contentée&quot; ?**

   L’interaction avec la peinture suivante (INP) et le temps jusqu’au premier octet (TTF) sont collectés.  La première peinture contentée n’est pas collectée pour le moment.

1. **Le chemin d’accès `/.rum` est bloqué sur mon site. Comment dois-je le corriger ?**

   Le chemin d’accès `/.rum` est requis pour que la collection RUM fonctionne. Si vous utilisez un réseau de diffusion de contenu devant AEM as a Cloud Service de l’Adobe, assurez-vous que le chemin d’accès `/.rum` vers la même origine AEM que votre autre contenu AEM. Assurez-vous également qu’il n’est pas ajusté.

1. **La collection RUM est-elle comptabilisée dans les demandes de contenu à des fins contractuelles ?**

   La bibliothèque RUM et la collection RUM ne sont pas comptabilisées comme des requêtes de contenu et n’augmentent pas le nombre de pages vues signalé ou d’appels API. De plus, pour les clients qui utilisent un réseau de diffusion de contenu prêt à l’emploi avec AEM as a Cloud Service, la [collection côté serveur](#serverside-collection) est la base des demandes de contenu.

1. **Comment puis-je me désinscrire ?**

   Adobe recommande d’utiliser la surveillance de l’utilisation réelle (RUM) en raison de ses avantages significatifs et de sa capacité à optimiser vos expériences numériques. Il peut offrir des informations précieuses qui peuvent améliorer les performances du site web. Le service est conçu pour être transparent et n’a aucun impact sur les performances de votre site web.

   S’exclure signifie manquer ces informations. Toutefois, si vous rencontrez des problèmes, contactez l’assistance Adobe.
