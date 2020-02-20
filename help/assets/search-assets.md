---
title: Recherche de ressources et d’images numériques dans AEM
description: Découvrez comment rechercher les ressources souhaitées dans AEM à l’aide du panneau Filtres et comment utiliser les ressources affichées dans la recherche.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 7141e42f53c556c0ac21def6085182ef400f5a71

---


# Recherche de ressources dans AEM {#search-assets-in-aem}

Vous pouvez obtenir une vitesse de contenu supérieure à l’aide des options conviviales de découverte de ressources dans Experience Manager. Vos équipes peuvent réduire le temps de commercialisation grâce à une expérience de recherche intelligente et transparente, grâce à la fonctionnalité prête à l&#39;emploi et aux méthodes personnalisées. La recherche de ressources est essentielle pour l’utilisation d’un système de gestion des ressources numériques, que ce soit pour une utilisation plus poussée par les créatifs, pour une gestion robuste des ressources par les utilisateurs et spécialistes du marketing ou pour l’administration par les administrateurs DAM. Les recherches simples, avancées et personnalisées que vous pouvez effectuer via l’interface utilisateur d’AEM Assets ou d’autres applications et surfaces permettent de répondre à ces cas d’utilisation.

AEM prend en charge les cas d’utilisation suivants. Cet article décrit l’utilisation, les concepts, les configurations, les limitations et le dépannage de ces cas d’utilisation.

| Recherche de ressources | Configuration et administration | Utilisation des résultats de recherche |
|--- |--- |--- |
| [Recherches de base](#searchbasics) | [Index de recherche](#searchindex) | [Trier les résultats](#sort) |
| [Comprendre l&#39;interface utilisateur de recherche](#searchui) |  | [Vérification des propriétés et des métadonnées d’un fichier](#checkinfo) |
| [Suggestions de recherche](#searchsuggestions) | [Métadonnées obligatoires](#mandatorymetadata) | [Téléchargement](#download) |
| [Comprendre les résultats et le comportement de la recherche](#searchbehavior) | [Modification des facettes de recherche](#searchfacets) | [Mises à jour des métadonnées en bloc](#metadataupdates) |
| [Classement et augmentation des recherches](#searchrank) | [Extraction de texte](#extracttextupload) | [Collections dynamiques](#collections) |
| [Recherche avancée : filtrage et portée de la recherche](#scope) | [Prédicats personnalisés](#custompredicates) | [Comprendre les résultats](#unexpectedresults) inattendus et [résoudre les problèmes](#troubleshoot) |
| [Rechercher à partir d’autres solutions et applications](#beyondomnisearch): Lien <br />de [ressource](#aal) Applicationde <br />[](#desktopapp) bureau <br />     Images [](#adobestock) Adobe Stock <br />     Fichiers [Contenu multimédia dynamique](#dynamicmedia) |  |  |
| [Sélecteur/sélecteur de ressources](#assetselector) |  |  |
| [Limites](#tips) et [conseils](#limitations) |  |  |
| [Exemples illustrés](#samples) |  |  |

Recherchez des ressources à l’aide du champ Omnisearch situé en haut de l’interface Web d’AEM. Accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]** dans AEM, cliquez sur ![icône_recherche](assets/do-not-localize/search_icon.png) dans la barre supérieure, entrez le mot-clé de recherche et appuyez sur Retour. Vous pouvez également utiliser le raccourci du mot-clé `/` (barre oblique) pour ouvrir le champ Omnisearch. `Location:Assets` est présélectionnée pour limiter les recherches aux ressources DAM. Vous pouvez effectuer des recherches avancées pour augmenter ou limiter la [portée de la recherche](#scope).

Use the **[!UICONTROL Filters]** panel to search for assets, folders, tags, and metadata. Vous pouvez filtrer les résultats de la recherche en fonction des différentes options (prédicats), telles que le type de fichier, la taille du fichier, la date de dernière modification, l’état du fichier, les données d’informations et les licences Adobe Stock. You can customize the Filters panel and add/remove search predicates using [search facets](/help/assets/search-facets.md).

La fonctionnalité de recherche AEM prend en charge la recherche de collections et la recherche de ressources dans une collection. Voir Collections [de](/help/assets/manage-collections.md)recherche.

## Comprendre l&#39;interface de recherche {#searchui}

Familiarisez-vous avec l&#39;interface de recherche et les actions disponibles.

![](assets/aem_search_results.png) Présentation des parties de l’interface *des résultats de la recherche Ressources* Figure : Présentation des parties de l’interface des résultats de la recherche Ressources

**** A. Enregistrez la recherche en tant que collection dynamique. **** B. Filtres (prédicats) pour limiter les résultats de la recherche. **C.** Afficher les fichiers, les dossiers ou les deux dans les résultats de la recherche. **** D. Cliquez sur Filtres pour ouvrir ou fermer le rail de gauche. **** E. L’emplacement de recherche est DAM. ************ F. Champ Omnisearch avec le mot-clé de recherche fourni par l’utilisateur **G. Cochez cette case pour sélectionner tous les résultats de recherche** H. Nombre de résultats de recherche affichés sur le total des résultats de recherche **I. Ferme la recherche** J. Basculer entre le mode Carte et le mode Liste

### Facettes de recherche dynamique {#dynamicfacets}

Vous pouvez découvrir plus rapidement les ressources de votre choix à partir de la page des résultats de recherche en utilisant le nombre de résultats de recherche attendus mis à jour dynamiquement dans les facettes de recherche. Le nombre prévu de ressources est mis à jour avant même d’appliquer le filtre de recherche. L’affichage du nombre prévu par rapport au filtre vous aide à parcourir rapidement et efficacement les résultats de la recherche. Pour plus d’informations, voir [Recherche de ressources dans AEM](/help/assets/search-assets.md).

![Affichage du nombre approximatif de ressources sans filtrer les résultats de la recherche dans les facettes de recherche.](assets/asset_search_results_in_facets_filters.png)

Affichage du nombre approximatif de ressources sans filtrer les résultats de la recherche dans les facettes de recherche.

## Search suggestions as you type {#searchsuggestions}

Lorsque vous commencez à saisir un mot-clé, AEM suggère les mots-clés ou expressions de recherche possibles. Les suggestions sont basées sur les ressources dans AEM. AEM indexe tous les champs de métadonnées pour faciliter la recherche. Pour fournir des suggestions de recherche, le système utilise les valeurs des quelques champs de métadonnées suivants. Pour fournir des suggestions de recherche, pensez à renseigner les champs suivants avec les mots-clés appropriés :

* Balises de ressources. (mappe vers `jcr:content/metadata/cq:tags`)
* Titre du fichier. (mappe vers `jcr:content/metadata/dc:title`)
* Description du fichier. (mappe vers `jcr:content/metadata/dc:description`)
* Titre dans le référentiel JCR. La valeur peut être mappée au titre du fichier. (mappe vers `jcr:content/jcr:title`)
* Description dans le référentiel JCR. La valeur peut être mappée à la description du fichier. (mappe vers `jcr:content/jcr:description`)

## Comprendre les résultats et le comportement de la recherche {#searchbehavior}

### Termes et résultats de recherche de base {#searchbasics}

Vous pouvez exécuter des recherches de mots-clés à partir du champ OmniSearch. La recherche de mots-clés n’est pas sensible à la casse et est une recherche en texte intégral (dans les champs de métadonnées courants). Si plusieurs mots-clés sont utilisés, `AND` est l&#39;opérateur par défaut entre les mots-clés. Les résultats sont triés par pertinence, en commençant par les correspondances les plus proches. Pour plusieurs mots-clés, les ressources qui contiennent les deux termes dans leurs métadonnées génèrent des résultats plus pertinents. Dans les métadonnées, les mots-clés qui apparaissent sous forme de balises actives sont classés plus haut que les mots-clés qui apparaissent dans d’autres champs de métadonnées.

AEM permet de donner plus de poids à un terme de recherche particulier. Il est également possible d’augmenter le classement de quelques ressources ciblées pour des termes de recherche spécifiques. Les administrateurs AEM peuvent effectuer ces configurations comme décrit ci-dessous.

Pour rechercher rapidement les ressources appropriées, l’interface riche fournit des mécanismes de filtrage, de tri et de sélection. Vous pouvez filtrer les résultats selon plusieurs critères et afficher le nombre de fichiers recherchés pour différents filtres. Vous pouvez également réexécuter la recherche en modifiant la requête dans le champ Omnisearch. Lorsque vous modifiez les termes ou filtres de recherche, les autres filtres restent appliqués pour préserver le contexte de la recherche.

Il arrive que des ressources inattendues apparaissent dans les résultats de la recherche. Pour plus d’informations, voir Résultats [](#unexpectedresults)inattendus.

AEM peut effectuer des recherches dans de nombreux formats de fichier et les filtres de recherche peuvent être personnalisés en fonction des besoins de votre entreprise. Contactez vos administrateurs pour savoir quelles options de recherche sont mises à disposition pour votre référentiel DAM et quelles restrictions votre connexion peut comporter.

<!-- 
### Results with and without Enhanced Smart Tags {#withsmarttags}

By default, AEM search combines the search terms with an AND clause. For example, consider searching for keywords woman running. Only the assets with both woman and running keywords in the metadata appear in the search results by default. The same behavior is retained when special characters (periods, underscores, or dashes) are used with the keywords. The following search queries return the same results:

* `woman running`
* `woman.running`
* `woman-running`

However, the query `woman -running` returns assets without `running` in their metadata.
Using smart tags adds an extra `OR` clause to find any of the search terms as the applied smart tags. An asset tagged with either `woman` or `running` using Smart Tags also appear in such a search query. So the search results are a combination of,

* Assets with `woman` and `running` keywords in the metadata (default behavior).

* Assets smart tagged with either of the keywords (Smart Tags behavior).
-->

### Classement et augmentation des recherches {#searchrank}

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche des balises dynamiques. Dans l’exemple ci-dessus, l’ordre approximatif de l’affichage des résultats de recherche est le suivant :

1. Matches of `woman running` in the various metadata fields.
1. Correspond à `woman running` dans les balises actives.
1. Matches of `woman` or of `running` in smart tags.

Vous pouvez améliorer la pertinence des mots-clés pour des ressources données afin d’améliorer les résultats de recherches basées sur ces mots-clés. En d’autres termes, les images pour lesquelles vous faites la promotion de mots-clés spécifiques apparaissent en haut des résultats lorsque vous lancez une recherche basée sur ces mots-clés.

1. Dans l’interface utilisateur Ressources, ouvrez la page des propriétés du fichier. Cliquez sur **[!UICONTROL Avancé]** et cliquez/appuyez sur **[!UICONTROL Ajouter]** sous **[!UICONTROL Elever pour rechercher des mots-clés]**.
1. Dans la boîte de dialogue **[!UICONTROL Rechercher une promotion]**, indiquez un mot-clé pour lequel vous souhaitez améliorer la recherche d’image puis cliquez/appuyez sur **[!UICONTROL Ajouter]**. Vous pouvez spécifier plusieurs mots-clés de la même manière.
1. Cliquez/appuyez sur **[!UICONTROL Enregistrer et fermer]**. La ressource que vous avez promue pour ce mot-clé apparaît parmi les principaux résultats de la recherche.

Vous pouvez l&#39;utiliser à votre avantage en augmentant le classement de certains fichiers dans les résultats de recherche du mot-clé ciblé. Voir l&#39;exemple de vidéo ci-dessous. For detailed info, see [search in AEM](https://helpx.adobe.com/experience-manager/kt/help/assets/search-feature-video-use.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Comprenez comment les résultats de la recherche sont classés et comment le classement peut être influencé.*

## Paramètres avancés {#scope}

AEM fournit diverses méthodes, telles que des filtres qui s’appliquent aux ressources recherchées, pour vous aider à localiser plus rapidement les ressources souhaitées. Quelques méthodes fréquemment utilisées sont décrites ci-dessous. Vous trouverez ci-dessous quelques exemples [](#samples) illustrés.

**Rechercher des fichiers ou des dossiers**: Dans les résultats de la recherche, voir fichiers, dossiers ou les deux. Dans le panneau **[!UICONTROL Filtres]** , vous pouvez sélectionner l’option appropriée. Voir Interface [de](#searchui)recherche.

**Rechercher des fichiers dans un dossier**: Vous pouvez limiter la recherche à un dossier spécifique. Dans le panneau **[!UICONTROL Filtres]** , ajoutez le chemin d’accès d’un dossier. Vous ne pouvez sélectionner qu’un seul dossier à la fois.

![Limiter les résultats de recherche à un dossier en ajoutant un chemin de dossier dans le panneau Filtres](assets/search_folder_select.gif)

Limiter les résultats de recherche à un dossier en ajoutant un chemin de dossier dans le panneau Filtres

<!--
### Find similar images {#visualsearch}

To find images that are visually similar to a user-selected image, click **[!UICONTROL Find Similar]** option from the card view of an image or from the toolbar. AEM displays the smart tagged images from the DAM repository that are similar to a user-selected image. See [how to configure similarity search](#configvisualsearch).

![Find similar images using the option in the card view](assets/search_find_similar.png)
*Figure: Find similar images using the option in the card view*
-->

### Images Adobe Stock {#adobestock}

From within the AEM user interface, users can search [Adobe Stock assets](/help/assets/aem-assets-adobe-stock.md) and license the required assets. Ajouter `Location: Adobe Stock` dans la barre d&#39;Omnisearch. Vous pouvez également utiliser le panneau Filtres pour rechercher toutes les ressources sous licence ou non sous licence ou effectuer des recherches dans une ressource spécifique à l’aide du numéro de fichier Adobe Stock.

### Fichiers de médias dynamiques {#dmassets}

Vous pouvez filtrer les images de médias dynamiques en sélectionnant Contenu multimédia **[!UICONTROL dynamique > Visionneuses]** dans le panneau **[!UICONTROL Filtres]** . Il filtre et affiche des fichiers tels que des visionneuses d’images, des carrousels, des visionneuses de supports variés et des visionneuses à 360°.

### Recherche à l’aide de valeurs spécifiques dans les champs de métadonnées {#gqlsearch}

Vous pouvez utiliser des fichiers en fonction des valeurs exactes de champs de métadonnées spécifiques, tels que le titre, la description et l’auteur. La fonction de recherche en texte intégral de GQL récupère uniquement les fichiers dont la valeur de métadonnées correspond exactement à votre requête de recherche. Les noms des propriétés (auteur, titre, etc.) et les valeurs sont sensibles à la casse.

| Champ de métadonnées | Valeur et utilisation des facettes |
|---|---|
| Titre | title:John |
| Créateur | creator:John |
| Emplacement | emplacement:NA |
| Description | description:&quot;Sample Image&quot; |
| Outil créateur | creatortool:&quot;Adobe Photoshop CC 2015&quot; |
| Détenteur de copyright | copyrightowner:&quot;Adobe Systems&quot; |
| Contributeur | contributor:John |
| Conditions d’utilisation | usageterms:&quot;CopyRights Reserved&quot; |
| Créé | created:AAAA-MM-JJTHH |
| Date d’expiration | expires:AAAA-MM-JJTHH |
| Heure d’activation | ontime:AAAA-MM-JJTHH |
| Heure de désactivation | offtime:AAAA-MM-JJTHH |
| Intervalle de temps (expires dateontime, offtime) | facet field : lowerboundupperbound |
| Chemin | /content/dam/&lt;nom_dossier> |
| Titre du PDF | pdftitle:&quot;Adobe Document&quot; |
| Objet | subject:&quot;Training&quot; |
| Balises | tags:&quot;Location And Travel&quot; |
| Type | type:&quot;image\png&quot; |
| Largeur de l’image | width:lowerboundupperbound |
| Hauteur de l’image | height:lowerboundupperbound |
| Personne | person:John |

Le chemin, la limite, la taille et l’ordre des propriétés ne peuvent pas être OUés avec une autre propriété.

Le mot-clé d’une propriété générée par un utilisateur correspond au libellé de son champ dans l’éditeur de propriétés en minuscules et sans espace.

Voici quelques exemples de formats de recherche pour des requêtes complexes :

* Pour afficher toutes les ressources avec plusieurs champs de facettes (par exemple : title=John Doe et creator tool=Adobe Photoshop) : `title:"John Doe" creatortool : Adobe*`
* To display all assets when the facets value is not a single word but a sentence (for example: title=Scott Reynolds): `title:"Scott Reynolds"`
* To display assets with multiple values of a single property (for example: title=Scott Reynolds or John Doe): `title:"Scott Reynolds" OR "John Doe"`
* To display assets with property values starting with a specific string (for example: title is Scott Reynolds): `title:Scott*`
* To display assets with property values ending with a specific string (for example: title is Scott Reynolds): `title:*Reynolds`
* To display assets with a property value that contains a specific string (for example: title = Basel Meeting Room): `title:*Meeting*`
* To display assets that contain a particular string and have a specific property value (for example: search for string Adobe in assets having title=John Doe): `*Adobe* title:"John Doe"`

## Recherche de ressources à partir d’autres offres ou interfaces AEM {#beyondomnisearch}

Adobe Experience Manager (AEM) connecte le référentiel DAM à diverses autres solutions AEM afin de fournir un accès plus rapide aux ressources numériques et de rationaliser les processus de création. Toute découverte de ressources commence par la navigation ou la recherche. Le comportement de recherche reste largement le même sur les différentes surfaces et solutions. Certaines méthodes de recherche changent lorsque le public cible, les cas d’utilisation et l’interface utilisateur varient d’une solution AEM à l’autre. Les méthodes spécifiques sont documentées pour les solutions individuelles dans les liens ci-dessous. Les conseils et comportements universellement applicables sont décrits dans cet article.

### Recherche de fichiers à partir du panneau Adobe Asset Link {#aal}

Grâce à Adobe Asset Link, les professionnels de la création peuvent désormais accéder au contenu stocké dans AEM Assets, sans quitter les applications Adobe Creative Cloud prises en charge. Les créatifs peuvent parcourir, rechercher, extraire et archiver facilement des ressources à l’aide du panneau intégré des applications Creative Cloud : Photoshop, Illustrator et InDesign. Asset Link permet également aux utilisateurs de rechercher des résultats visuellement similaires. Les résultats d’affichage de la recherche visuelle sont optimisés par les algorithmes d’apprentissage automatique d’Adobe Sensei et aident les utilisateurs à trouver des images esthétiques similaires. Reportez-vous à la page [Rechercher et parcourir des fichiers](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) à l’aide d’Adobe Asset Link.

### Recherche de fichiers dans l’application de bureau AEM {#desktopapp}

Les professionnels de la création utilisent l’application de bureau pour rendre les ressources AEM facilement consultables et disponibles sur leur bureau local (Windows ou Mac). Les créatifs peuvent facilement révéler les ressources souhaitées dans le Finder Mac ou l’Explorateur Windows, ouvertes dans les applications de bureau et modifiées localement - les modifications sont enregistrées dans AEM avec une nouvelle version créée dans le référentiel. L’application prend en charge les recherches de base à l’aide d’un ou de plusieurs mots-clés, * et ? caractères génériques et opérateur ET. Reportez-vous à la page [Navigation, recherche et aperçu des fichiers](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) dans l’application de bureau.

### Search assets in Brand Portal {#brandportal}

Les utilisateurs et les marketeurs du secteur d&#39;activité utilisent le portail de marque pour partager efficacement et en toute sécurité les ressources numériques approuvées avec leurs équipes internes étendues, partenaires et revendeurs. See [search assets on Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### Recherche d’images Adobe Stock {#adobestock-1}

Dans l’interface utilisateur AEM, les utilisateurs peuvent rechercher des ressources Adobe Stock et obtenir des licences pour les ressources requises. Ajouter `Location: Adobe Stock` dans le champ Omnisearch. Vous pouvez également utiliser le panneau **[!UICONTROL Filtres]** pour rechercher toutes les ressources sous licence ou non sous licence ou effectuer des recherches dans une ressource spécifique à l’aide du numéro de fichier Adobe Stock. Reportez-vous à la page [Gestion des images Adobe Stock dans AEM](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Recherche de fichiers Contenu multimédia dynamique {#dynamicmedia}

Vous pouvez filtrer les images de médias dynamiques en sélectionnant Contenu multimédia **[!UICONTROL dynamique]** > **[!UICONTROL Visionneuses]** dans le panneau **[!UICONTROL Filtres]** . Il filtre et affiche des fichiers tels que des visionneuses d’images, des carrousels, des visionneuses de supports variés et des visionneuses à 360°. Lors de la création de pages Web, les auteurs peuvent rechercher des visionneuses dans l’outil de recherche de contenu. Un filtre pour les visionneuses est disponible dans un menu contextuel.

### Recherche de fichiers dans Content Finder lors de la création de pages Web {#contentfinder}

Les auteurs peuvent utiliser l’outil de recherche de contenu pour rechercher dans le référentiel DAM les ressources appropriées et les utiliser dans les pages Web qu’ils créent.

<!-- Authors can also use the Connected Assets functionality to search for assets that are available on a remote AEM deployment. Authors can then use these assets in web pages on a local AEM deployment. See [use remote assets](use-assets-across-connected-assets-instances.md#use-remote-assets).
-->

### Rechercher des collections {#collections}

La fonctionnalité de recherche AEM prend en charge la recherche de collections et la recherche de ressources dans une collection. Voir Collections [de](/help/assets/manage-collections.md)recherche.

## Asset selector {#assetselector}

Le sélecteur de ressources vous permet de rechercher, filtrer et parcourir les ressources DAM d’une manière spéciale. Le sélecteur de ressources est disponible à l’adresse `https://[aem_server]:[port]/aem/assetpicker.html`. Vous pouvez récupérer les métadonnées des fichiers que vous sélectionnez à l’aide du sélecteur de fichiers. Vous pouvez le lancer avec les paramètres de requête pris en charge, tels que le type de fichier (image, vidéo, texte) et le mode de sélection (sélections simples ou multiples). Ces paramètres définissent le contexte du sélecteur de ressources pour une instance de recherche particulière et restent inchangés tout au long de la sélection.

The asset selector uses the HTML5 `Window.postMessage` message to send data for the selected asset to the recipient. Le sélecteur de ressources utilise le vocabulaire d’interface foundation picker de Granite. Par défaut, le sélecteur de ressources fonctionne en mode Navigation.

Vous pouvez transmettre les paramètres de requête suivants dans une URL pour démarrer le sélecteur de ressources dans un contexte spécifique :

| Nom | Valeurs | Exemple | Objectif |
|---|---|---|---|
| suffixe de la ressource (B) | Chemin d’accès au dossier indiqué comme suffixe de la ressource dans l’URL :[https://localhost:4502/aem/assetpicker.html/&lt;chemin_dossier>](https://localhost:4502/aem/assetpicker.html) | To launch the asset selector with a particular folder selected, for example with the folder /content/dam/we-retail/en/activities, selected, the URL should be of the form: [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | Si vous avez besoin de sélectionner un dossier en particulier au démarrage du sélecteur de ressources, vous pouvez l’indiquer comme suffixe de ressource. |
| mode | single, multiple | [https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single) | En mode multiple, vous pouvez sélectionner plusieurs ressources simultanément à l’aide du sélecteur de ressources. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) of an asset (wildcard also supported) | <ul><li>[https://localhost:4502/aem/assetpicker.html?mimetype=image/png](https://localhost:4502/aem/assetpicker.html?mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&mimetype=*png)</li></ul> | Utilisez-le pour filtrer les ressources basées sur le(s) type(s) de MIME |
| dialog | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Utilisez ces paramètres pour ouvrir le sélecteur de ressources sous forme de boîte de dialogue Granit. Cette option s’applique uniquement lorsque vous lancez le sélecteur de ressources via le champ Granite Path et que vous le configurez comme URL pickerSrc. |
| assettype (S) | images, documents, multimedia, archives | <ul><li>[https://localhost:4502/aem/assetpicker.html?assettype=images](https://localhost:4502/aem/assetpicker.html?assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=multimedia](https://localhost:4502/aem/assetpicker.html?assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=archives](https://localhost:4502/aem/assetpicker.html?assettype=archives)</li></ul> | Utilisez cette option pour filtrer les types de ressources en fonction de la valeur indiquée. |
| root | &lt;chemin_dossier> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&root=/content/dam/we-retail/en/activities) | Utilisez cette option pour spécifier le dossier racine du sélecteur de ressources. Ici, le sélecteur de ressources ne vous permet de sélectionner qu’une seule ressource enfant (directe/indirecte) sous le dossier racine. |

Pour accéder à l’interface du sélecteur de ressources, accédez à `https://[AEM server]:[port]/aem/assetpicker`. Recherchez le dossier souhaité, puis sélectionnez une ou plusieurs ressources. Vous pouvez également rechercher le fichier souhaité dans la zone Omnisearch, appliquer le filtre suivant vos besoins, puis le sélectionner.

![Parcourir et sélectionner un fichier dans le sélecteur de ressources](assets/assetpicker.png)

Parcourir et sélectionner un fichier dans le sélecteur de ressources

## Restrictions {#limitations}

La fonctionnalité de recherche dans AEM Assets présente les limites suivantes :

* N&#39;entrez pas d&#39;espace de début dans la requête de recherche, sinon la recherche ne fonctionne pas.
* AEM peut continuer à afficher le terme de recherche une fois que vous avez sélectionné les propriétés d’un fichier à partir des résultats recherchés, puis annuler la recherche (CQ-4273540).
* Lors de la recherche de dossiers ou de fichiers et de dossiers, les résultats de la recherche ne peuvent être triés sur aucun paramètre.
* Si vous appuyez sur Entrée sans lier quoi que ce soit dans la barre Omnisearch, AEM renvoie une liste de fichiers uniquement et non de dossiers. Si vous recherchez spécifiquement des dossiers sans utiliser de mot-clé, AEM ne renvoie aucun résultat.

La recherche visuelle ou par analogie présente les limites suivantes :

* La recherche visuelle fonctionne mieux avec des référentiels plus volumineux. Bien qu’il n’y ait pas de nombre minimum d’images requis pour obtenir de bons résultats, la qualité des correspondances avec quelques images peut ne pas être aussi bonne que les correspondances d’un grand référentiel.
* Vous ne pouvez pas modifier le modèle ni entraîner AEM à rechercher des images similaires. Par exemple, l’ajout ou la suppression de balises actives dans quelques ressources ne modifie pas le modèle. Les ressources sont exclues des résultats de recherche visuellement similaires.

## Conseils de recherche {#tips}

* Si vous surveillez l’état de révision des ressources, utilisez l’option appropriée pour trouver les ressources qui sont approuvées ou en attente d’approbation.
* Utilisez le prédicat Statistiques pour rechercher les ressources prises en charge en fonction de leurs statistiques d’utilisation obtenues auprès de diverses applications Creative. Les données d’utilisation sont regroupées sous le score d’utilisation, les impressions, les clics et les canaux de médias où les ressources apparaissent dans des catégories.
* Utilisez cette case à cocher pour sélectionner tous les résultats de recherche ou les résultats de recherche filtrés à appliquer à la sélection. Il sélectionne tous les fichiers recherchés, quel que soit le nombre de fichiers affichés dans la vue utilisateur actuelle. Par exemple, vous pouvez télécharger tous les fichiers sélectionnés, mettre à jour les propriétés de métadonnées en bloc pour tous les fichiers sélectionnés ou ajouter les fichiers sélectionnés à une collection.
* Pour rechercher des fichiers qui ne contiennent pas les métadonnées obligatoires, voir Métadonnées [](#mandatorymetadata)obligatoires.
* La recherche utilise tous les champs de métadonnées. Une recherche générique, telle que la recherche de 12, renvoie généralement de nombreux résultats. Pour de meilleurs résultats, utilisez des guillemets doubles (et non des guillemets simples) ou assurez-vous que le nombre est contigu à un mot sans caractère spécial (par exemple, *shoe12*).
* La recherche de texte intégral prend en charge des opérateurs tels que -, ^, etc. Pour rechercher des informations sous forme de chaînes littérales, indiquez la phrase de recherche entre guillemets. Par exemple, utilisez &quot;Notebook - Beauty&quot; au lieu de &quot;Notebook - Beauty&quot;.
* Si les résultats de la recherche sont trop nombreux, limitez la [portée de la recherche](#scope) à zéro dans les ressources souhaitées. Il fonctionne mieux lorsque vous avez une idée de la meilleure manière de rechercher les ressources souhaitées, par exemple un type de fichier spécifique, un emplacement spécifique, des métadonnées spécifiques, etc.

* **Balisage**: Les balises permettent de classer les fichiers qui peuvent être parcourus et recherchés plus efficacement. Le balisage permet de propager la taxonomie appropriée à d’autres utilisateurs et processus. AEM propose des méthodes pour baliser automatiquement les ressources à l’aide des services intelligents artificiels d’Adobe Sensei, qui améliorent constamment le balisage de vos ressources avec l’utilisation et la formation. Lorsque vous recherchez des fichiers, les balises actives sont prises en compte si la fonction est activée sur votre compte. Il fonctionne avec la fonctionnalité de recherche intégrée. Voir Comportement [de la](#searchbehavior)recherche. Pour optimiser l’ordre d’affichage des résultats de recherche, vous pouvez [augmenter le classement](#searchrank) de quelques ressources sélectionnées.

* **Indexation**: Seules les métadonnées et les ressources indexées sont renvoyées dans les résultats de la recherche. Pour une meilleure couverture et de meilleures performances, veillez à une indexation appropriée et suivez les bonnes pratiques. Voir [indexation](#searchindex).

## Quelques exemples illustrant la recherche {#samples}

Utilisez des guillemets doubles autour des mots-clés pour rechercher des fichiers contenant exactement l’expression dans l’ordre spécifié par l’utilisateur.

![Comportement de recherche avec et sans guillemets](assets/search_with_quotes.gif)

Comportement de recherche avec et sans guillemets

**Rechercher avec un caractère générique** astérisque : Pour élargir la recherche, utilisez un astérisque avant ou après le mot recherché pour faire correspondre n’importe quel nombre de caractères. Par exemple, la recherche d’une exécution sans astérisque ne renvoie pas de fichiers contenant une variante du mot (y compris dans les métadonnées). Un astérisque remplace tout nombre de caractères. Par exemple :

* `run` renvoie des fichiers avec un mot-clé à exécution exacte
* `run*` renvoie des fichiers avec exécution, exécution, exécution, etc.
* `*run` renvoie oups, une nouvelle exécution, etc.
* `*run*` renvoie toutes les combinaisons possibles.

![Illustration de l’utilisation d’un caractère générique astérisque dans la recherche de ressources à l’aide d’un exemple](assets/search_with_asterisk_run.gif)

Illustration de l’utilisation d’un caractère générique astérisque dans la recherche de ressources à l’aide d’un exemple

**Rechercher avec un caractère générique** de point d’interrogation : Pour élargir la recherche, utilisez un ou plusieurs &quot;?&quot; pour correspondre au nombre exact de caractères. Par exemple, dans l’illustration suivante,

* `run???` ne correspond à aucun fichier.

* `run????` correspond au mot `running` à quatre caractères après `run`.

* `??run` correspond au mot `rerun` avec deux caractères avant `run`.

![Illustration de l’utilisation du caractère générique de point d’interrogation dans la recherche de ressources à l’aide d’un exemple](assets/search_with_questionmark_run.gif)

Illustration de l’utilisation du caractère générique de point d’interrogation dans la recherche de ressources à l’aide d’un exemple

**Exclure un mot-clé**: Utilisez le tiret pour rechercher des fichiers qui ne contiennent pas de mot-clé. Par exemple, `running -shoe` la requête renvoie les fichiers qui contiennent `running`, mais pas `shoe`. De même, `camp -night` la requête renvoie les fichiers qui contiennent `camp` mais pas `night`. Notez que `camp-night` la requête renvoie des fichiers qui contiennent à la fois `camp` et `night`.

![Utilisation du tiret pour rechercher des fichiers ne contenant pas de mot-clé](assets/search_dash_exclude_keyword.gif)exclu *Figure :Utilisation du tiret pour rechercher des fichiers ne contenant pas de mot-clé exclu*

<!--
## Configuration and administration tasks related to search functionality {#configadmin}

### Search index configurations {#searchindex}

Asset discovery relies on indexing of DAM contents, including the metadata. Faster and accurate asset discovery relies on optimized indexing and appropriate configurations. See [indexing](/help/operations/indexing.md).

### Sort on Name column {#sortbyname}

In list view, you can sort the search results just as you can sort assets in any folder. Sorting does not work on the `Name` column by default. To sort by the `Name` column, overlay `/libs/dam/gui/content/commons/availablecolumns` and change the value of sortable to `True`.

<!--
### Visual or similarity search {#configvisualsearch}

Visual search uses smart tagging and requires AEM 6.5.2.0 or later. After configuring smart tagging functionality, follow these steps.

1. In AEM CRXDE, in `/oak:index/lucene` node, add the following properties and values and save the changes.

    * `costPerEntry` property of type `Double` with the value `10`.

    * `costPerExecution` property of type `Double` with the value `2`.

    * `refresh` property of type `Boolean` with the value `true`.

   This configuration allows searches from the appropriate index.

1. To create Lucene index, in CRXDE, at `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`, create node named `imageFeatures` of type `nt-unstructured`. In `imageFeatures` node,

    * Add `name` property of type `String` with the value `jcr:content/metadata/imageFeatures/haystack0`.

    * Add `nodeScopeIndex` property of type `Boolean` with the value of `true`.

    * Add `propertyIndex` property of type `Boolean` with the value of `true`.

    * Add `useInSimilarity` property of type `Boolean` with the value `true`.

   Save the changes.

1. Access `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` and add `similarityTags` property of type `Boolean` with the value of `true`.
1. Apply Smart Tags to the assets in your AEM repository. See [how to configure smart tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html).
1. In CRXDE, in `/oak-index/damAssetLucene` node, set the `reindex` property to `true`. Save the changes.
1. (Optional) If you have customized search form then copy the `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` node to `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Save all the changes.

For related information, see [understand smart tags in AEM](https://helpx.adobe.com/experience-manager/kt/help/assets/smart-tags-feature-video-understand.html) and [how to manage smart tags](/help/assets/smart-tags.md).

-->
<!--

### Mandatory metadata {#mandatorymetadata}

Business users, administrators, or DAM librarians can define some metadata as mandatory metadata that is a must for the business processes to work. For various reasons, some assets may be missing this metadata, such as legacy assets or assets migrated in bulk. Assets with missing or invalid metadata are detected and reported based on the indexed metadata property. To configure it, see [mandatory metadata](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

### Modify search facets {#searchfacets}

To improve the speed of discovery, AEM Assets offers search facets using which you can filter the search results. The Filters panel includes a few standard facets by default. Administrators can customize the Filters panel to modify the default facets using the in-built predicates. AEM provides a good collection of in-built predicates and an editor to customize the facets. See [search facets](/help/assets/search-facets.md).

### Extract text when uploading assets {#extracttextupload}

You can configure AEM to extract the text from the assets when users upload assets, such as PSD or PDF files. AEM indexes the extracted text and helps users search these assets based on the extracted text. See [upload assets](/help/assets/manage-digital-assets.md#uploading-assets).

<!-- Check with gklebus if this customization is possible in Cloud Service now

### Custom predicates to filter search results {#custompredicates}

Predicates are used to create facets. Administrators can customize the search facets in the Filters panel using pre-configured predicates. These predicates can be customized using overlays. See [create custom predicates](/help/assets/searchx.md).

You can search for digital assets based on one or more of the following properties. Filters that apply on some of these properties are available by default and some other filters can be custom-created to apply on the other properties.

| Search field | Search property values |
|---|---|
| MIME Types | Images, Documents, Multimedia, Archives, or Other. |
| Last Modified | Hour, Day, Week, Month, or Year. |
| File Size | Small, Medium, or Large. |
| Publish Status | Published or Unpublished. |
| Approved Status | Approved or Rejected. |
| Orientation | Horizontal, Vertical, or Square. |
| Style | Color, or Black & White. |
| Video Height | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Width | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Format | DVI, Flash, MPEG4, MPEG, OGG Theora, QuickTime, Windows Media. Value is stored in the metadata of the source video and any renditions. |
| Video Codec | x264. Value is stored in the metadata of video renditions only. |
| Video Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Audio Codec | Libvorbis, Lame MP3, AAC Encoding. Value is stored in the metadata of video renditions only. |
| Audio Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |

-->

## Utilisation des résultats de recherche de ressources {#aftersearch}

Une fois que vous avez vu des fichiers recherchés qui correspondent à vos critères, vous pouvez exécuter les tâches standard suivantes avec ou exécuter les actions suivantes sur ces résultats de recherche :

* Affichez les propriétés de métadonnées et d’autres informations.
* Téléchargez un ou plusieurs fichiers.
* Utilisez les actions de bureau pour ouvrir ces ressources dans l’application de bureau.
* Créez des collections dynamiques.

### Trier les résultats recherchés {#sort}

Le tri des résultats de recherche vous permet de découvrir plus rapidement les ressources requises. Le tri des résultats de la recherche fonctionne en mode Liste et uniquement lorsque vous sélectionnez **[!UICONTROL [Fichiers](#searchui)]**dans le panneau**[!UICONTROL  Filtres ]**. AEM Assets utilise le tri côté serveur pour trier rapidement toutes les ressources (quel que soit leur nombre) dans un dossier ou les résultats d’une requête de recherche. Le tri côté serveur fournit des résultats plus rapides et plus précis que le tri côté client.

En mode Liste, vous pouvez trier les résultats de la recherche tout comme vous pouvez trier les fichiers de n’importe quel dossier. Le tri fonctionne sur ces colonnes : Titre, État, Dimensions, Taille, Évaluation, Utilisation, (Date) Modifiée, (Date) Publiée, Processus et Extrait.

Voir [Configuration du tri sur la colonne](#sortbyname)Nom. Pour les limitations de la fonctionnalité de tri, voir [Limites](#limitations).

### Vérification des informations détaillées d’un fichier {#checkinfo}

Vous pouvez vérifier les informations détaillées d’une ressource recherchée à partir de la page des résultats de la recherche.

Pour afficher toutes les métadonnées d’un fichier, sélectionnez-le, puis cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils.

Pour vérifier les commentaires sur l’historique d’un fichier ou d’une version d’un fichier, cliquez sur le fichier pour ouvrir un aperçu de grande taille. Ouvrez la chronologie dans le rail de gauche et sélectionnez **[!UICONTROL Commentaires]** ou **[!UICONTROL Versions]**. Vous pouvez également trier l’activité de la chronologie comme les commentaires ou les versions dans un ordre chronologique.

![Tri des entrées de chronologie pour un fichier de recherche](assets/sort_timeline_search_results.gif)

Tri des entrées de chronologie pour un fichier de recherche

### Téléchargement de fichiers recherchés {#download}

Vous pouvez télécharger les fichiers recherchés et leurs rendus au fur et à mesure que vous téléchargez des fichiers ordinaires à partir de dossiers. Sélectionnez un ou plusieurs fichiers dans les résultats de la recherche, puis cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils.

### Propriétés des métadonnées de mise à jour en masse {#metadataupdates}

Il est possible d’effectuer des mises à jour en masse des champs de métadonnées courants de plusieurs fichiers. Dans les résultats de la recherche, sélectionnez un ou plusieurs fichiers. Cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils et mettez à jour les métadonnées selon les besoins. Cliquez sur **[!UICONTROL Enregistrer et fermer]** lorsque vous avez terminé. Les métadonnées précédemment existantes dans les champs mis à jour sont remplacées.

Pour les fichiers disponibles dans un dossier unique ou une collection, il est plus facile de [mettre à jour les métadonnées en bloc](/help/assets/manage-metadata.md#manage-assets-metadata). Pour les fichiers disponibles dans plusieurs dossiers ou qui correspondent à un critère commun, il est plus rapide de mettre à jour les métadonnées en masse par le biais de la recherche.

### Collections dynamiques {#collections-1}

Une collection est un ensemble ordonné de ressources pouvant inclure des ressources provenant de différents emplacements, car les collections ne contiennent que des références à ces ressources. Les collections sont de deux types :

* Liste de référence statique de ressources, de dossiers et d’autres collections.
* Liste dynamique (collection dynamique) qui renseigne les fichiers de la collection en fonction de critères de recherche.

Vous pouvez créer des collections dynamiques en fonction des critères de recherche. Dans le panneau **[!UICONTROL Filtres]** , sélectionnez **[!UICONTROL Fichiers]** et cliquez sur **[!UICONTROL Enregistrer la collection]** dynamique. Voir [Gestion des collections](/help/assets/manage-collections.md).

## Résultats de recherche inattendus {#unexpectedresults}

**Rechercher les métadonnées** manquantes : Lors de la recherche de fichiers qui ne contiennent pas les métadonnées obligatoires, AEM peut afficher certains fichiers qui possèdent des métadonnées valides. Les métadonnées manquantes sont détectées et rapportées en fonction de la propriété de métadonnées indexées. Même si les métadonnées des fichiers sont fixes, elles continuent à s’afficher comme des métadonnées manquantes jusqu’à ce que la réindexation se produise. Voir Métadonnées [](/help/assets/metadata-schemas.md#defining-mandatory-metadata)obligatoires.

**Trop de résultats** de recherche : Pour éviter d&#39;obtenir trop de résultats de recherche, pensez à limiter les résultats de recherche. Par exemple, pour rechercher des ressources dans DAM, sélectionnez `Location:Assets` dans la barre de recherche Omniture. Pour plus de filtres de recherche, voir [portée de la recherche](#scope).

<!-- Another reason to get more than expected search results can be use of smarts tags. See [search behavior with smart tags](#withsmarttags). 
-->

<!--
**Partially related or unrelated search results**: AEM may display seemingly partially related or unrelated assets, alongside the desired assets in the search results. If you enable Enhanced Smart Tags, the search behavior changes slightly. See how it changes [after smart tagging](#withsmarttags).
-->

**Aucune suggestion de saisie semi-automatique pour les fichiers** nouvellement transférés : Les métadonnées (titres, balises, etc.) des ressources récemment transférées ne sont pas immédiatement disponibles en tant que suggestions lorsque vous commencez à saisir un mot-clé de recherche dans la barre d&#39;Omnisearch. AEM Assets attend l’expiration d’un délai d’expiration (une heure par défaut) avant d’exécuter une tâche d’arrière-plan afin d’indexer les métadonnées pour tous les fichiers nouvellement téléchargés ou mis à jour, puis ajoute les métadonnées à la liste des suggestions.

**Aucun résultat** de recherche : Si AEM affiche une page vide pour une requête de recherche, les raisons suivantes peuvent être invoquées :

* Il n’existe aucun fichier correspondant à votre requête.
* Vous ajoutez un espace blanc avant la requête de recherche. C&#39;est une limitation [connue](#limitations).

* Un champ de métadonnées non pris en charge contient le mot-clé que vous recherchez. Tous les champs de métadonnées ne sont pas pris en compte pour les recherches. Voir [scope](#scope).
* L’heure d’activation et de désactivation est configurée pour le fichier et la recherche a été effectuée pendant l’heure d’arrêt du fichier.

**Le filtre/prédicat de recherche n&#39;est pas disponible**: Si une personnalisation attendue des filtres de recherche n’est pas disponible dans l’interface utilisateur, contactez votre administrateur pour vérifier si la personnalisation a été implémentée pour tous les auteurs et sur le serveur de production que vous utilisez. Il est possible que la configuration soit incorrecte.

## Résolution des problèmes liés à la recherche {#troubleshoot}

Voir ci-dessous les problèmes et les mesures possibles :

* Si un filtre/prédicat de recherche attendu n’est pas visible, contactez votre administrateur.
* Lorsque vous recherchez des images visuellement similaires, il arrive qu’une image attendue ne figure pas dans les résultats de la recherche. Vérifiez si ces ressources sont indexées et balisées de manière intelligente.
* Lors de la recherche d’images visuellement similaires, il arrive qu’une image apparemment sans pertinence s’affiche dans les résultats de la recherche. AEM affiche autant de ressources potentiellement pertinentes que possible. Les images moins pertinentes, le cas échéant, sont ajoutées aux résultats, mais avec un classement de recherche inférieur. La qualité des correspondances et la pertinence des ressources recherchées diminuent lorsque vous faites défiler les résultats de la recherche.
