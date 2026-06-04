---
title: Présentation de l’agent de modernisation de l’expérience
description: Découvrez comment l’agent de modernisation de l’expérience intègre de nouveaux sites web dans Edge Delivery Services à l’aide de l’IA.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: c23a6f55-2ba8-4290-b7e8-06cad5de0fc8
source-git-commit: f2ab0a3d604ed4cd07ec8922ed331dfc37b45e5f
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 0%

---


# Présentation de l’agent de modernisation de l’expérience {#experience-modernization-agent}

Découvrez comment l’agent de modernisation de l’expérience intègre des sites web à Edge Delivery Services à l’aide de l’IA.

## Présentation {#introduction}

[Dans le cadre du Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) l’agent de modernisation d’Experience Manager accélère l’intégration à Edge Delivery Services en automatisant les migrations de sites web et la configuration des sites de base.

Il associe [compétences en création de site et migration](#creation-migration) pour l’intégration initiale du site web et [fonctionnalités de développement par bloc](#block-development) pour prendre en charge les workflows de création et de migration de site. En outre, il propose la [console de modernisation de l’expérience](#console) en tant qu’environnement de développement web assisté par l’IA, directement accessible. Bien que les utilisateurs puissent utiliser l’agent directement via cette console, les développeurs conservent un contrôle total sur les éléments livrés.

Pour les migrations complexes ou de haute priorité, Adobe propose le modèle de diffusion [&#x200B; Ingénieur de résultat agent (AOE) &#x200B;](#aoe-delivery) un service d’ingénierie conçu pour fournir des sites Edge Delivery prêts pour la production à l’aide de l’agent de modernisation de l’expérience.

## Avantages {#benefits}

L’agent de modernisation de l’expérience accélère le délai d’évaluation pour l’adoption de [&#128279;](/help/edge/overview.md) et vous permet d’adapter l’expérience web de votre marque.

* **Vitesse élevée** : l’automatisation de l’IA gère les travaux de migration répétitifs (importation de contenu, mappage de bloc, application du système de conception), en comprimant les délais de migration par rapport aux approches traditionnelles
* **Axé sur l’efficacité** : l’automatisation réduit le travail répétitif, ce qui permet aux équipes de se concentrer sur des travaux d’implémentation à plus forte valeur ajoutée
* **Accessible à tous** : les demandes en langage naturel rendent les modifications du site web accessibles aux utilisateurs et utilisatrices moins techniques, avec un aperçu en direct pour valider instantanément les modifications
* **Gouvernance d’entreprise** : les développeurs conservent une autorité totale sur ce qui est mis en ligne par le biais de workflows de révision intégrés à GitHub
* **Flexibilité post-migration** : permet aux équipes d’étendre et d’affiner les sites migrés à l’aide de modèles Edge Delivery Services

## Compétences en création et migration de site {#creation-migration}

L’agent de modernisation d’expérience offre des compétences pour créer de nouveaux sites Edge Delivery Services et migrer des sites web existants. Tout nouveau site Edge Delivery Services ou migration est encouragé à tirer parti de ces compétences.

* Accélère la création et la migration de sites web de plusieurs mois à plusieurs semaines ou jours, réduisant considérablement le délai d’évaluation pour l’adoption de Edge Delivery Services
* Prend en charge la migration d’un large éventail de plateformes CMS, d’AEM héritées ou de systèmes de conception (comme Figma) vers des projets Edge Delivery Services compatibles avec la production
* Prend en charge les bonnes pratiques en matière de performances, d’accessibilité et de conception réactive conformément aux conseils de Edge Delivery Services

Les compétences détaillées incluent la migration de pages, l’importation en bloc, l’extraction de conception, la configuration de la navigation et le Web scraping.

## Migrations basées sur des données et création de pages {#figma}

Outre les migrations de sites en direct, l’agent de modernisation d’Experience peut utiliser Figma comme source de conception. Pour utiliser ces fonctionnalités, configurez les détails de votre Figma dans [la console de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/console.md).

### Reconception De La Migration À L’Aide De Blocs Dérivés De Figma {#figma-redesign}

Lorsque vous migrez un site web existant vers une expérience repensée, l’agent [établit d’abord la collection de blocs repensée à partir des composants Figma](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md#figma-redesign-migration) puis exécute la migration du site par rapport au site web source actif et mappe le contenu source dans ces blocs dérivés de Figma.

* **Figma** est la source de conception et de bibliothèque de blocs cible.
* **Le site web en ligne** reste la source du contenu.
* Le contenu est validé par rapport au site web source ; la sortie visuelle est validée par rapport au système de conception dérivé de Figma.

### Créer une page à partir de Figma {#figma-new-page}

Lorsqu’une page n’existe pas déjà sur un site web source, l’agent [génère une nouvelle page Edge Delivery Services directement à partir d’un cadre ou d’une page Figma](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md#figma-new-page-from-figma) en mappant les sections Figma à des blocs existants, au contenu par défaut ou à de nouvelles variantes. Le texte et les ressources proviennent de Figma.

Pour plus d’informations sur ces workflows, la migration individuelle des blocs Figma et des conseils sur les invites, consultez le [Guide de l’invite de l’agent de modernisation de l’expérience.](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md)

## Bloquer les fonctionnalités de développement {#block-development}

L’agent de modernisation d’expérience tire parti des fonctionnalités générales de développement de Edge Delivery Services, qui permettent de réaliser diverses tâches de développement et offrent une valeur continue au-delà de la création ou de la migration initiale du site.

* Suit la méthodologie de développement piloté par le contenu (CDD) pour les modèles de contenu conviviaux pour la création
* Tire parti des [Collecte de blocs](https://www.aem.live/developer/block-collection) et [Partie de blocs](https://www.aem.live/developer/block-party/) pour trouver des implémentations de référence et des bonnes pratiques
* Prend en charge les workflows de test et de débogage pour valider les modifications avant le déploiement

Les fonctionnalités détaillées incluent le développement de blocs, la modélisation de contenu, la découverte de blocs de référence, les tests et le débogage.

## Console de modernisation de l’expérience {#console}

Experience Modernization Agent fournit un environnement de développement web assisté par l’IA pour Edge Delivery Services, exposé sous forme d’interface web à l’adresse [`aemcoder.adobe.io`.](https://aemcoder.adobe.io)

* La console ne nécessite aucune configuration locale pour que les utilisateurs et utilisatrices commencent à demander des modifications immédiatement en langage naturel.
* Effectuez rapidement des tâches de développement d’expérience quotidiennes tout en les prévisualisant via l’aperçu AEM en direct et synchronisez le contenu avec AEM.
* La console prend en charge la gouvernance d’entreprise par le biais de workflows de révision GitHub standard.

La console de modernisation de l’expérience en libre-service est généralement disponible. Les utilisateurs et utilisatrices intéressés peuvent demander l’accès pour garantir une expérience d’intégration fluide.

Commencez avec la console de modernisation de l’expérience !

* Si vous modernisez votre site en ciblant la création de documents, [commencez ici.](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md)
* Si vous modernisez votre site en ciblant la création AEM, [commencez ici.](/help/ai-in-aem/agents/brand-experience/modernization/getting-started-aem-authoring.md)

## Compétence en documentation de projet {#project-documentation}

Reconnaissant la nature fastidieuse des transferts de projet, [les compétences en documentation de projet](/help/ai-in-aem/agents/brand-experience/modernization/project-documentation.md) peuvent générer automatiquement une documentation complète une fois les travaux de création et de développement terminés.

## Compétence du catalogue de sites {#site-catalog}

La compétence de catalogue de sites permet d’explorer à un site web existant, de cataloguer tous les modèles de page et les variantes de bloc, de capturer des captures d’écran de chaque modèle et bloc et de générer un lot de rapports HTML interactifs à réviser. Cette compétence est précieuse pour :

* **Toute personne commençant un projet de migration** afin d’obtenir un inventaire complet des mises en page, des variantes de bloc, des paramètres régionaux et des pages par modèle avant d’écrire du code, afin que les équipes puissent planifier avec précision et faire apparaître la complexité au plus tôt
* **Les équipes qui effectuent des imports en bloc** pour identifier les pages partageant la même disposition, importez et perfectionnez manuellement les pages représentatives en premier, puis importez en bloc toutes les pages restantes pour ce modèle
* **Chefs de projet et parties prenantes** pour comprendre l’ampleur de l’effort

Consultez le document [Compétences en catalogue de sites](/help/ai-in-aem/agents/brand-experience/modernization/site-catalog.md) pour plus d’informations.

## Diffusion de l’ingénieur chargé des résultats (AOE) {#aoe-delivery}

Pour les migrations complexes ou les résultats accélérés, Adobe propose la diffusion Ingénieur de résultat agent (AOE). Il s’agit d’un service facultatif dans lequel les ingénieurs Adobe exploitent l’agent de modernisation d’Experience en votre nom, associant l’automatisation de l’IA à des conseils d’experts pour fournir des résultats prêts pour la production à grande échelle. Pour plus d’informations sur la diffusion AOE, consultez le document [Diffusion AOE de l’agent de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/aoe-delivery.md).

Si le modèle AOE vous intéresse pour votre prochaine migration :

* Contactez votre représentant Adobe ou l’équipe de votre compte pour lancer la définition de la portée et la planification.
* Adobe confirmera l’éligibilité, évaluera l’engagement et proposera un plan d’engagement.

## Limites {#limitations}

Les cas d’utilisation suivants nécessitent un effort d’implémentation supplémentaire en plus des compétences de l’agent de modernisation d’expérience.

La compétence de grattage ne prend pas en charge les sources suivantes.

* Sources intranet ou protégées telles que le contenu non accessible derrière une authentification, un VPN ou un pare-feu
   * Vous pouvez également utiliser [SLICC](https://www.sliccy.com) qui peut utiliser le contexte d’authentification de votre navigateur pour accéder aux sources protégées.
* Contenu dynamique complexe, tel qu’un contenu nécessitant une interaction utilisateur sophistiquée pour apparaître dans le DOM.
   * Le contenu rendu côté client est pris en charge si le contenu est accessible via une URL spécifique.
   * Les éléments masqués via CSS mais présents dans le DOM comme les onglets, les accordéons ou les carrousels sont également pris en charge.

L&#39;agent ne prend pas en charge les cibles suivantes.

* Environnements de publication AEM dans lesquels les sites utilisent la diffusion HTL
   * Les compétences ciblent Edge Delivery Services uniquement.
* Modèles de diffusion découplée tels que la diffusion basée sur une API uniquement ou une SPA (par exemple, Next.js)

Les exigences suivantes ne sont pas couvertes par des compétences d’automatisation dédiées et nécessitent un effort manuel.

* Perfection stricte des pixels
   * Seule la fidélité de conception pratique est automatisée
* Intégrations de données/services tiers côté serveur ou côté client
* Intégrations de la fonctionnalité de commerce ou de recherche
* Couche de données MarTech pour le ciblage/expérimentation
* Isolation des fragments de contenu/d’expérience
* Héritage multisite (MSM)
* Fonctionnalités personnalisées (par exemple, calculatrices, configurateurs)
* Logique commerciale personnalisée

## Étapes suivantes {#next-steps}

Commencez par migrer un site à l’aide du document [Prise en main de l’agent de modernisation d’Experience Platform](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md).
