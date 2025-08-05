---
title: Configurer l’interface d’utilisation du hub de contenus
description: Configurer l’interface d’utilisation du hub de contenus
exl-id: e9e22862-9bcd-459a-bcf4-7f376a0b329a
source-git-commit: 4125f6d99c1c1d63b9234d66dc552695bd30e7bc
workflow-type: tm+mt
source-wordcount: '2089'
ht-degree: 11%

---

# Configurer l’interface d’utilisation du hub de contenus {#configure-content-hub-user-interface}

>[!CONTEXTUALHELP]
>id="configure_content_hub"
>title="Configurer l’interface d’utilisation du hub de contenus"
>abstract="Experience Manager Assets permet à l’équipe d’aministration de configurer les options disponibles dans l’interface d’utilisation du hub de contenus. En fonction des options de configuration sélectionnées par l’équipe d’aministration, les utilisateurs et utilisatrices du hub de contenus peuvent afficher les champs sur le hub de Contenus. Les options de configuration incluent des métadonnées lors de l’import des ressources, des filtres, des propriétés de ressources, des métadonnées lors de la recherche de ressources, d’une image de marque personnalisée et de tout lien personnalisé."
>additional-url="https://images-tv.adobe.com/mpcv3/4477/74a81d1c-0cfe-41f4-8a06-18ff70604e45_1732023385.854x480at800_h264.mp4" text="Regarder la vidéo"

<!-- ![Download assets](assets/download-asset.jpg) -->

![Configuration de ressources sur Content Hub](assets/configure-assets.png)

Experience Manager Assets permet à l’équipe d’aministration de configurer les options disponibles dans l’interface d’utilisation du hub de contenus. En fonction des options de configuration sélectionnées par l’équipe d’aministration, les utilisateurs et utilisatrices du hub de contenus peuvent afficher les champs sur le hub de Contenus. Les options de configuration incluent :

* Filtres disponibles pour les utilisateurs lors de la recherche de ressources.

* Détails ou propriétés de la ressource disponibles pour chaque ressource.

* Champs de métadonnées disponibles pour les utilisateurs lors de l’ajout de ressources à Content Hub.

* Champs de métadonnées de ressource disponibles pour une recherche dans Content Hub.

* Valorisation de marque du contenu que vous devez afficher pour votre organisation.

* Tous les liens personnalisés que vous devez inclure sur Content Hub en plus des ressources, des collections et des informations.

## Prérequis {#prerequisites-configuration-ui}

Les [administrateurs Content Hub](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) peuvent définir les options de configuration pour d&#39;autres utilisateurs de votre organisation.

## Accéder aux options de configuration sur Content Hub {#access-configuration-options-content-hub}

Pour accéder aux options de configuration de Content Hub :

1. Cliquez sur l’icône utilisateur dans le volet de droite.

1. Dans la section **[!UICONTROL Paramètres du produit]**, sélectionnez **[!UICONTROL Configurations]**.

   ![Accéder aux options de configuration sur Content Hub](assets/access-content-hub-configuration-ui.png)

## Gestion des options de configuration sur Content Hub {#manage-configuration-options}

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

* [Collections et partage](#configure-collections-content-hub)

<!--* [Enable public link sharing](#enable-public-link-sharing)-->

### Import {#configure-import-options-content-hub}

Vous pouvez configurer les champs de métadonnées qui s’affichent pour les utilisateurs lors du chargement ou de l’importation de ressources sur le portail Content Hub, tels que le nom de la campagne, les mots-clés, les canaux, la période, la région, etc. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Importer]**.

1. Cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Indiquez un libellé pour la propriété, mappez-le à une propriété à l’aide du champ **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée des nouvelles métadonnées de la ressource.

1. Cliquez sur le bouton (bascule) **[!UICONTROL Champ obligatoire]** pour rendre le nouveau champ de métadonnées obligatoire à spécifier pour les utilisateurs lors du chargement de nouvelles ressources.

1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de la ressource existante.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété disponible, pour modifier les libellés, rendre ces champs obligatoires ou non obligatoires pour les utilisateurs lors du chargement de ressources à l’aide du bouton (bascule) **[!UICONTROL champ obligatoire]** ou cliquer sur l’icône Supprimer pour supprimer une propriété de métadonnées.

Cliquez sur le bouton (bascule) **[!UICONTROL Approbation automatique]** si vous avez besoin que toutes les ressources que vous ajoutez au référentiel Experience Manager Assets soient approuvées automatiquement afin qu’elles soient disponibles immédiatement dans Content Hub. Dans le cas contraire, les auteurs ou les administrateurs de gestion des ressources numériques doivent approuver manuellement les ressources pour les rendre disponibles sur Content Hub. Par défaut, le bouton (bascule) est défini sur l’état Désactivé .

Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications pour appliquer les modifications.

![Détails de chargement de l’interface utilisateur de configuration sur Content Hub](/help/assets/assets/import-content-hub1.png)

Les métadonnées activées dans l’interface utilisateur de configuration s’affichent dans la page de chargement des ressources :
![Chargement de métadonnées sur Content Hub](assets/add-assets-for-approval1.png)

### Filtres {#configure-filters-content-hub}

Content Hub permet aux administrateurs de configurer des filtres qui s’affichent lors de la recherche de ressources. Pour ajouter un nouveau filtre, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Filtres]**.

1. Cliquez sur **[!UICONTROL Ajouter des filtres]**.

1. Indiquez un libellé pour le filtre, mappez-le à une propriété à l’aide du champ **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée du nouveau filtre.
1. Cliquez sur **[!UICONTROL Confirmer]**. Le nouveau filtre s’affiche dans la liste des filtres existants.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications afin que le nouveau filtre s’affiche sur la page Rechercher lors du filtrage des ressources.

   >[!NOTE]
   >
   >Le nouveau filtre ne s’affiche sur la page Rechercher que s’il existe au moins une ressource dans le référentiel correspondant aux critères de filtre.

De même, vous pouvez cliquer sur ![icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque filtre disponible, pour modifier les libellés ou cliquer sur l’icône de suppression pour supprimer un filtre existant. Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications pour appliquer les modifications.
![Filtres de l’interface utilisateur de configuration sur Content Hub](assets/configuration-filter1.png)

Les filtres activés dans l’interface utilisateur de configuration s’affichent dans la page Rechercher :
![Recherche sur Content Hub](assets/content-hub-filters1.png)

### Détails des ressources {#configure-asset-details-content-hub}

Vous pouvez également configurer les propriétés de la ressource qui s’affichent pour chaque ressource, telles que le nom du fichier, le titre, le format, la taille, etc. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Détails de la ressource]**.

1. Cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Indiquez un libellé pour la propriété, mappez-le à une propriété à l’aide du champ **[!UICONTROL Métadonnées]** et sélectionnez le type d’entrée des nouvelles métadonnées de la ressource.
1. Cliquez sur **[!UICONTROL Confirmer]**. Les nouvelles métadonnées s’affichent dans la liste des propriétés de la ressource existante.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications de sorte que la nouvelle propriété s’affiche sur la page des détails de la ressource.

De même, vous pouvez cliquer sur ![icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété disponible, pour modifier les libellés ou cliquer sur l’icône de suppression pour supprimer tout détail de ressource existant. Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications pour appliquer les modifications.

![Détails de la ressource de l’interface utilisateur de configuration dans Content Hub](assets/configuration-asset-details.png)

Les propriétés activées dans l’interface utilisateur de configuration s’affichent dans la page Détails de la ressource :

![Propriétés de la ressource sur Content Hub](assets/asset-details-page-content-hub1.png)

### Carte de ressources {#asset-card}

Vous pouvez également configurer les propriétés de métadonnées clés que vous devez afficher sur la **Carte de ressource** jusqu’à 6 champs maximum.
![métadonnées clés sur la carte de la ressource](/help/assets/assets/asset-card-metadata.png)
Pour configurer les propriétés de métadonnées afin de les afficher sur la carte **[!UICONTROL Ressource]**, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **Carte des ressources**.
2. Cliquez sur **Ajouter des métadonnées**. La boîte de dialogue **Ajouter des métadonnées de carte de ressources** s’affiche.
3. Indiquez le nom des métadonnées dans le champ **Libellé** et sélectionnez une propriété de métadonnées dans le champ **Métadonnées**.
4. Cliquez sur **Confirmer** puis sur **Enregistrer** pour appliquer les modifications afin que la nouvelle propriété s’affiche sur la page des détails de la ressource.
   ![carte des ressources](/help/assets/assets/configuration-asset-card1.png)
De même, cliquez sur ![Modifier](/help/assets/assets/edit-content-hub.svg) disponible en regard de chaque propriété disponible pour apporter les modifications nécessaires ou cliquez sur ![Supprimer](/help/assets/assets/delete-content-hub.svg) pour supprimer une propriété de métadonnées existante. Cliquez sur **Enregistrer** après avoir effectué toutes les modifications pour appliquer les modifications.

### Recherche {#configure-metadata-search-content-hub}

L’administration peut définir les champs de métadonnées qui font l’objet d’une recherche lorsqu’un utilisateur spécifie un critère de recherche dans Content Hub. Procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Ajouter des métadonnées]**.

1. Spécifiez le champ de métadonnées et cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications de sorte que la nouvelle propriété de métadonnées s’affiche dans la liste des champs de métadonnées.

De même, vous pouvez cliquer sur ![icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque propriété de métadonnées disponible, pour modifier la propriété ou cliquer sur l’icône de suppression pour supprimer une propriété existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications pour appliquer les modifications.
![Recherche dans l’interface utilisateur de configuration de Content Hub](assets/configuration-search.png)

### Branding {#configure-branding-content-hub}

En tant qu’administrateur, personnalisez votre portail [!DNL Content Hub] pour répondre à vos exigences en matière de marque.
![réinitialiser la valeur par défaut](/help/assets/assets/reset-default-content-hub.png)
Sur la page ![Branding](/help/assets/assets/ColorPalette.svg) **[!UICONTROL Branding]**, utilisez les sections **[!UICONTROL Bannière]**, **[!UICONTROL Couleurs]** et **[!UICONTROL Image de bannière]** pour exécuter les personnalisations suivantes :

1. [Modifiez l’image de bannière à partir de la section [!UICONTROL &#x200B; Image de bannière &#x200B;]](#Change-the-banner-image)
1. [Mettez à jour le titre et le texte du corps de la bannière et modifiez la couleur du texte dans la section [!UICONTROL Bannière]](#Add-title-and-body-text-to-your-banner-and-change-the-text-color)
1. [Modifiez la couleur principale et secondaire de la section [!UICONTROL Couleurs] pour appliquer un jeu de couleurs qui s’aligne sur le thème de votre marque](#Change-the-primary-and-secondary-color)

Sélectionnez l’option **[!UICONTROL Réinitialiser les valeurs par défaut]** pour annuler vos modifications et restaurer le thème par défaut.

#### Modification de l’image de bannière{#Change-the-banner-image}

Sur la page ![Image de marque](/help/assets/assets/ColorPalette.svg) **[!UICONTROL Image de marque]**, effectuez les étapes suivantes pour modifier l’image de bannière de votre déploiement [!DNL Content Hub] :

1. Cliquez sur ![sélectionner une image](/help/assets/assets/Browse.svg) **[!UICONTROL Sélectionner dans la galerie]** pour sélectionner une image de bannière à l’aide de la boîte de dialogue du sélecteur de ressources. Le sélecteur de ressources affiche uniquement les images approuvées.
1. Sélectionnez l’image, cliquez sur **[!UICONTROL Sélectionner]**, puis cliquez sur **[!UICONTROL Enregistrer]** pour l’afficher en tant qu’image de bannière de votre déploiement [!DNL Content Hub].
   ![image de bannière](/help/assets/assets/banner-image-content-hub1.png)

#### Ajoutez le titre et le corps du texte à votre bannière et modifiez la couleur du texte{#Add-title-and-body-text-to-your-banner-and-change-the-text-color}

Sur la page ![Branding](/help/assets/assets/ColorPalette.svg) **[!UICONTROL Branding]**, utilisez les champs respectifs de la section **[!UICONTROL Bannière]** pour ajouter le titre et le corps du texte à votre bannière.
Cliquez sur la zone carrée en regard de la **[!UICONTROL Couleur du texte de bannière]** pour sélectionner une couleur de texte dans le sélecteur de couleurs pour votre texte de bannière ou spécifiez le code hexadécimal de la couleur dans le champ en regard de la zone carrée du sélecteur de couleurs.
![centre de contenu de texte de bannière](/help/assets/assets/banner-text-content-hub.png)

#### Modification de la couleur principale et de la couleur secondaire{#Change-the-primary-and-secondary-color}

Sur la page ![Branding](/help/assets/assets/ColorPalette.svg) **[!UICONTROL Branding]**, utilisez la section **[!UICONTROL Couleurs]** pour définir les couleurs primaires et secondaires en les sélectionnant à l’aide du sélecteur de couleurs ou en définissant le code hexadécimal de la couleur. Ces couleurs définissent les couleurs d’arrière-plan, de texte et d’icône des éléments de l’interface utilisateur pour aligner votre interface utilisateur [!DNL Content Hub] avec le thème de votre marque.
![couleur primaire et secondaire](/help/assets/assets/primary-secondary-color-content-hub1.png)
**[!UICONTROL Couleur du Principal &#x200B;]:** Le jeu de couleurs principal s’applique aux actions de sélection, aux éléments interactifs tels que les cases à cocher, les barres de recherche et les commutateurs à travers les [!DNL Content Hub], y compris [!DNL Content Hub] page d’accueil et la page [!UICONTROL Configuration]. Elle s’applique également aux options d’action disponibles sur les interfaces de [!DNL Content Hub] principales, telles que les options disponibles sur les pages **[!UICONTROL Toutes les Assets]** et **[!UICONTROL Collections]**.

**[!UICONTROL Couleur Secondaire &#x200B;]:** Sur la page d&#39;accueil [!DNL Content Hub], le jeu de couleurs secondaire s&#39;applique aux options de l&#39;interface utilisateur et aux champs de saisie disponibles dans les boîtes de dialogue. Elle s’applique à toutes les options de menu de configuration disponibles sur la page [!UICONTROL Configuration], à l’exception des actions de sélection, des cases à cocher, des barres de recherche et des commutateurs.

### Visibilité des ressources{#asset-visibility-content-hub}

Les administrateurs peuvent décider s’ils souhaitent que les ressources expirées soient visibles sur Content Hub. Si les ressources expirées sont rendues visibles, les administrateurs et administratrices peuvent également définir si les personnes peuvent les télécharger.

Par défaut, les ressources arrivées à expiration ne s’affichent pas dans Content Hub.

Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Visibilité des ressources]**.

1. Dans la section **[!UICONTROL Visible]**, activez le bouton (bascule) **[!UICONTROL Autoriser les utilisateurs à afficher les ressources expirées]** pour rendre toutes les ressources expirées visibles sur Content Hub.

1. Après avoir activé la visibilité des ressources, vous pouvez activer ou désactiver la possibilité de télécharger les ressources expirées à l’aide du bouton **[!UICONTROL Autoriser les utilisateurs à télécharger les ressources expirées]**.
1. Activez le bouton (bascule) **[!UICONTROL Autoriser les utilisateurs à afficher les ressources approuvées pour diffusion]** pour afficher toutes les ressources approuvées pour diffusion dans Content Hub.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

   ![Ressources expirées sur le hub de contenus](assets/asset-visibility-content-hub1.png)

Après avoir activé la visibilité des ressources, vous pouvez afficher les ressources expirées sur Content Hub, comme illustré dans l’image suivante :

![Ressources expirées sur le hub de contenus](assets/view-download-expired-assets.png)

Si l’administrateur a activé le téléchargement, les utilisateurs de Content Hub peuvent également les télécharger, comme indiqué dans l’image.

Si la visibilité des ressources arrivées à expiration est activée, Content Hub met également en surbrillance les ressources arrivant à expiration dans les 15 prochains jours à l’aide du message `Expiring in n days` sur la carte des ressources.

### Rendus {#renditions-content-hub}

Les rendus sont des versions personnalisées des ressources numériques, telles que les images, les documents, etc., conçues pour différents appareils et plateformes afin d’assurer des performances optimales. En savoir plus sur les [rendus dans Adobe Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/renditions).

Pour cela, procédez comme suit :

Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Rendus]**. Les options suivantes sont disponibles :

* Activez le bouton (bascule) [!UICONTROL Activer la disponibilité des rendus] pour rendre tous les rendus visibles sur Content Hub.

* Activez ou désactivez le bouton (bascule) **[!UICONTROL Autoriser les utilisateurs à télécharger les ressources d’origine]** pour contrôler la disponibilité du téléchargement des ressources d’origine.

  ![Configuration des rendus sur Content Hub](assets/configuration-renditions1.png)

Pour plus d’informations sur l’affichage et le téléchargement des rendus dans Content Hub, voir [téléchargement de ressources dans Content Hub](/help/assets/download-assets-content-hub.md).

### Liens personnalisés {#configure-custom-links-content-hub}

Vous pouvez également ajouter des onglets personnalisés en plus des onglets standard **[!UICONTROL Toutes les Assets]**, **[!UICONTROL Collections]** et **[!UICONTROL Informations]** sur le portail Content Hub, juste en dessous de la bannière. Pour cela, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Liens personnalisés]**.

1. Cliquez sur **[!UICONTROL Ajouter un lien]**.

1. Spécifiez du texte dans les champs **[!UICONTROL Libellé]** et **[!UICONTROL URL]**. Le libellé que vous définissez s’affiche sous la forme d’un onglet et, lorsque vous cliquez sur le libellé, vous accédez à l’URL définie dans le champ **[!UICONTROL URL]**.

1. Cliquez sur **[!UICONTROL Confirmer]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

De même, vous pouvez cliquer sur ![icône Modifier](assets/do-not-localize/edit_icon.svg), disponible en regard de chaque URL, pour modifier les liens ou cliquer sur l’icône de suppression pour supprimer une URL existante. Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications pour appliquer les modifications.
![Liens personnalisés de l’interface utilisateur de configuration de Content Hub](assets/configuration-custom-links1.png)

Le lien personnalisé s’affiche sous la forme d’un nouvel onglet en regard de l’onglet Insights sur la page d’accueil de Content Hub.
![Onglets de liens personnalisés de l’interface utilisateur de configuration de Content Hub](assets/configuration-ui-custom-link-tab.png)

### Collections et partage {#configure-collections-content-hub}

Les administrateurs peuvent définir des autorisations utilisateur lors de la création de collections. Pour activer ces paramètres, procédez comme suit :

1. Dans l’interface utilisateur [Configurations](#access-configuration-options-content-hub), cliquez sur **[!UICONTROL Collections]**.

1. Activez le bouton (bascule) **[!UICONTROL Activer le lien public]** pour permettre la création de liens publics que les utilisateurs et utilisatrices externes peuvent utiliser pour accéder aux ressources et les télécharger sans se connecter au Content Hub.

1. Activez le bouton (bascule) **[!UICONTROL Afficher uniquement les collections]** pour autoriser les collections accessibles à tous, mais modifiables uniquement par le créateur et l’administrateur.

1. Activez le bouton (bascule) **[!UICONTROL Collections publiques]** pour autoriser les collections qui sont à la fois accessibles et modifiables par tout le monde. Si les bascules **[!UICONTROL Afficher uniquement les collections]** et **[!UICONTROL Collections publiques]** sont désactivées, alors par défaut, les utilisateurs non-administrateurs peuvent créer uniquement des collections privées.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les modifications.

   ![Onglet Collections de configurations dans Content Hub](assets/collections-and-sharing1.png)

<!--
### Enable public link sharing {#enable-public-link-sharing}

Enable the following setting on the Configurations user interface to allow Content Hub users to generate a public link:

1. On the [Configurations](#access-configuration-options-content-hub) user interface, click **[!UICONTROL Collections and Sharing]**.

1. Enable the **[!UICONTROL Enable Public Link]** toggle and click **[!UICONTROL Save]** to apply the changes.

    ![Enable public link sharing in Content Hub](assets/enable-public-link-sharing-tab.png)

-->

En savoir plus sur le [partage de ressources dans la  [!DNL Content Hub]](share-assets-content-hub.md).