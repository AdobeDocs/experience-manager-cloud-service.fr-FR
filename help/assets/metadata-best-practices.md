---
title: Gestion des métadonnées et bonnes pratiques
description: Découvrez les bonnes pratiques en matière de métadonnées pour gérer efficacement vos ressources numériques.
role: User, Admin
exl-id: d90519df-55a6-4e23-81ad-ff2365d71c0d
feature: Metadata, Best Practices
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 1%

---

<!-- Keywords to focus on:
metadata best practices
aem metadata 
experience manager metadata-->

# Gestion des métadonnées et bonnes pratiques {#metadata-best-practices}

Pour que votre entreprise se démarque et interagisse avec davantage de clients, il est essentiel d’utiliser des visuels de haute qualité tels que des images, des vidéos et d’autres ressources numériques. Pour ce faire, vous avez besoin d’un processus qui vous permet d’ajouter des métadonnées à toutes les ressources numériques, afin qu’elles puissent être facilement recherchées. Les métadonnées sont les données qui fournissent des informations essentielles sur les ressources numériques, notamment leur nom, leur type, leur emplacement dans un référentiel, leur date de modification et les balises associées. Les métadonnées rationalisent la gestion des ressources, améliorent la recherche et l’accessibilité, et assurent un contrôle efficace des versions.

Découvrez comment utiliser les métadonnées dans le système de gestion des ressources numériques (DAM) pour [gérer efficacement les métadonnées de vos ressources numériques](manage-metadata.md).

## Types de métadonnées

En fonction des différents aspects des données, les métadonnées sont classées en tant que métadonnées techniques, métadonnées d’information et métadonnées administratives.

### Métadonnées techniques

Les métadonnées techniques comprennent les aspects techniques d’une ressource. Ce type de métadonnées est essentiel pour que les utilisateurs comprennent les caractéristiques inhérentes aux ressources numériques, ce qui facilite leur traitement et leur utilisation efficaces.
Il comprend des détails tels que :

* Taille du fichier
* Format
* Résolution
* Dimensions
* Mode Couleur

### Métadonnées d’information

Les métadonnées d’information englobent des informations descriptives qui améliorent la compréhension du contenu d’une ressource. Ces métadonnées jouent un rôle essentiel dans la découverte, la capacité de recherche et la compréhension de l’importance de la ressource. Les métadonnées d’information incluent les mots-clés, les légendes et les descriptions.

Par exemple, lors de la gestion d’une vidéo dans Experience Manager Assets, nous pouvons inclure les métadonnées d’information suivantes :

* **Mots-clés** : marketing, lancement de produit, promotion
* **Légende** : Présentation de notre dernier produit aux fonctionnalités intéressantes
* **Description** : aperçu détaillé du contenu vidéo.

Les utilisateurs et utilisatrices qui recherchent du contenu lié au marketing peuvent facilement trouver et comprendre la signification de la vidéo ci-dessus.

### Métadonnées d’administration

Les métadonnées administratives traitent des aspects de gestion des ressources numériques. Il garantit le contrôle de l’accès, la conformité et la gestion du cycle de vie global des ressources dans le système de gestion des ressources numériques. Il contient des informations relatives aux éléments suivants :

* Propriété des actifs
* Droits d’utilisation
* Autorisations
* Autres détails administratifs

Les métadonnées administratives assurent la gestion correcte des ressources, le contrôle de l’accès et la conformité au sein du système de gestion des ressources numériques.

## Bonnes pratiques relatives aux métadonnées

### Définissez votre stratégie de métadonnées dès le début.

La gestion des métadonnées commence par la définition d’une stratégie de métadonnées qui fournit une base pour évaluer la valeur à long terme.

La création d’un schéma de métadonnées personnalisé en fonction de vos besoins est essentielle lors de la planification de votre stratégie de métadonnées. Un schéma bien conçu fournit un cadre structuré pour classer et organiser les ressources dans Experience Manager.

#### Vidéo : ajout de champs personnalisés au schéma de métadonnées

>[!VIDEO](https://video.tv.adobe.com/v/3425977)

Votre stratégie de métadonnées peut inclure la définition des éléments suivants :

* **Objectifs :** décrire clairement les objectifs et les résultats attendus des métadonnées. Identifiez l’objectif que vous souhaitez atteindre en ajoutant les métadonnées.

* **Objectif :** permet de définir pourquoi vous capturez des métadonnées. Spécifiez la valeur qu’il ajoute à vos processus, systèmes ou organisations.

* **Plan d’accessibilité :** créez un plan pour rendre les métadonnées facilement accessibles et détectables. Expliquez qui va l’utiliser et les outils ou méthodes à utiliser.

* **Propriétés des métadonnées :** identifiez et définissez soigneusement chaque propriété de métadonnées. Assurez-vous que chaque propriété a une raison claire d&#39;être incluse, en lien avec les objectifs et le but.

Pour garantir des résultats cohérents dans l’ensemble du référentiel, planifiez soigneusement la stratégie. En savoir plus sur les [schémas de métadonnées](metadata-schemas.md).

### Création d’un plan de gouvernance des métadonnées

La gouvernance des données garantit que les efforts de gestion des métadonnées de l’entreprise sont alignés sur les objectifs commerciaux globaux.
La stratégie de gouvernance peut comprendre les éléments suivants :

* Établissement de politiques et de procédures pour la gestion des données et des métadonnées.
* Définir des normes pour la qualité et l&#39;intégrité des données.
* Définir les rôles et les responsabilités dans la gestion des données.

Déterminez d’où proviennent les informations et examinez les détails de la stratégie de métadonnées, y compris les propriétés et leurs sources. Elle peut être adaptée en fonction de la complexité de la stratégie. Dans les grandes entreprises, il existe un système de gestion des métadonnées maître qui supervise plusieurs systèmes dans la pile maître.

>[!NOTE]
>
>Découvrez comment [gérer les métadonnées de vos ressources numériques](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html).

### Cohérence avec la stratégie de métadonnées

Une stratégie de métadonnées cohérente garantit une organisation et une récupération efficaces des ressources numériques. Adoptez une approche stratégique pour capturer et mettre en œuvre les valeurs des métadonnées, tout en offrant la flexibilité nécessaire pour permettre une évolution sans modifications inutiles. <br>

Dans la gestion des métadonnées à l’échelle de l’entreprise, la cohérence est importante lors du nommage et du référencement des ressources. Par exemple, lors de la gestion simultanée de plusieurs ressources, « pensez à ajouter des métadonnées en bloc. <br>

Voici quelques-unes des bonnes pratiques à suivre :

* **Éviter les valeurs en double :** si vous disposez d’une collection d’images d’une campagne marketing, utilisez des noms cohérents et évitez les doublons.<br>
Par exemple, au lieu d’utiliser des noms en double tels que *campaign_image_001* et *campaign_image_002*, implémentez une convention de nommage systématique telle que *event_promotion* et *product_launch*, pour garantir une identification claire et ordonnée.

* **Utiliser efficacement des vocabulaires contrôlés :** implémentez des vocabulaires contrôlés en utilisant des termes normalisés pour les balises. Découvrez comment implémenter le [framework de balisage AEM](/help/implementing/developing/introduction/tagging-framework.md) efficacement.  <br>
Par exemple, utilisez de manière cohérente des termes tels que *product_launch* ou *event_promotion* lors du balisage des images avec des thèmes afin de maintenir une séquence systématique.

* **Préserver la précision et l’exhaustivité :** pour garantir la cohérence, la précision, l’exhaustivité et l’alignement des métadonnées sur différentes sources sont essentiels.
Par exemple, lors de l’ajout de métadonnées à un document PDF, vérifiez que les détails tels que les noms de l’auteur et les mots-clés sont exacts et complets.

#### Vidéo : ajout de métadonnées en bloc aux ressources

>[!VIDEO](https://video.tv.adobe.com/v/3425978)

### Évaluation et amélioration de la capacité de recherche des métadonnées

Évaluez votre stratégie de métadonnées pour améliorer la capacité de recherche des métadonnées. Simplifiez les workflows et améliorez les fonctionnalités de recherche pour une réutilisation efficace. Évitez de traiter avec des métadonnées qui n’ont pas d’objectif clair.

Vous pouvez tenir compte des bonnes pratiques suivantes pour optimiser la recherche dans les métadonnées :

* **Optimisation des mots-clés :** améliorez la recherche de métadonnées en optimisant les mots-clés associés aux ressources. Vous pouvez améliorer la pertinence des mots-clés pour des ressources spécifiques dans [!UICONTROL Assets Manager] en procédant comme suit :

   1. Accédez à **[!UICONTROL Assets]** > **[!UICONTROL Fichier]** > **[!UICONTROL [Dossier de ressources]]**.
   1. Sélectionnez la ressource pour laquelle vous souhaitez mettre à jour les métadonnées, puis cliquez sur **[!UICONTROL Propriétés]**.
   1. Accédez à l’onglet **[!UICONTROL Avancé]**, puis cliquez sur **[!UICONTROL Ajouter]** sous l’onglet **[!UICONTROL Élever pour rechercher des mots-clés]**. <br>Vous devez utiliser le schéma de métadonnées par défaut pour élever les mots-clés de recherche.
   1. Saisissez le mot-clé pour lequel vous souhaitez améliorer la recherche, puis cliquez sur **[!UICONTROL Ajouter]**.<br>
Vous pouvez ajouter plusieurs mots-clés et les classer en fonction de votre priorité.
   1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.
Recherchez la ressource à l’aide des mots-clés que vous avez ajoutés. La ressource s’affiche parmi les principaux résultats de recherche.

  Découvrez comment [booster la recherche dans Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=fr).

* **Champs de métadonnées personnalisés :** personnalisez vos champs de métadonnées pour capturer des informations supplémentaires sur les ressources. Par exemple, ajoutez des champs spécifiques pour les détails du projet, des informations de copyright ou toute autre donnée pertinente qui améliore les fonctionnalités de recherche. Découvrez [ modifier ou ajouter des métadonnées personnalisées ](meta-edit.md) dans Experience Manager Assets.


* **Validation des métadonnées :** implémentez des contrôles de validation pour les entrées de métadonnées afin d’assurer la cohérence et la précision. L’utilisation de vocabulaires contrôlés rend le processus de validation plus fluide et réduit les risques d’entrées peu claires ou incohérentes. Cela peut impliquer de définir des instructions pour certaines propriétés de métadonnées afin d’éviter toute information ambiguë ou incohérente.

* **Suivi des utilisations :** évaluer la pertinence et l’utilisation de différentes propriétés de métadonnées au fil du temps. Identifiez et hiérarchisez les métadonnées fréquemment utilisées ou contribuez de manière significative aux processus de recherche et de récupération.

#### Vidéo : ajouter des mots-clés pour améliorer la recherche

>[!VIDEO](https://video.tv.adobe.com/v/3425979)

### Simplifier et comprendre les métadonnées

Simplifiez les métadonnées pour une meilleure gouvernance et une meilleure adoption par les utilisateurs. Soyez simple et facile à comprendre, en encourageant les utilisateurs à ajouter des informations essentielles.
Essayez les bonnes pratiques suivantes pour simplifier les métadonnées :

* **Optimiser les options de propriété** Concentrez-vous sur la mise en évidence des propriétés essentielles sans surcharger les utilisateurs avec trop de champs de métadonnées à remplir. Par exemple, lors de l’ajout de métadonnées pour une image, incluez uniquement les champs clés tels que le titre, la description et les balises pour une catégorisation efficace.

* **Éliminer les propriétés par défaut inutiles :** simplifiez le formulaire de métadonnées en éliminant les propriétés prêtes à l’emploi par défaut qui ne sont pas pertinentes pour votre cas d’utilisation. Supprimez les propriétés par défaut rarement utilisées pour une interface et une expérience plus épurées.

* **Vérifier et mettre à jour régulièrement les métadonnées** Mettez régulièrement à jour les métadonnées et adaptez-les à l’évolution des besoins et des technologies pour vous assurer que les utilisateurs fournissent des informations précieuses au fil du temps.

### Analyse du parcours de contenu

Examinez la chaîne d’approvisionnement du contenu pour trouver les sources de métadonnées et impliquez toutes les parties prenantes, en commençant par le sommet, pour une approche approfondie des bonnes pratiques. Faites appel à différents membres du personnel pour assurer un soutien complet à l’échelle de l’organisation. <br>Incorporez des métadonnées à différentes étapes pour partager la responsabilité de fournir les détails de la ressource lors du chargement. Par exemple, l’intégration de [!DNL Experience Manager Assets] et [!DNL Workfront] offre des avantages substantiels en termes de gestion des métadonnées, améliorant l’efficacité et la collaboration dans la création et la gestion de contenu. Cette intégration garantit une synchronisation efficace des métadonnées pour les ressources liées et met automatiquement à jour les détails du projet lorsque des modifications sont apportées dans [!DNL Workfront].

Communiquez rapidement les objectifs, les progrès, les jalons et les défis afin de recevoir les commentaires et la coopération de toutes les parties prenantes. Encouragez la collaboration à l’échelle de l’organisation pour créer des processus efficaces et des métadonnées précieuses.

En savoir plus sur [les métadonnées et les concepts associés](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-concepts.html) pour gérer efficacement les métadonnées Experience Manager.
