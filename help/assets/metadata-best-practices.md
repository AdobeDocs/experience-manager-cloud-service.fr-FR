---
title: Gestion des métadonnées et bonnes pratiques
description: Découvrez les bonnes pratiques en matière de métadonnées pour gérer efficacement vos ressources numériques.
role: User, Admin
exl-id: d90519df-55a6-4e23-81ad-ff2365d71c0d
feature: Metadata, Best Practices
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1399'
ht-degree: 1%

---

<!-- Keywords to focus on:
metadata best practices
aem metadata 
experience manager metadata-->

# Gestion des métadonnées et bonnes pratiques {#metadata-best-practices}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- |---------|----|-----|

Pour que votre entreprise se démarque et attire davantage de clients, l’utilisation de visuels de haute qualité tels que des images, des vidéos et d’autres ressources numériques est essentielle. Pour ce faire, vous avez besoin d’un processus qui vous permet d’ajouter des métadonnées à toutes les ressources numériques, ce qui facilite la recherche. Les métadonnées sont des données qui fournissent des détails essentiels sur les ressources numériques, notamment le nom, le type, l’emplacement de la ressource dans un référentiel, la date de modification et les balises associées. Les métadonnées simplifient la gestion des ressources, améliorent la recherche et l’accessibilité et assurent un contrôle efficace des versions.

Découvrez comment utiliser les métadonnées dans le système de gestion des ressources numériques (DAM) pour [gérer efficacement les métadonnées de vos ressources numériques](manage-metadata.md).

## Types de métadonnées

En fonction des différents aspects des données, les métadonnées sont catégorisées comme des métadonnées techniques, des métadonnées d’information et des métadonnées administratives.

### Métadonnées techniques

Les métadonnées techniques incluent les aspects techniques d’une ressource. Ce type de métadonnées est essentiel pour que les utilisateurs comprennent les caractéristiques inhérentes aux ressources numériques, ce qui facilite le traitement et l’utilisation efficaces.
Elle comprend des détails tels que :

* Taille du fichier
* Format
* Résolution
* Dimensions
* Mode colorimétrique

### Métadonnées d’information

Les métadonnées d’information englobent des informations descriptives qui améliorent la compréhension du contenu d’une ressource. Ces métadonnées sont essentielles pour la découverte de contenu, la recherche et la compréhension de la signification de la ressource. Les métadonnées d’information incluent les mots-clés, les légendes et les descriptions.

Par exemple, lors de la gestion d’une vidéo dans Experience Manager Assets, nous pouvons inclure les métadonnées d’information suivantes :

* **Mots-clés** : marketing, lancement de produit, promotion
* **Légende** : présentation de notre dernier produit avec des fonctionnalités intéressantes
* **Description** : présentation détaillée du contenu vidéo.

Les utilisateurs qui recherchent du contenu lié au marketing peuvent facilement trouver et comprendre la signification de la vidéo ci-dessus.

### Métadonnées administratives

Les métadonnées administratives traitent des aspects de gestion des ressources numériques. Il assure le contrôle d’accès, la conformité et la gestion du cycle de vie global des ressources dans le système de gestion des ressources numériques. Il comprend des informations relatives à :

* Propriété des ressources
* Droits d’utilisation
* Autorisations
* Autres détails administratifs

Les métadonnées administratives garantissent la gestion, le contrôle d’accès et la conformité corrects des ressources au sein du système de gestion des ressources numériques.

## Bonnes pratiques relatives aux métadonnées

### Définition de votre stratégie de métadonnées depuis le début

La gestion des métadonnées commence par la définition d’une stratégie de métadonnées qui fournit une base pour évaluer la valeur à long terme.

Il est essentiel de créer un schéma de métadonnées personnalisé en fonction de vos besoins lors de la planification de votre stratégie de métadonnées. Un schéma bien conçu fournit un cadre structuré pour catégoriser et organiser les ressources dans Experience Manager.

#### Vidéo : Ajout de champs personnalisés au schéma de métadonnées

>[!VIDEO](https://video.tv.adobe.com/v/3425977)

Votre stratégie de métadonnées peut inclure la définition des éléments suivants :

* **Objectifs :** décrire clairement les objectifs et les résultats attendus des métadonnées. Identifiez ce que vous souhaitez obtenir en ajoutant les métadonnées.

* **Objectif :** Définissez la raison pour laquelle vous capturez des métadonnées. Indiquez la valeur qu’il ajoute à vos processus, systèmes ou organisation.

* **Plan d’accessibilité :** Créez un plan pour rendre les métadonnées facilement accessibles et décevables. Expliquez qui l’utilisera, ainsi que les outils ou les méthodes à utiliser.

* **Propriétés des métadonnées :** identifiez et définissez soigneusement chaque propriété de métadonnées. Assurez-vous que chaque propriété a une raison claire d’être incluse, en se connectant aux objectifs et à l’objectif.

Pour garantir des résultats cohérents dans l’ensemble du référentiel, planifiez soigneusement la stratégie. En savoir plus sur les [schémas de métadonnées](metadata-schemas.md).

### Création d’un plan de gouvernance des métadonnées

La gouvernance des données permet de s’assurer que les efforts de gestion des métadonnées de l’entreprise sont alignés sur les objectifs généraux de l’entreprise.
La stratégie de gouvernance peut inclure :

* Définition des politiques et procédures relatives à la gestion des données et des métadonnées.
* Définition de normes de qualité et d’intégrité des données.
* Définition des rôles et des responsabilités dans la gestion des données.

Déterminez d’où proviennent les informations et examinez les détails de la stratégie de métadonnées, y compris les propriétés et leurs sources. Elle peut évoluer en fonction de la complexité de la stratégie. Dans les grandes entreprises, il y a un système de gestion des métadonnées maître qui supervise plusieurs systèmes dans la pile maître.

>[!NOTE]
>
>Découvrez comment [gérer les métadonnées de vos ressources numériques](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html).

### Respecter la stratégie de métadonnées

Une stratégie de métadonnées cohérente garantit une organisation et une récupération efficaces des ressources numériques. Adoptez une approche stratégique pour capturer et mettre en oeuvre les valeurs de métadonnées, ce qui vous permet d’optimiser l’évolution sans changements inutiles. <br>

Dans la gestion des métadonnées à l’échelle de l’entreprise, la cohérence est importante lors de l’attribution des noms et du référencement des ressources. Par exemple, lors de la gestion simultanée de plusieurs ressources, &quot;envisagez d’ajouter des métadonnées en bloc. <br>

Voici quelques-unes des bonnes pratiques à suivre :

* **Évitez les valeurs en double :** Si vous disposez d’une collection d’images provenant d’une campagne marketing, utilisez des noms cohérents et évitez les doublons.<br>
Par exemple, au lieu d&#39;utiliser des noms en double comme *campaign_image_001* et *campaign_image_002*, implémentez une convention d&#39;affectation de noms systématique telle que *event_promotion* et *product_launch*, en assurant une identification claire et ordonnée.

* **Utilisez efficacement les vocabulaires contrôlés :** Mettez en oeuvre des vocabulaires contrôlés en utilisant des termes normalisés pour les balises. Découvrez comment implémenter efficacement [AEM Tagging Framework](/help/implementing/developing/introduction/tagging-framework.md).  <br>
Par exemple, utilisez systématiquement des termes tels que *product_launch* ou *event_promotion* lorsque vous balisez des images avec des thèmes pour maintenir une séquence systématique.

* **Conserver l’exactitude et l’exhaustivité :** Pour maintenir la cohérence, l’exactitude, l’exhaustivité et l’alignement des métadonnées entre les différentes sources est essentielle.
Par exemple, lors de l’ajout de métadonnées à un document de PDF, vérifiez que les détails tels que les noms d’auteur et les mots-clés sont exacts et complets.

#### Vidéo : Ajout de métadonnées en bloc à des ressources

>[!VIDEO](https://video.tv.adobe.com/v/3425978)

### Évaluation et amélioration de la recherche de métadonnées

Évaluez votre stratégie de métadonnées pour améliorer la recherche de métadonnées. Simplifiez les workflows et améliorez les fonctionnalités de recherche pour une réutilisation efficace. Évitez de gérer des métadonnées qui n’ont pas un objectif clair.

Vous pouvez tenir compte des bonnes pratiques suivantes pour optimiser la recherche de métadonnées :

* **Optimisation des mots-clés :** améliorez la recherche de métadonnées en optimisant les mots-clés associés aux ressources. Vous pouvez améliorer la pertinence des mots-clés pour des ressources spécifiques dans [!UICONTROL Assets Manager] en procédant comme suit :

   1. Accédez à **[!UICONTROL Assets]** > **[!UICONTROL Fichier]** > **[!UICONTROL [Dossier de ressources]]**.
   1. Sélectionnez la ressource pour laquelle vous souhaitez mettre à jour les métadonnées, puis cliquez sur **[!UICONTROL Propriétés]**.
   1. Accédez à l’onglet **[!UICONTROL Avancé]**, puis cliquez sur **[!UICONTROL Ajouter]** sous l’onglet **[!UICONTROL Élever pour les mots-clés de recherche]**. <br>Vous devez utiliser le schéma de métadonnées par défaut pour élever les mots-clés de recherche.
   1. Saisissez le mot-clé pour lequel vous souhaitez augmenter la recherche, puis cliquez sur **[!UICONTROL Ajouter]**.<br>
Vous pouvez ajouter plusieurs mots-clés et les classer selon votre priorité.
   1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.
Recherchez la ressource à l’aide des mots-clés que vous avez ajoutés. La ressource apparaît parmi les principaux résultats de recherche.

  Découvrez comment [stimuler la recherche dans Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=fr).

* **Champs de métadonnées personnalisés :** personnalisez vos champs de métadonnées pour capturer des informations supplémentaires sur les ressources. Par exemple, ajoutez des champs spécifiques pour les détails du projet, les informations de copyright ou toute autre donnée pertinente qui améliore les fonctionnalités de recherche. Découvrez [comment modifier ou ajouter des métadonnées personnalisées](meta-edit.md) dans Experience Manager Assets.


* **Validation des métadonnées :** Mettez en oeuvre des contrôles de validation pour les entrées de métadonnées afin d’assurer la cohérence et la précision. L’utilisation de vocabulaires contrôlés rend le processus de validation plus fluide et réduit le risque d’entrées floues ou incohérentes. Cela peut impliquer de définir des instructions pour certaines propriétés de métadonnées afin d’éviter des informations ambiguës ou incohérentes.

* **Suivi de l’utilisation :** évaluez la pertinence et l’utilisation des différentes propriétés de métadonnées au fil du temps. Identifiez les métadonnées fréquemment utilisées et privilégiez-les, ou contribuez de manière significative aux processus de recherche et de récupération.

#### Vidéo : Ajout de mots-clés pour améliorer la recherche

>[!VIDEO](https://video.tv.adobe.com/v/3425979)

### Simplification et compréhension des métadonnées

Simplifiez les métadonnées pour une meilleure gouvernance et une meilleure adoption par les utilisateurs. Soyez clair et facile à comprendre, en encourageant les utilisateurs à ajouter des informations essentielles.
Pour simplifier les métadonnées, appliquez les bonnes pratiques suivantes :

* **Optimiser les options de propriété :** Concentrez-vous sur la mise en surbrillance des propriétés essentielles sans charger les utilisateurs avec trop de champs de métadonnées à remplir. Par exemple, lors de l’ajout de métadonnées pour une image, incluez uniquement des champs clés tels que le titre, la description et les balises pour une catégorisation efficace.

* **Éliminez les propriétés par défaut inutiles :** simplifiez le formulaire de métadonnées en éliminant les propriétés par défaut prêtes à l’emploi qui ne sont pas pertinentes pour votre cas d’utilisation. Supprimez les propriétés par défaut rarement utilisées pour une interface et une expérience plus propres.

* **Révision et mise à jour périodiques des métadonnées :** Mettez régulièrement à jour les métadonnées et vous adaptez aux besoins et aux technologies changeants afin de vous assurer que les utilisateurs fournissent des informations précieuses au fil du temps.

### Analyse du parcours de contenu

Examinez la chaîne d’approvisionnement du contenu pour rechercher des sources de métadonnées et impliquer toutes les parties prenantes, à partir du haut, afin d’obtenir une approche des bonnes pratiques approfondie. Impliquez différents membres du personnel pour assurer un soutien complet à l’échelle de l’entreprise. <br> Incorporez des métadonnées à différentes étapes pour partager la responsabilité de fournir des détails de ressources lors du chargement. Par exemple, l’intégration de [!DNL Experience Manager Assets] et [!DNL Workfront] offre des avantages substantiels en termes de gestion des métadonnées, ce qui améliore l’efficacité et la collaboration dans la création et la gestion de contenu. Cette intégration assure une synchronisation efficace des métadonnées pour les ressources liées, en mettant automatiquement à jour les détails du projet lorsque des modifications sont effectuées dans [!DNL Workfront].

Communiquer rapidement les objectifs, les progrès, les jalons et les défis pour recevoir la contribution et la coopération de toutes les parties prenantes. Encourager la collaboration à travers l’organisation pour créer des processus efficaces et des métadonnées précieuses.

En savoir plus sur les [métadonnées et les concepts associés](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-concepts.html) pour gérer efficacement les métadonnées Experience Manager.
