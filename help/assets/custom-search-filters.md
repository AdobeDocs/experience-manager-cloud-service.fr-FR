---
title: Filtres de recherche personnalisés
description: En savoir plus sur la personnalisation du formulaire des filtres de recherche
role: User, Leader, Developer
source-git-commit: 0f97264a3daf7a40ecbb619b5c686ffc279800fb
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 13%

---

# Personnalisation des filtres de recherche {#customize-search-filters}

Les filtres de recherche vous permettent d’affiner les résultats de la recherche en fonction de divers paramètres tels que la date, le type de fichier, les balises et la pertinence, ce qui améliore la précision des requêtes. L’application de filtres vous permet de passer rapidement au crible les résultats les plus pertinents. Cela permet non seulement de gagner du temps, mais également d’améliorer l’expérience de recherche globale en adaptant les résultats aux préférences et besoins spécifiques.
En savoir plus sur la [recherche](search-assets-view.md).

Les filtres de recherche personnalisés ne peuvent être mappés qu’aux entrées de votre index de propriété indexable. Assurez-vous que toutes les métadonnées personnalisées sont incluses avant de configurer votre expérience de filtre personnalisé. [!DNL Assets view] permet de personnaliser les filtres de recherche pour rationaliser le processus de recherche. Pour personnaliser le modèle Filtres de recherche , procédez comme suit :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Paramètres généraux]**.
1. Accédez à l’onglet **[!UICONTROL Rechercher]**. Cliquez sur **[!UICONTROL Personnaliser]** pour configurer votre formulaire de recherche.

   ![paramètres de filtre de recherche personnalisée](assets/custom-search-filter.png)

1. Le formulaire [!UICONTROL  Configurer les filtres ] s’affiche. Assurez-vous d’être en mode d’édition afin de pouvoir apporter des modifications au modèle. Vous pouvez passer en [!UICONTROL mode Aperçu] pour afficher l’aperçu d’un formulaire de recherche existant.
1. Déposez des éléments de filtre du [filtres personnalisés](#available-custom-filters) sur la zone de travail. Vous pouvez faire glisser et déposer le composant pour le réorganiser si nécessaire.

   >[!VIDEO](https://video.tv.adobe.com/v/3443080)

1. Cliquez sur **[!UICONTROL Mode Aperçu]** pour passer en revue les modifications.
1. Cliquez sur **[!UICONTROL Confirmer]** pour enregistrer.

## Filtres personnalisés disponibles {#available-custom-filters}

La vue Assets fournit les filtres personnalisés suivants, reconfigurables en fonction des besoins :

* [Filtrer les éléments](#filter-elements)
* [Filtres préconfigurés](#preconfigured-filters)

### Filtrer les éléments {#filter-elements}

Vous pouvez utiliser une collection d’éléments de filtre sur la zone de travail des filtres de recherche personnalisés. Ces éléments sont reconfigurables en fonction de la convivialité des attributs de propriété de recherche. Cependant, vous pouvez personnaliser les [propriétés de filtre](#filter-properties) en fonction de vos besoins. Les éléments de filtre suivants sont disponibles dans [!DNL Assets view] :

<table>
    <tr>
        <th>Filtrer les éléments</th>
        <th>Description</th>
        <th>Propriétés</th>
    </tr>
    <tr>
        <td>Texte</td>
        <td>Un champ de texte est une zone de saisie dans laquelle vous pouvez saisir des informations relatives au filtre.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Valeurs
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Options</td>
        <td>Les options se rapportent aux alternatives disponibles pour sélectionner un élément préféré dans une liste.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Valeurs
                <li>Options
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Booléen</td>
        <td>Une valeur booléenne représente une valeur vraie. Il peut être utilisé lorsque vous souhaitez être spécifique pour choisir une option parmi d’autres.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Nombre</td>
        <td>Utilisez cet élément de filtre pour représenter une valeur numérique.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Procédure pas à pas
                <li>Valeur de procédure pas à pas
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Liste déroulante</td>
        <td>Pour effectuer un choix parmi les différentes options affichées dans une liste d’options.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Options
                <li>Valeurs
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Plage</td>
        <td>Utilisé pour spécifier la date.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Navigateur de chemins d’accès</td>
        <td>Permet de parcourir les fichiers ou dossiers du référentiel Experience Manager.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Explorateur de chemins d’accès
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Balises</td>
        <td>Permet de sélectionner des balises parmi les options disponibles. Les balises fournissent des informations plus spécifiques sur les ressources et améliorent leur visibilité. Les balises déjà appliquées aux ressources sélectionnées s’affichent dans le panneau <b>Propriétés</b>. Si vous stockez les balises sur une propriété de métadonnées personnalisée et que vous utilisez le chemin racine pour la restreindre à une hiérarchie, vous pouvez utiliser la même configuration dans vos filtres de recherche. Si vous ne trouvez pas les balises appropriées, créez-les et affectez-les aux ressources sélectionnées. Voir <a href = "tagging-management-assets-view.md"> Gestion des balises dans la vue Assets </a> pour plus d’informations sur la création et l’affectation de balises à des ressources.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Sélecteur de balises
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>User</td>
        <td>Utilisé pour spécifier le type d’utilisateur parmi les administrateurs, les utilisateurs réguliers et les consommateurs.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Description
            </ul>
        </td>
    </tr>
</table>

### Filtres préconfigurés {#preconfigured-filters}

Les filtres préconfigurés sont des paramètres prédéfinis qui vous permettent de les utiliser directement sur la zone de travail. Cependant, vous pouvez personnaliser les [propriétés de filtre](#filter-properties) en fonction de vos besoins. Les filtres suivants sont préconfigurés dans [!DNL Assets view] :

<table>
    <tr>
        <th>Filtres préconfigurés</th>
        <th>Description</th>
        <th>Propriétés</th>
    </tr>
    <tr>
        <td>Type de fichier</td>
        <td>Filtrez les résultats de la recherche selon les types de fichiers pris en charge : « Images », « Documents » et « Vidéos ».</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Options
                <li>Valeurs
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Format de fichier</td>
        <td>La vue Assets prend en charge tout format de fichier binaire avec les services de base, tels que le stockage, le chargement, la copie, le déplacement, la suppression et l’ajout de métadonnées.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Taille de l’image</td>
        <td>Fournissez une ou plusieurs des dimensions minimales et maximales pour filtrer les images. Les dimensions sont fournies en pixels et ne correspondent pas à la taille de fichier des images.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Procédure pas à pas
                <li>Valeur de procédure pas à pas
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Largeur de l’image</td>
        <td>Dimensions verticales d’une image.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Procédure pas à pas
                <li>Valeur de procédure pas à pas
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Hauteur de l’image</td>
        <td>Dimensions horizontales d’une image.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Procédure pas à pas
                <li>Valeur de procédure pas à pas
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Date de création</td>
        <td>Période de création des ressources.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Date de modification</td>
        <td>Période à laquelle les ressources ont été modifiées</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Statut de la ressource</td>
        <td>La vue Assets vous permet de définir le statut des ressources disponibles dans le référentiel. Définissez le statut d’une ressource pour mieux gouverner et gérer la consommation en aval des ressources numériques. Choisissez entre <b>Approuvé, Rejeté ou Aucun statut</b>.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Balises intelligentes</td>
        <td>Filtrage des ressources à l’aide de balises intelligentes ajoutées au référentiel Experience Manager.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Prise en charge des délimiteurs
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Statut Dynamic Media</td>
        <td>Choisissez le statut d’une ressource entre Publiée ou Dépubliée.</td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Options
                <li>Valeurs
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Date d’expiration</td>
        <td>Filtrez les ressources en spécifiant une période après laquelle les ressources ne sont plus valides ou nécessaires. </td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Type de sélection
                <li>Description
            </ul>
        </td>
    </tr>
    <tr>
        <td>Balises (taxonomie)</td>
        <td>Il s’agit d’un système d’organisation et de classification des ressources numériques à l’aide de balises, créant essentiellement une structure hiérarchique de mots-clés qui permet aux utilisateurs de rechercher et de trouver facilement du contenu pertinent en appliquant des balises spécifiques à chaque ressource. </td>
        <td>
            <ul>
                <li>Libellé
                <li>Métadonnées
                <li>Sélecteur de balises
                <li>Description
            </ul>
        </td>
    </tr>
</table>

#### Propriétés du filtre {#filter-properties}

Chaque élément de filtre est associé à un ensemble de propriétés. Les propriétés suivantes sont utilisées dans les éléments de filtre et préconfigurés :

<table>
    <tr>
        <th>Propriétés</th>
        <th>Valeurs</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>Libellé</td>
        <td>Texte</td>
        <td>Il s’agit de l’identifiant du filtre que vous utilisez.</td>
    </tr>
    <tr>
        <td>Métadonnées</td>
        <td>Liste déroulante</td>
        <td>La propriété de métadonnées est utilisée pour mapper des métadonnées approuvées à partir du référentiel Adobe Experience Manager Assets. Vous pouvez choisir la valeur de métadonnées dans le menu déroulant qui doit être mappée à l’élément de filtre. </td>
    </tr>
    <tr>
        <td>Type de sélection</td> 
        <td>Simple, Multiple, Exact ou Range </td>
        <td>
            <ul>
                <li>La <b>sélection unique</b> permet de choisir un élément à la fois, ce qui est idéal pour les choix distincts.
                <li>La <b>sélection multiple</b> permet de choisir plusieurs éléments simultanément, ce qui s’avère utile pour sélectionner plusieurs options. 
                <li><b>Sélection exacte</b> permet de choisir un élément précis parmi diverses options.
                <li><b>Sélection de plage</b> permet de choisir un ensemble continu de valeurs dans une plage définie, ce qui est utile pour sélectionner une plage de dates ou de valeurs numériques.
            </ul>
        </td>   
    </tr>
    <tr>
        <td>Options</td>
        <td>Manuelle, Chemin JSON ou Chargement CSV</td>
        <td>
            <ul>
                <li>Choisissez <b>Manuel</b> si vous souhaitez ajouter des options manuellement. 
                <li>Choisissez <b>Chemin JSON</b> pour ajouter des options à partir du fichier JSON. 
                <li>Choisissez <b>Chargement CSV</b> pour importer un fichier CSV contenant les valeurs à ajouter dans les options.
            </ul>
        </td>
    </tr>
    <tr>
       <td>Valeurs</td>
        <td>Ajouter ou modifier</td>
        <td>
        <ul>
        <li>Cliquez sur <b>ajouter</b> pour ajouter une nouvelle valeur. 
        <li>Cliquez sur <span>✎</span> pour modifier le libellé. 
        <li>Cliquez sur <img src="assets/do-not-localize/delete.svg"> pour supprimer la valeur de l’option. 
        <li>Cliquez sur <b>Modifier</b> pour modifier les options d’édition. 
        <li>Vous pouvez également modifier la séquence des options en les maintenant enfoncées.
        </td>
    </tr>
    <tr>
        <td>Prise en charge des délimiteurs</td>
        <td>Activer ou désactiver</td>
        <td>Un délimiteur est un symbole utilisé pour séparer des éléments distincts dans le texte. Par exemple, des virgules, des espaces ou des points-virgules.</td>
    </tr>
    <tr>
        <td>Procédure pas à pas</td>
        <td>Valeur</td>
        <td>Activez le bouton Procédure pas à pas sur le champ numérique pour incrémenter ou décrémenter la valeur à chaque clic. </td>
    </tr>
    <tr>
        <td>Valeur de procédure pas à pas </td>
        <td>Nombre</td>
        <td>Elle indique la valeur d’incrémentation/décrémentation lors de l’utilisation du bouton d’exécution pas à pas. Il s’affiche lorsque l’exécution pas à pas est activée.</td>
    </tr>
    <tr>
        <td>Description</td>
        <td>Texte</td>
        <td>Ajoutez une explication détaillée pour fournir des informations supplémentaires sur l’élément de filtre.</td>
    </tr>
</table>


## Supprimer un élément de filtre {#delete-a-filter-element}

Pour supprimer un filtre de recherche, procédez comme suit :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Paramètres généraux]**.
1. Accédez à l’onglet **[!UICONTROL Rechercher]**. Cliquez sur **[!UICONTROL Personnaliser]** pour configurer votre formulaire de recherche.
1. Le formulaire [!UICONTROL  Configurer les filtres ] s’affiche. Assurez-vous d’être en mode d’édition afin de pouvoir apporter des modifications au modèle.
1. Sélectionnez l’élément de filtre à supprimer. Sélectionnez par exemple **[!UICONTROL Hauteur de l’image]**.
1. Cliquez sur **[!UICONTROL Supprimer une catégorie]** pour supprimer l’élément de filtre. L’élément **[!UICONTROL Hauteur de l’image]** est supprimé de la zone de travail.
1. Cliquez sur **[!UICONTROL Confirmer]** pour enregistrer le formulaire.

## Utilisation de filtres de recherche personnalisés{#using-custom-search-filters}

Une fois les filtres de recherche configurés, vous pouvez les utiliser pour rechercher des ressources dans le référentiel.

![Utilisation de filtres de recherche personnalisés](assets/using-custom-search-filters.png)

>[!MORELIKETHIS]
>
>* [Recherche de ressources](search-assets-view.md)
