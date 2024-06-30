---
title: Configuration de l’interface utilisateur de Content Hub
description: Configuration de l’interface utilisateur de Content Hub
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 6%

---

# Configuration de l’interface utilisateur de Content Hub {#configure-content-hub-user-interface}

<!-- ![Download assets](assets/download-asset.jpg) -->
![Configuration de ressources sur Content Hub](assets/configure-assets.png)

Experience Manager Assets permet aux administrateurs de configurer les options disponibles dans l’interface utilisateur de Content Hub. En fonction des options de configuration sélectionnées par les administrateurs, les utilisateurs de Content Hub peuvent afficher les champs de Content Hub. Les options de configuration incluent :

* Filtres disponibles pour les utilisateurs lors de la recherche de ressources.

* Détails ou propriétés des ressources disponibles pour chaque ressource.

* Champs de métadonnées disponibles pour les utilisateurs lors de l’ajout de ressources à Content Hub.

* Champs de métadonnées de ressource disponibles pour la recherche dans Content Hub.

* Contenu de marque que vous devez afficher pour votre entreprise.

* Tous les liens personnalisés que vous devez inclure dans Content Hub en plus des ressources, des collections et des insights.

## Conditions préalables {#prerequisites-configuration-ui}

[Administrateurs Content Hub](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) peut définir les options de configuration pour d’autres utilisateurs de votre entreprise.

## Accès aux options de configuration sur Content Hub {#access-configuration-options-content-hub}

Pour accéder aux options de configuration sur Content Hub :

1. Cliquez sur l’icône utilisateur dans le volet de droite.

1. Dans le **[!UICONTROL Paramètres du produit]** , sélectionnez **[!UICONTROL Configurations]**.

   ![Accès aux options de configuration sur Content Hub](assets/access-content-hub-configuration-ui.png)

## Gestion des options de configuration dans Content Hub {#manage-configuration-options}

Gérez les options de configuration suivantes pour vos utilisateurs :

* [Import](#configure-import-options-content-hub)

* [Filtres](#configure-filters-content-hub)

* [Détails des ressources](#configure-asset-details-content-hub)

* [Recherche](#configure-metadata-search-content-hub)

* [Branding](#configure-branding-content-hub)

* [Liens personnalisés](#configure-custom-links-content-hub)

### Import {#configure-import-options-content-hub}

Vous pouvez configurer les champs de métadonnées qui s’affichent pour les utilisateurs lors du chargement ou de l’importation de ressources sur le portail Content Hub, tels que le nom de la campagne, les mots-clés, les canaux, la période, la région, etc. Pour cela, procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Importer]**.

1. Cliquez sur **[!UICONTROL Ajout de métadonnées]**.

1. Spécifiez un libellé pour la propriété, puis mappez-le à une propriété à l’aide de la propriété **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée des nouvelles métadonnées de la ressource.

1. Cliquez sur le bouton **[!UICONTROL Champ obligatoire]** pour rendre le nouveau champ de métadonnées obligatoire à spécifier pour les utilisateurs lors du chargement de nouvelles ressources.

1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de ressource existantes.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponibles en regard de chaque propriété disponible, pour modifier les libellés, rendez ces champs obligatoires ou non obligatoires pour les utilisateurs lors du chargement de ressources à l’aide de la variable **[!UICONTROL Champ obligatoire]** Activez ou cliquez sur l’icône Supprimer pour supprimer une propriété de métadonnées.

Cliquez sur le bouton **[!UICONTROL Validation automatique]** Activez cette option si vous souhaitez que toutes les ressources que vous ajoutez au référentiel Experience Manager Assets soient automatiquement approuvées afin qu’elles soient disponibles immédiatement dans Content Hub. Autrement, les auteurs ou les administrateurs DAM doivent approuver manuellement les ressources pour les rendre disponibles sur Content Hub. Le bouton bascule est désactivé par défaut.

Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Informations détaillées sur le chargement de l’interface utilisateur de configuration dans Content Hub](assets/configuration-ui-upload-details.png)

Les métadonnées activées dans l’interface utilisateur de configuration s’affichent sur la page de chargement des ressources :

![Chargement de métadonnées sur Content Hub](assets/configuration-ui-add-assets.png)

### Filtres {#configure-filters-content-hub}

Content Hub permet aux administrateurs de configurer des filtres qui s’affichent lors de la recherche de ressources. Pour ajouter un nouveau filtre, procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Filtres]**.

1. Cliquez sur **[!UICONTROL Ajout de filtres]**.

1. Spécifiez un libellé pour le filtre, puis mappez-le à une propriété à l’aide de la propriété **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée du nouveau filtre.
1. Cliquez sur **[!UICONTROL Confirmer]**. Le nouveau filtre s’affiche dans la liste des filtres existants.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que le nouveau filtre s’affiche sur la page Rechercher lors du filtrage des ressources.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque filtre disponible, pour modifier les libellés ou cliquez sur l’icône de suppression pour supprimer un filtre existant. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Filtres de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-filters.png)

Les filtres activés dans l’interface utilisateur de configuration s’affichent sur la page Rechercher :

![Recherche sur Content Hub](assets/filters-for-search.png)


### Détails des ressources {#configure-asset-details-content-hub}

Vous pouvez également configurer les propriétés de ressource qui s’affichent pour chaque ressource, telles que le nom de fichier, le titre, le format, la taille, etc. Pour cela, procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Détails de la ressource]**.

1. Cliquez sur **[!UICONTROL Ajout de métadonnées]**.

1. Spécifiez un libellé pour la propriété, puis mappez-le à une propriété à l’aide de la propriété **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée des nouvelles métadonnées de la ressource.
1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de ressource existantes.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que la nouvelle propriété s’affiche sur la page des détails de la ressource.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété disponible, pour modifier les libellés ou cliquez sur l’icône de suppression pour supprimer les détails de ressource existants. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Détails des ressources de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-asset-details.png)

Les propriétés activées dans l’interface utilisateur de configuration s’affichent sur la page Détails de la ressource :

![Propriétés des ressources sur Content Hub](assets/config-ui-asset-properties.png)

### Recherche {#configure-metadata-search-content-hub}

Les administrateurs peuvent définir les champs de métadonnées qui font l’objet d’une recherche lorsqu’un utilisateur spécifie un critère de recherche sur Content Hub. Procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Ajout de métadonnées]**.

1. Spécifiez le champ de métadonnées et cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que la nouvelle propriété de métadonnées s’affiche dans la liste des champs de métadonnées.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété de métadonnées disponible, pour modifier la propriété ou cliquez sur l’icône de suppression pour supprimer une propriété existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Recherche dans l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Les administrateurs peuvent également personnaliser le titre et le corps du texte sur la bannière du portail Content Hub, en fonction de vos besoins en termes de branding. Pour cela, procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Marques]**.

1. Spécification du texte dans **[!UICONTROL Texte du titre sur la bannière]** et **[!UICONTROL Corps de texte sur la bannière]** des champs.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

![Marque de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-branding.png)

Les mises à jour de branding activées dans l’interface utilisateur de configuration s’affichent sur la bannière du portail Content Hub :

![Marque de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-branding-updates.png)

### Liens personnalisés {#configure-custom-links-content-hub}

Vous pouvez également ajouter des onglets personnalisés aux **[!UICONTROL Toutes les Assets]**, **[!UICONTROL Collections]**, et **[!UICONTROL Informations]** onglets sur le portail Content Hub juste en dessous de la bannière. Pour cela, procédez comme suit :

1. Sur le [Configurations](#access-configuration-options-content-hub) interface utilisateur, cliquez sur **[!UICONTROL Liens personnalisés]**.

1. Cliquez sur **[!UICONTROL Ajouter un lien]**.

1. Spécification du texte dans **[!UICONTROL Libellé]** et **[!UICONTROL URL]** des champs. Le libellé que vous définissez s’affiche sous la forme d’un onglet. Lorsque vous cliquez sur le libellé, vous accédez à l’URL définie dans la variable **[!UICONTROL URL]** champ .

1. Cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![Icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque URL, pour modifier les liens ou cliquez sur l’icône de suppression pour supprimer une URL existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir apporté toutes les modifications pour appliquer les modifications.

![Interface utilisateur de configuration Liens personnalisés sur Content Hub](assets/configuration-ui-custom-links.png)

Le lien personnalisé s’affiche sous forme d’un nouvel onglet en regard de l’onglet Statistiques sur la page d’accueil de Content Hub.

![Onglets Liens personnalisés de l’interface utilisateur de configuration sur Content Hub](assets/configuration-ui-custom-link-tab.png)


