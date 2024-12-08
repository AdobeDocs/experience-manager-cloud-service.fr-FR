---
title: Configurer l’interface d’utilisation du hub de contenus
description: Configurer l’interface d’utilisation du hub de contenus
exl-id: e9e22862-9bcd-459a-bcf4-7f376a0b329a
source-git-commit: 323fe1ba95b027f3c0d625e122b1885723e94b0f
workflow-type: tm+mt
source-wordcount: '1718'
ht-degree: 17%

---

# Configurer l’interface d’utilisation du hub de contenus {#configure-content-hub-user-interface}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!CONTEXTUALHELP]
>id="configure_content_hub"
>title="Configurer l’interface d’utilisation du hub de contenus"
>abstract="Experience Manager Assets permet à l’équipe d’aministration de configurer les options disponibles dans l’interface d’utilisation du hub de contenus. En fonction des options de configuration sélectionnées par l’équipe d’aministration, les utilisateurs et utilisatrices du hub de contenus peuvent afficher les champs sur le hub de Contenus. Les options de configuration incluent des métadonnées lors de l’import des ressources, des filtres, des propriétés de ressources, des métadonnées lors de la recherche de ressources, d’une image de marque personnalisée et de tout lien personnalisé."
>additional-url="https://images-tv.adobe.com/mpcv3/4477/74a81d1c-0cfe-41f4-8a06-18ff70604e45_1732023385.854x480at800_h264.mp4" text="Regarder la vidéo"

<!-- ![Download assets](assets/download-asset.jpg) -->

![Configuration de ressources sur Content Hub](assets/configure-assets.png)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Experience Manager Assets permet à l’équipe d’aministration de configurer les options disponibles dans l’interface d’utilisation du hub de contenus. En fonction des options de configuration sélectionnées par l’équipe d’aministration, les utilisateurs et utilisatrices du hub de contenus peuvent afficher les champs sur le hub de Contenus. Les options de configuration incluent :

* Filtres disponibles pour les utilisateurs lors de la recherche de ressources.

* Détails ou propriétés des ressources disponibles pour chaque ressource.

* Champs de métadonnées disponibles pour les utilisateurs lors de l’ajout de ressources à Content Hub.

* Champs de métadonnées de ressource disponibles pour la recherche dans Content Hub.

* Contenu de marque que vous devez afficher pour votre entreprise.

* Tous les liens personnalisés que vous devez inclure dans Content Hub en plus des ressources, des collections et des insights.

## Conditions préalables {#prerequisites-configuration-ui}

[Les administrateurs Content Hub](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) peuvent définir les options de configuration pour d’autres utilisateurs de votre entreprise.

## Accès aux options de configuration sur Content Hub {#access-configuration-options-content-hub}

Pour accéder aux options de configuration sur Content Hub :

1. Cliquez sur l’icône utilisateur dans le volet de droite.

1. Dans la section **[!UICONTROL Paramètres du produit]**, sélectionnez **[!UICONTROL Configurations]**.

   ![ Accès aux options de configuration sur Content Hub](assets/access-content-hub-configuration-ui.png)

## Gestion des options de configuration dans Content Hub {#manage-configuration-options}

En tant qu’administrateur, gérez les options de configuration suivantes pour vos utilisateurs :

* [Import](#configure-import-options-content-hub)

* [Filtres](#configure-filters-content-hub)

* [Détails des ressources](#configure-asset-details-content-hub)
* [Carte de ressources](#asset-card)

* [Recherche](#configure-metadata-search-content-hub)

* [Branding](#configure-branding-content-hub)

* [Ressources expirées](#expired-assets-content-hub)

* [Rendus](#renditions-content-hub)

* [Liens personnalisés](#configure-custom-links-content-hub)

### Import {#configure-import-options-content-hub}

Vous pouvez configurer les champs de métadonnées qui s’affichent pour les utilisateurs lors du chargement ou de l’importation de ressources sur le portail Content Hub, tels que le nom de la campagne, les mots-clés, les canaux, la période, la région, etc. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Importer]**.

1. Cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Spécifiez un libellé pour la propriété, mappez-le à une propriété à l’aide du champ **[!UICONTROL Metadata]** et sélectionnez le type d’entrée pour les nouvelles métadonnées de ressource.

1. Cliquez sur le bouton **[!UICONTROL Champ obligatoire]** pour rendre le nouveau champ de métadonnées obligatoire pour spécifier les utilisateurs lors du chargement de nouvelles ressources.

1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de ressource existantes.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété disponible, pour modifier les étiquettes, rendre ces champs obligatoires ou non obligatoires pour les utilisateurs lors du chargement des ressources à l’aide du bouton d’activation/désactivation **[!UICONTROL Champ obligatoire]** ou cliquer sur l’icône Supprimer pour supprimer toute propriété de métadonnées.

Cliquez sur le bouton **[!UICONTROL Validation automatique]** si vous souhaitez que toutes les ressources que vous ajoutez au référentiel Experience Manager Assets soient automatiquement approuvées afin qu’elles soient disponibles dans Content Hub immédiatement. Autrement, les auteurs ou les administrateurs DAM doivent approuver manuellement les ressources pour les rendre disponibles sur Content Hub. Le bouton bascule est désactivé par défaut.

Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Détails de chargement de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-upload-details.png)

Les métadonnées activées dans l’interface utilisateur de configuration s’affichent sur la page de chargement des ressources :

![Chargement de métadonnées sur Content Hub](assets/configuration-ui-add-assets.png)

### Filtres {#configure-filters-content-hub}

Content Hub permet aux administrateurs de configurer des filtres qui s’affichent lors de la recherche de ressources. Pour ajouter un nouveau filtre, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Filtres]**.

1. Cliquez sur **[!UICONTROL Ajouter des filtres]**.

1. Spécifiez un libellé pour le filtre, mappez-le à une propriété à l’aide du champ **[!UICONTROL Metadata]** et sélectionnez le type d’entrée pour le nouveau filtre.
1. Cliquez sur **[!UICONTROL Confirmer]**. Le nouveau filtre s’affiche dans la liste des filtres existants.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que le nouveau filtre s’affiche sur la page Rechercher lors du filtrage des ressources.

   >[!NOTE]
   >
   Le nouveau filtre s’affiche sur la page Recherche uniquement s’il existe une autre ressource dans le référentiel correspondant aux critères de filtrage.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque filtre disponible, pour modifier les étiquettes ou cliquer sur l’icône Supprimer pour supprimer tout filtre existant. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Filtres d’IU de configuration sur Content Hub](assets/configuration-ui-filters.png)

Les filtres activés dans l’interface utilisateur de configuration s’affichent sur la page Rechercher :

![Rechercher sur Content Hub](assets/filters-for-search.png)


### Détails des ressources {#configure-asset-details-content-hub}

Vous pouvez également configurer les propriétés de ressource qui s’affichent pour chaque ressource, telles que le nom de fichier, le titre, le format, la taille, etc. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Détails de la ressource]**.

1. Cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Spécifiez un libellé pour la propriété, mappez-le à une propriété à l’aide du champ **[!UICONTROL Metadata]** et sélectionnez le type d’entrée pour les nouvelles métadonnées de ressource.
1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de ressource existantes.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que la nouvelle propriété s’affiche sur la page des détails de la ressource.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété disponible, pour modifier les étiquettes ou cliquer sur l’icône Supprimer pour supprimer les détails de ressource existants. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![ Détails des ressources de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-asset-details.png)

Les propriétés activées dans l’interface utilisateur de configuration s’affichent sur la page Détails de la ressource :

![Propriétés de ressource sur Content Hub](assets/config-ui-asset-properties.png)

### Carte de ressources {#asset-card}

Vous pouvez également configurer les champs de métadonnées clés que vous devez afficher sur la **carte de ressources** jusqu’à 6 champs au maximum. Pour cela, procédez comme suit :

![Métadonnées clés sur la carte de ressources](/help/assets/assets/asset-card-key-metadata.png)

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **Asset Card**.
2. Cliquez sur **Ajouter des métadonnées**. La boîte de dialogue **Ajouter des métadonnées de carte de ressource** s’affiche.
3. Indiquez le nom des métadonnées dans le champ **Label** et sélectionnez une propriété de métadonnées dans le champ **Metadata** .
4. Cliquez sur **Confirmer**, puis sur **Enregistrer** pour appliquer les modifications afin que la nouvelle propriété s’affiche sur la page des détails de la ressource.
   ![carte de ressource](/help/assets/assets/asset-card.png)

De même, cliquez sur ![edit](/help/assets/assets/edit-content-hub.svg) disponible en regard de chaque propriété disponible pour apporter les modifications requises ou cliquez sur ![delete](/help/assets/assets/delete-content-hub.svg) pour supprimer toute propriété de métadonnées existante. Cliquez sur **Enregistrer** après avoir apporté toutes les modifications pour appliquer les modifications.

### Recherche {#configure-metadata-search-content-hub}

Les administrateurs peuvent définir les champs de métadonnées qui font l’objet d’une recherche lorsqu’un utilisateur spécifie un critère de recherche sur Content Hub. Procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Spécifiez le champ de métadonnées et cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que la nouvelle propriété de métadonnées s’affiche dans la liste des champs de métadonnées.

De même, vous pouvez cliquer sur ![Modifier l’icône](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété de métadonnées disponible, pour modifier la propriété ou cliquer sur l’icône de suppression pour supprimer une propriété existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Recherche de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Les administrateurs peuvent également personnaliser le titre et le corps du texte sur la bannière du portail Content Hub, en fonction de vos besoins en termes de branding. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Valorisation de marque]**.

1. Spécifiez le texte dans les champs **[!UICONTROL Texte du titre sur la bannière]** et **[!UICONTROL Texte du corps sur la bannière]** .

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

![Marque de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-branding.png)

Les mises à jour de branding activées dans l’interface utilisateur de configuration s’affichent sur la bannière du portail Content Hub :

![Marque de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-branding-updates.png)

### Ressources expirées{#expired-assets-content-hub}

Les administrateurs peuvent contrôler s’ils ont besoin que les ressources expirées soient visibles sur Content Hub. Si les ressources expirées sont rendues visibles, les administrateurs et administratrices peuvent également définir si les personnes peuvent les télécharger.

Les ressources expirées ne s’affichent pas par défaut dans Content Hub.

Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Assets expirée]**.

1. Dans la section **[!UICONTROL Visible]** , activez le bouton d’activation/désactivation **[!UICONTROL Autoriser les utilisateurs à afficher les ressources expirées]** pour rendre toutes les ressources expirées visibles sur Content Hub.

1. Après avoir activé la visibilité des ressources, vous pouvez activer ou désactiver la possibilité de télécharger les ressources expirées à l’aide du bouton d’activation/désactivation **[!UICONTROL Autoriser les utilisateurs à télécharger les ressources expirées]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

   ![Ressources expirées sur le hub de contenus](assets/expired-assets-content-hub.png)

Après avoir activé la visibilité des ressources, vous pouvez afficher les ressources expirées sur Content Hub, comme illustré dans l’image suivante :

![Ressources expirées sur le hub de contenus](assets/view-download-expired-assets.png)

Si l’administrateur a activé le téléchargement, les utilisateurs de Content Hub peuvent également le télécharger, comme indiqué dans l’image.

Si la visibilité des ressources expirées est activée, Content Hub met également en surbrillance les ressources arrivant à expiration au cours des 15 prochains jours à l’aide du message `Expiring in n days` sur la carte de ressources.

### Rendus {#renditions-content-hub}

Les rendus sont des versions personnalisées des ressources numériques, telles que des images, des documents, etc., conçues pour différents appareils et plateformes afin d’assurer des performances optimales. Pour en savoir plus sur les [rendus dans Adobe Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/renditions).

Content Hub permet de télécharger des rendus statiques. Les rendus statiques sont différentes représentations du fichier d’origine d’une ressource générée en mode natif. Par exemple, les miniatures ou les rendus optimisés pour les appareils mobiles. Les administrateurs peuvent gérer et contrôler la disponibilité des rendus de ressources, et gérer si vous pouvez télécharger des ressources d’origine ou non.

Pour cela, procédez comme suit :

Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Rendus]**. Les options suivantes sont disponibles :

* Activez le bouton d’activation/désactivation [!UICONTROL Activer la disponibilité des rendus statiques] pour rendre tous les rendus statiques visibles sur Content Hub.

* Activez ou désactivez le bouton d’activation/désactivation **[!UICONTROL Autoriser les utilisateurs à télécharger les ressources d’origine]** afin de contrôler la disponibilité du téléchargement des ressources d’origine.

  ![Configuration de rendus sur Content Hub](assets/config-renditions.png)

Pour plus d’informations sur l’affichage et le téléchargement des rendus statiques dans Content Hub, voir [téléchargement de ressources dans Content Hub](/help/assets/download-assets-content-hub.md).

### Liens personnalisés {#configure-custom-links-content-hub}

Vous pouvez également ajouter des onglets personnalisés en plus des onglets **[!UICONTROL Tous les Assets]**, **[!UICONTROL Collections]** et **[!UICONTROL Statistiques]** standard sur le portail Content Hub juste en dessous de la bannière. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Liens personnalisés]**.

1. Cliquez sur **[!UICONTROL Ajouter un lien]**.

1. Spécifiez le texte dans les champs **[!UICONTROL Libellé]** et **[!UICONTROL URL]** . Le libellé que vous définissez s&#39;affiche sous forme d&#39;onglet et lorsque vous cliquez sur le libellé, vous accédez à l&#39;URL définie dans le champ **[!UICONTROL URL]**.

1. Cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque URL, pour modifier les liens ou cliquer sur l’icône Supprimer pour supprimer toute URL existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Liens personnalisés de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-custom-links.png)

Le lien personnalisé s’affiche sous forme d’un nouvel onglet en regard de l’onglet Statistiques sur la page d’accueil de Content Hub.

![Onglets Liens personnalisés de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-custom-link-tab.png)
