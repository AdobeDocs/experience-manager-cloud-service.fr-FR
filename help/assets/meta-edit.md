---
title: Modification ou ajout de métadonnées
description: Découvrez les métadonnées des ressources dans [!DNL Experience Manager Assets] et les différentes façons de les modifier.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 64%

---

# Modification ou ajout de métadonnées {#how-to-edit-or-add-metadata}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les métadonnées sont des informations supplémentaires sur la ressource qui peuvent faire l’objet d’une recherche. Elles sont automatiquement extraites lorsque vous chargez une image. Vous pouvez modifier les métadonnées existantes ou ajouter de nouvelles propriétés de métadonnées à des champs existants (par exemple lorsqu’un champ de métadonnées est vide).

Comme les entreprises ont besoin de vocabulaires de métadonnées contrôlés et fiables, [!DNL Experience Manager Assets] ne permet pas l’ajout à la demande de nouvelles propriétés de métadonnées. Bien que les auteurs et autrices ne puissent pas ajouter de nouveaux champs de métadonnées pour les ressources, les développeurs et développeuses le peuvent. Voir [Création d’une propriété de métadonnées pour les ressources](meta-edit.md#editing-metadata-schema).

## Modification des métadonnées d’une ressource {#editing-metadata-for-an-asset}

Pour modifier les métadonnées :

1. Utilisez l’une des méthodes suivantes :

   * Dans l’interface utilisateur d’Assets, sélectionnez la ressource et sélectionnez l’icône **[!UICONTROL Afficher les propriétés]** dans la barre d’outils.
   * À partir de la miniature de la ressource, sélectionnez l’action rapide **[!UICONTROL Afficher les propriétés]**.
   * Sur la page de la ressource, sélectionnez **[!UICONTROL Afficher les propriétés]** dans la barre d’outils.

   La page Ressource affiche les métadonnées de la ressource. Ces métadonnées sont automatiquement extraites lorsqu’elles sont chargées (assimilées) dans Experience Manager Assets.

1. Apportez des modifications aux métadonnées sous les différents onglets, le cas échéant. Une fois l’opération terminée, sélectionnez **[!UICONTROL Enregistrer]** dans la barre d’outils pour enregistrer vos modifications. Sélectionnez **[!UICONTROL Fermer]** pour revenir à l’interface web d’Assets.

   >[!NOTE]
   >
   >Si un champ de texte est vide, cela signifie qu’aucune métadonnée n’a été définie. Vous pouvez saisir une valeur dans le champ et l’enregistrer pour ajouter cette propriété de métadonnées.

Toute modification apportée aux métadonnées d’une ressource est écrite dans les données XMP du binaire d’origine. Cette modification est apportée par le biais du workflow d’écriture différée des métadonnées d’Experience Manager. Les modifications apportées aux propriétés existantes (telles que `dc:title`) sont écrasées et les propriétés créées (y compris les propriétés personnalisées telles que `cq:tags`) sont ajoutées avec le schéma.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Modification d’un schéma de métadonnées {#editing-metadata-schema}

Pour en savoir plus sur la modification d’un schéma de métadonnées, consultez la section [Modification de formulaires de schéma de métadonnées](metadata-schemas.md#edit-metadata-schema-forms).

## Enregistrement d’un espace de noms personnalisé dans Experience Manager {#registering-a-custom-namespace-within-aem}

Vous pouvez ajouter vos propres espaces de noms à Experience Manager. Tout comme il existe des espaces de noms prédéfinis tels que cq, jcr et sling, vous pouvez disposer d’un espace de noms pour le traitement des données XML et des métadonnées de votre référentiel.

1. Accédez à la page d’administration du type de nœud *https://&lt;hôte>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Sélectionnez **[!UICONTROL Espaces de noms]** en haut de la page. La page d’administration des espaces de noms s’affiche dans une fenêtre.

1. Pour ajouter un espace de noms, sélectionnez **[!UICONTROL New]** en bas de l’écran.
1. Spécifiez un espace de noms personnalisé dans la convention de l’espace de noms XML (spécifiez l’identifiant sous la forme d’un URI et d’un préfixe associé pour l’identifiant), puis sélectionnez **[!UICONTROL Enregistrer]**.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
