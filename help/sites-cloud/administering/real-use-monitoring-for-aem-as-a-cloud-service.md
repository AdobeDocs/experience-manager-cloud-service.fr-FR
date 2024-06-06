---
title: Surveillance à usage réel pour AEM as a Cloud Service
description: Découvrez comment utiliser la surveillance de l’utilisation réelle (RUM) pour capturer et analyser en temps réel l’expérience utilisateur numérique d’un site web ou d’une application.
source-git-commit: 17a47bc440f971bcd220846ba31812fb1ee2f12e
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 0%

---


>[!NOTE]
>
>Nous sommes ravis d’annoncer la [Déploiement GA](/help/release-notes/release-notes-cloud/release-notes-current.md#real-use-monitoring) pour le service de surveillance de l’utilisation réelle, la collecte de données côté client. Il s’agit d’un service automatisé et aucune configuration client n’est requise.

# Service de surveillance à usage réel pour AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>La surveillance côté client fonctionne uniquement pour les clients avec la version d’AEM Cloud Service. **2024.5.16461** et au-dessus.

## Vue d’ensemble {#overview}

Le service de surveillance de l’utilisation réelle (RUM) est une technologie de surveillance des performances qui capture et analyse en temps réel les expériences utilisateur numériques d’un site web ou d’une application. Il offre une visibilité sur les performances en temps réel d’une application web et fournit des informations plus approfondies sur l’expérience de l’utilisateur final. La &quot;Surveillance des utilisateurs réels&quot; a été renommée &quot;Surveillance de l’utilisation réelle&quot;, car elle reflète mieux l’essence réelle du service, qui se concentre sur l’optimisation des performances par la surveillance des engagements du site web, plutôt que sur les utilisateurs eux-mêmes.

Grâce à RUM, les mesures de performances clés sont suivies dès le lancement de l’URL jusqu’à ce que la demande soit renvoyée au navigateur. Toutes ces mesures aident les développeurs à améliorer l’application afin qu’elle soit facile à utiliser pour les utilisateurs finaux.

## Qui Peut Bénéficier De Real Use Monitoring Service ? {#who-can-benefit-from-rum-service}

Le service de surveillance à usage réel est bénéfique pour tous les clients. Il offre un reflet représentatif des interactions des utilisateurs, ce qui garantit une mesure fiable de l’engagement du site web en capturant le nombre de pages vues côté client.

Pour tous les clients Adobe, ce service fournit des informations précieuses sur les interactions utilisateur. Les clients qui utilisent leur propre réseau de diffusion de contenu peuvent bénéficier de rapports de trafic simplifiés, car Adobe intègre désormais directement la collecte de données, rendant ainsi inutile la création de rapports distincts lors des cycles de renouvellement.

Souhaitez-vous déverrouiller tout le potentiel de votre site web en utilisant l’outil de visualisation de l’explorateur RUM des Adopteurs anticipés d’Adobe pour obtenir des informations utiles sur l’engagement de votre site web ? Cet outil peut fournir des informations sur les performances de votre page, y compris des mesures sur le nombre de clics, les taux de conversion des principales versions Web (CWV), les conversions et les cartes de parcours des clients. Grâce à ces informations puissantes, vous pouvez optimiser vos expériences numériques pour répondre plus efficacement aux besoins de vos utilisateurs. Si vous souhaitez en savoir plus et obtenir un accès, envoyez-nous un e-mail à l’adresse `rum-explorer@adobe.com`.

## Comprendre le fonctionnement du service de surveillance d’utilisation réelle {#understand-how-the-rum-service-works}

Adobe Experience Manager utilise la surveillance de l’utilisation réelle (RUM) pour aider les clients et les Adobes à comprendre comment les visiteurs interagissent avec les sites Adobe Experience Manager, à diagnostiquer les problèmes de performances et à mesurer l’efficacité des expériences. RUM protège la confidentialité des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues est surveillée) et aucune information d’identification personnelle n’est collectée.

## Service de surveillance et confidentialité en temps réel {#rum-service-and-privacy}

Le service de surveillance de l’utilisation réelle de Adobe Experience Manager est conçu pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie qu’aucune information personnelle n’est collectée par le site que vous visitez ou mise à la disposition de l’Adobe.

En tant qu’opérateur de site, aucune inscription supplémentaire n’est requise pour activer la surveillance par le biais de cette fonctionnalité. Il n’existe pas de fenêtre contextuelle ni de formulaire de consentement supplémentaire que les utilisateurs finaux peuvent accepter pour activer RUM.

## Échantillonnage des données du service de surveillance d’utilisation réelle {#rum-service-data-sampling}

Les solutions d’analyse web traditionnelles tentent de collecter des données sur chaque visiteur. Le service Adobe Experience Manager RUM capture uniquement les informations provenant d’une petite fraction de pages vues. Le service est censé être échantillonné et rendu anonyme plutôt qu’un remplacement pour les analyses. Par défaut, le ratio d’échantillonnage des pages est de 1:100. Pour l’instant, les opérateurs du site ne peuvent ni augmenter ni diminuer le taux d’échantillonnage. Pour estimer précisément le trafic total, pour chaque 100 pages vues, les données sont collectées à partir de 1, ce qui vous donne une approximation fiable du trafic global.

Comme la décision de collecter les données est prise sur une page vue par page, il devient pratiquement impossible de suivre les interactions sur plusieurs pages. Par conception, RUM n’a aucun concept de visiteurs ou de sessions, uniquement des pages vues.

## Données en cours de collecte {#what-data-is-being-collected}

Le service de surveillance de l’utilisation réelle est conçu pour empêcher la collecte d’informations d’identification personnelle. L’ensemble complet des informations pouvant être collectées par RUM est répertorié ci-dessous :

* Nom d’hôte du site visité, par exemple : `experienceleague.adobe.com`
* Le type d’agent utilisateur général et le système d’exploitation utilisé pour afficher la page, tels que : `desktop:windows` ou `mobile:ios`
* Heure de la collecte des données, par exemple : `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* URL de la page visitée, par exemple : `https://experienceleague.adobe.com/docs`
* URL du référent (URL de la page qui a lié à la page active, si l’utilisateur a suivi un lien)
* Identifiant généré de manière aléatoire de la page vue, dans un format similaire à : `2Ac6`
* Le poids ou l’inverse du taux d’échantillonnage, par exemple : `100`. Cela signifie que seulement une page vue sur cent est enregistrée
* Point de contrôle ou nom d’un événement particulier dans la séquence de chargement de la page ou d’interaction avec lui en tant que visiteur
* Source, ou identifiant de l’élément DOM avec lequel l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple, il peut s’agir d’une image.
* La cible, ou le lien vers une page ou une ressource externe avec laquelle l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple : `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Les mesures de performances des principales caractéristiques du web (CWV), notamment la plus grande peinture de contenu (LCP), le premier délai d’entrée (FID), le changement de mise en page cumulée (CLS) et le délai de premier octet (TTF) qui décrivent la qualité de l’expérience du visiteur.

## Fonctionnement de la surveillance des utilisations réelles pour un client {#how-rum-works-for-a-customer}

La surveillance de l’utilisation réelle surveille automatiquement le trafic côté client pour vous fournir des informations précieuses. En tant que client Adobe, vous n’avez pas besoin d’effectuer d’autres étapes, car ce service est parfaitement intégré à votre configuration existante. Avec le déploiement Disponibilité générale (GA) , vous bénéficierez automatiquement de cette nouvelle fonctionnalité.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Utilisation des données du service de surveillance d’utilisation réelle {#how-rum-service-data-is-being-used}

Les données RUM sont bénéfiques aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement en termes de performances pour les sites clients
* Pour simplifier la recherche automatisée de trafic qui inclut les pages vues.
* Pour comprendre comment Adobe Experience Manager interagit avec d’autres scripts (tels que les analyses, le ciblage ou les bibliothèques externes) sur la même page, afin d’améliorer la compatibilité.

## Limites et compréhension des différences dans les mesures de performances et les pages vues {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Lorsque vous analysez les données RUM, il peut y avoir des écarts dans les pages vues et d’autres mesures de performances. Ces écarts peuvent être attribués à plusieurs facteurs inhérents à la surveillance en temps réel côté client. Voici les points essentiels à prendre en compte par les clients lors de l’interprétation de leurs données RUM :

1. **Bloqueurs de dispositif de suivi**

   * Les utilisateurs finaux qui utilisent des bloqueurs de suivi ou des extensions de confidentialité peuvent empêcher la collecte de données RUM, car ces outils limitent l’exécution des scripts de suivi. Cette restriction peut entraîner des pages vues et des interactions utilisateur sous-estimées, ce qui crée une incohérence entre l’activité réelle du site et les données capturées par RUM.

1. **Limites de la capture d’appels API/JSON sans interface**

   * Le service de données RUM se concentre sur l’expérience côté client et ne capture pas pour l’instant les appels d’API principal ou JSON effectués à partir d’une application sans interface AEM. L’exclusion de ces appels des données du service RUM crée des écarts par rapport aux demandes de contenu mesurées par CDN Analytics.

## Questions fréquentes {#faq}


1. **Les clients pourront-ils intégrer les scripts de service RUM à des systèmes tiers tels que Dynatrace ?**

   Oui.

1. **Les mesures &quot;Interaction vers la prochaine peinture&quot;, &quot;Temps jusqu’au premier octet&quot; et &quot;Première peinture contentée&quot; des vitaux web sont-elles collectées ?**

   L’interaction avec la prochaine peinture (INP) et le temps jusqu’au premier octet (TTF) sont collectés.  La première peinture contentée n’est pas collectée pour le moment.

1. **La variable `/.rum` Le chemin est bloqué sur mon site. Comment dois-je le réparer ?**

   La variable `/.rum` Le chemin d’accès est requis pour que la collection RUM fonctionne.  Si vous disposez d’un réseau de diffusion de contenu devant ce que Adobe fournit dans le cadre d’AEM as a Cloud Service, vous devez vous assurer que la variable `/.rum` chemin d’accès transfère vers la même origine AEM que le reste de votre contenu AEM.

1. **La collecte RUM est-elle comptabilisée dans les demandes de contenu à des fins contractuelles ?**

   Ni la bibliothèque RUM, ni le nombre de collections RUM en tant que requêtes de contenu et n’augmentera pas le nombre de pages vues ou d’appels API signalé. En outre, pour les clients qui utilisent un réseau de diffusion de contenu prêt à l’emploi avec AEM as a Cloud Service, [collection côté serveur](#serverside-collection) est la base des demandes de contenu.

1. **Comment puis-je me désinscrire ?**

Nous vous recommandons vivement d’utiliser la surveillance de l’utilisation réelle (RUM) en raison de ses avantages significatifs et de sa capacité à optimiser vos expériences numériques. Il peut offrir des informations précieuses qui peuvent améliorer les performances du site web. Le service est conçu pour être transparent et n’a aucun impact sur les performances de votre site web.

S’exclure signifie ne pas tenir compte de ces informations. Toutefois, si vous rencontrez des problèmes, contactez l’assistance Adobe.
