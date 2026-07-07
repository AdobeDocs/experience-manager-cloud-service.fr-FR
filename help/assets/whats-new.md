---
title: Nouveautés de Content Hub
description: Apprenez-en plus sur certaines des fonctionnalités de Content Hub récemment lancées.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 77a5c54c-bbc5-4dfb-9c3a-aa0620e836d0
source-git-commit: bcdfc9bb418ab405faa82c55820a6ec6062c2b17
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 56%

---

# Nouveautés de Content Hub {#whats-new-content-hub}

Content Hub est disponible dans le cadre d’Experience Manager Assets as a Cloud Service pour démocratiser l’accès au contenu de marque pour les organisations et leurs partenaires commerciaux. Il se concentre sur la distribution des ressources pour activation à grande échelle et la création de variantes de contenu adaptées à la marque afin d’améliorer l’agilité marketing.

La vidéo suivante présente les principales fonctionnalités de Content Hub :

>[!VIDEO](https://video.tv.adobe.com/v/3463712)

>[!IMPORTANT]
>
>[Assets Ultimate](/help/assets/assets-ultimate-overview.md) et Assets as a Cloud Service incluent 250 utilisateurs et utilisatrices limités pour Content Hub. [Assets Prime](/help/assets/assets-prime.md) inclut 50 utilisateurs et utilisatrices limités pour Content Hub.

## Date de publication {#release-date}

La date de publication de la version Content Hub (2026.05.0) est le 28 mai 2026 (la même que celle de la version AEM as a Cloud Service). La prochaine version des fonctionnalités (2026.06.0) est prévue pour le 25 juin 2026.

## Fonctionnalités de la version de mai 2026 {#may-2026-release-features}

**Recherche optimisée par l&#39;IA**

AEM Assets Content Hub comprend désormais Recherche optimisée par l&#39;IA, une fonctionnalité de recherche avancée qui permet de comprendre la signification et l’intention des requêtes des utilisateurs et utilisatrices au lieu de se fier uniquement à des correspondances exactes de mots-clés. Recherche optimisée par l&#39;IA fournit des résultats plus précis et pertinents en reconnaissant les relations entre les mots, les concepts et l’intention de l’utilisateur. Il prend en charge les requêtes multilingues, gère les fautes d’orthographe et les fautes de frappe, comprend les synonymes et affiche les ressources pertinentes même lorsque les utilisateurs n’utilisent pas les termes exacts des métadonnées.

Par exemple, une recherche de `Woman drinking coffee` peut également renvoyer des ressources balisées avec des termes associés, tels que `Lady`, `Girl`, `Latte` ou `Cappuccino`.

Les administrateurs peuvent activer ou désactiver Recherche optimisée par l&#39;IA dans Content Hub à l’aide du menu Configurations en sélectionnant Recherche optimisée par l&#39;IA ou la recherche traditionnelle par mot-clé.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/content-hub/search-assets-content-hub#ai-search-aem-assets-content-hub"}


**Options de tri personnalisé**

Content Hub permet désormais aux administrateurs d’activer les champs de métadonnées personnalisés en tant qu’options de tri sur la page d’accueil de Content Hub. Outre les options de tri par défaut, Taille, Modifié, Nom et Pertinence, les administrateurs peuvent configurer des champs de métadonnées spécifiques à l’entreprise tels que le canal, la région, le SKU ou la campagne pour aider les utilisateurs à organiser plus efficacement les résultats de la recherche.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/content-hub/search-assets-content-hub#configure-sorting-aem-assets-content-hub"}

**Prise en charge des événements de recherche et de téléchargement de ressources pour les API de diffusion**

Les API de diffusion AEM Assets prennent désormais en charge la recherche de ressources et les événements de téléchargement de ressources, ce qui permet aux entreprises de suivre et de répondre à la manière dont les ressources sont découvertes et utilisées dans les applications et expériences connectées. Ces événements permettent d’améliorer la visibilité sur les modèles d’utilisation des ressources, de prendre en charge les workflows d’analyse et de création de rapports et de simplifier les intégrations aux systèmes externes et les processus d’automatisation.

Grâce aux informations basées sur les événements, les équipes peuvent mieux comprendre l’engagement du contenu et créer des workflows de ressources numériques plus connectés. Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/asset_downloaded).

**URL de diffusion des ressources**

Content Hub permet désormais aux utilisateurs de copier l’URL de diffusion d’une ressource directement à partir des propriétés de la ressource. Cette amélioration facilite le partage et l’intégration de ressources approuvées sur des sites web, des applications et des systèmes externes. En fournissant un accès rapide aux liens prêts pour la diffusion, les équipes peuvent rationaliser les workflows de distribution de contenu et accélérer la réutilisation des ressources dans les expériences digitales.

>[!IMPORTANT]
>
>Ces fonctionnalités sont disponibles en tant que fonctionnalités à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.


## Fonctionnalités de la version de février 2026 {#february-2026-release-features}

**Gestion des autorisations dans Content Hub à l’aide de l’agent de gouvernance AEM**

Dans Content Hub, l’agent de gouvernance AEM s’assure que seules les bonnes personnes accèdent aux bonnes ressources au bon moment. En appliquant des contrôles granulaires basés sur les attributs et les droits d’utilisation, il protège le contenu sensible tout en permettant une collaboration sécurisée. Cela signifie des risques de conformité réduits, une intégrité de marque renforcée et des workflows plus rapides. Les équipes peuvent ainsi partager et réutiliser des ressources en toute confiance, sans se soucier des risques d’accès non autorisé ou d’utilisation abusive. Cet équilibre entre sécurité et flexibilité se traduit par une efficacité opérationnelle et une confiance accrues dans l’ensemble de l’organisation.

![Présentation de la gestion des autorisations](/help/ai-in-aem/agents/governance/assets/permission-management.png)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/ai-in-aem/agents/governance/overview#permission-and-digital-rights-management"}


## Fonctionnalités de la version d’octobre 2025 {#october-2025-release-features}

**Améliorations apportées à l’expérience de téléchargement Content Hub**

Content Hub prend désormais en charge le téléchargement de plusieurs rendus de ressources dans une hiérarchie aplatie, ce qui élimine la nécessité de parcourir plusieurs dossiers. Les préférences utilisateur pour le comportement de téléchargement sont désormais conservées pour une expérience cohérente entre les sessions. La nouvelle expérience de téléchargement de ressources simplifie la gestion des ressources et améliore l’efficacité en facilitant la localisation et l’organisation des fichiers téléchargés.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}

## Fonctionnalités de la version de septembre 2025 {#september-2025-release-features}

**Marquer les collections comme favoris**

Vous pouvez désormais marquer les collections en tant que Favoris dans Content Hub, ce qui facilite leur organisation et leur récupération. Une fois ajoutées, vos collections favorites sont facilement disponibles dans l’onglet **[!UICONTROL Favoris]** de la page d’accueil de Content Hub.

**Épingler des collections pour un accès rapide**

Les administrateurs et administratrices de Content Hub peuvent désormais épingler des collections dans Content Hub pour un accès rapide. Les collections épinglées sont affichées dans une section **[!UICONTROL épinglées]** dédiée sur la page d’accueil Collections, ce qui facilite la conservation des collections importantes à portée de main.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/content-hub/collections-content-hub#pin-unpin-collection"}

## Fonctionnalités de la version d’août 2025 {#august-release-features}

**Recherche en masse via les propriétés de filtre**

Content Hub permet désormais de découvrir plus rapidement les ressources dont vous avez besoin. Grâce à la nouvelle fonctionnalité de recherche en masse, vous pouvez saisir plusieurs valeurs pour n’importe quelle propriété de filtre, séparées par un délimiteur (par exemple, plusieurs ID de SKU), et récupérer instantanément toutes les ressources correspondantes à l’aide d’une seule recherche.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/search-assets-content-hub#bulk-search"}

## Fonctionnalités de la version de juillet 2025 {#july-2025-release-features}

**Amélioration de la flexibilité du branding dans le hub de contenus**

En s’appuyant sur les fonctionnalités de personnalisation existantes, le hub de contenus permet désormais aux administrateurs et administratrices d’adapter davantage leur déploiement en ajoutant des images de logo personnalisées. La prise en charge du format de fichier TIFF a également été ajoutée pour les images de bannière et de logo, ce qui permet une plus grande flexibilité de conception.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/configure-content-hub-ui-options#configure-branding-content-hub"}

**Partage plus intelligent avec des liens portant des titres**

Vous pouvez désormais ajouter un titre lorsque vous générez un lien partagé, que ce soit à partir de la vue des détails de la ressource ou après avoir sélectionné une ou plusieurs ressources. Cela permet aux personnes destinataires d’identifier facilement la finalité de chaque lien, en particulier lorsqu’elles reçoivent plusieurs ressources partagées.

![lien privé et public](/help/assets/assets/shared-link-for-assets.png)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/share-assets-content-hub"}

**Amélioration de la navigation dans les filtres**

Le hub de contenus comprend désormais une option **Tout afficher** dans les filtres, ce qui permet d’afficher toutes les facettes disponibles ainsi que le nombre de ressources, en partant de la limite actuelle de dix facettes maximum. L’amélioration des fonctionnalités de recherche et de tri au sein de chaque filtre facilite la découverte et la gestion plus efficaces des ressources.

## Fonctionnalités de la version de juin 2025 {#june-2025-release-features}

### Gouvernance des collections {#collections-governance}

Content Hub permet désormais de contrôler l’accès aux collections lors de leur création, en veillant à ce que seuls les utilisateurs et utilisatrices autorisés puissent afficher ou gérer les ressources regroupées. Il garantit l’amélioration de la sécurité et de la collaboration, une gestion des ressources organisée et une gouvernance simplifiée.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/collections-content-hub#create-collections"}

## Fonctionnalités de la version de mai 2025 {#may-2025-release-features}

La version de mai de Content Hub comprend les fonctionnalités suivantes :

* [Contrôle d’accès basé sur les attributs](#attribute-based-access-control)

* [Image de marque de l’interface d’utilisation](#ui-branding)

* [Partage de lien public](#public-link-sharing)

* [Télécharger plusieurs ressources au format ZIP](#download-multiple-assets-as-zip)

* [Rendus Dynamic Media dans Content Hub](#dynamic-media-renditions)

### Contrôle d’accès basé sur les attributs (ABAC) {#attribute-based-access-control}

Content Hub permet désormais d’appliquer des restrictions basées sur des règles pour accéder aux ressources. Les autorisations de ressources assurent la gouvernance et garantissent que seules les ressources appropriées soient accessibles aux utilisateurs et utilisatrices.

Les règles de restriction des ressources sont basées sur des métadonnées. Si les conditions définies dans la règle correspondent aux métadonnées de la ressource, la ressource s’affiche pour les groupes d’utilisateurs et d’utilisatrices.

Voici quelques-uns des principaux avantages du contrôle d’accès basé sur les attributs :

* Élimine la dépendance à la structure de dossiers pour les autorisations

* Permet aux administrateurs et administratrices de charger des ressources et de déterminer rétroactivement les structures d’autorisation

* Réduit le nombre de doublons - améliore l’intégrité des ressources. Des doublons sont nécessaires dans les autorisations basées sur des dossiers lorsqu’une même ressource est partagée avec différents groupes.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/attribute-based-access-control"}

### Image de marque de l’interface d’utilisation {#ui-branding}

Content Hub permet désormais aux administrateurs et administratrices de personnaliser l’interface d’utilisation avec des éléments spécifiques à la marque, tels que des images de bannière, des titres de bannière et du corps de texte, ainsi que des couleurs primaires et secondaires. Ces améliorations permettent d’assurer la cohérence de la marque, de simplifier l’intégration des utilisateurs et utilisatrices et d’établir la confiance.

![Image de marque de l’UI](/help/assets/assets/content-hub-ui-branding.png)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/configure-content-hub-ui-options#configure-branding-content-hub"}

### Partage de lien public {#public-link-sharing}

Content Hub prend désormais en charge la génération de liens partageables pour permettre aux utilisateurs et utilisatrices externes, sans accès aux applications, d’afficher les métadonnées des ressources ou de télécharger des ressources.

![Image de marque de l’UI](/help/assets/assets/public-and-private-link.png)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/share-assets-content-hub"}

### Télécharger plusieurs ressources au format ZIP {#download-multiple-assets-as-zip}

Content Hub permet désormais de télécharger les ressources sélectionnées et leurs rendus dans un fichier ZIP et non plus dans des fichiers séparés, ce qui simplifie la gestion des fichiers.

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}

### Rendus Dynamic Media dans Content Hub {#dynamic-media-renditions}

Accédez à tous vos rendus prédéfinis et recadrages intelligents Dynamic Media pour le téléchargement, directement depuis l’interface d’utilisation de Content Hub.

![Rendus Dynamic Media](/help/assets/assets/dm-renditions-content-hub.png)

[!BADGE Examiner en détail cette fonctionnalité]{type=Informative url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

