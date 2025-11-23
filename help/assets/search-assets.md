---
title: Comment rechercher des ressources dans AEM ?
description: Découvrez comment rechercher des ressources dans AEM à l’aide du panneau Filtres et comment utiliser les ressources affichées dans la recherche.
contentOwner: AG
mini-toc-levels: 1
feature: Selectors, Adobe Stock, Asset Distribution, Asset Management, Asset Processing
role: User, Admin
exl-id: 68bdaf25-cbd4-47b3-8e19-547c32555730
source-git-commit: 32bc8ba2a7e7a783b3e816c78873c6a8c559c1a1
workflow-type: tm+mt
source-wordcount: '5969'
ht-degree: 85%

---


# Rechercher des ressources dans AEM {#search-assets-in-aem}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/search-assets.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

[!DNL Adobe Experience Manager Assets] fournit des méthodes robustes de découverte de ressources qui vous aident à atteindre une vitesse de contenu plus élevée. Vos équipes peuvent réduire les délais de mise sur le marché grâce à une expérience de recherche des ressources intelligente et transparente basées sur des fonctionnalités prêtes à l’emploi et des méthodes personnalisées. La recherche de ressources est essentielle pour l’utilisation d’un système de gestion des ressources numériques, que ce soit pour une utilisation plus poussée par les rédacteurs et les rédactrices, pour une gestion robuste des ressources par les utilisateurs/utilisatrices et les spécialistes marketing ou encore pour l’administration par les administrateurs et administratrices DAM. Les recherches simples, avancées et personnalisées que vous pouvez effectuer via l’interface utilisateur [!DNL Assets] ou d’autres applications et surfaces permettent de répondre à ces cas d’utilisation.

La recherche de ressources dans AEM prend en charge les cas d’utilisation suivants, dont cet article décrit l’utilisation, les concepts, les configurations, les limitations et le dépannage.

| Rechercher des ressources | Configurer et administratrer la fonctionnalité de recherche | Utiliser les résultats de recherche de ressources |
|---|---|---|
| [Recherches de base](#searchbasics) | [Index de recherche](#searchindex) | [Tri des résultats](#sort) |
| [Présentation de l’interface utilisateur de recherche](#searchui) | [Extraction de texte](#extracttextupload) | [Vérification des propriétés et des métadonnées d’une ressource](#checkinfo) |
| [Suggestions de recherche](#searchsuggestions) | [Métadonnées obligatoires](#mandatorymetadata) | [Téléchargement](#download) |
| [Présentation des résultats de recherche et du comportement](#searchbehavior) | [Modification des facettes de recherche](#searchfacets) | [Mises à jour des métadonnées en masse](#metadata-updates) |
| [Classement et amplification des recherches](#searchrank) | [Prédicats personnalisés](#custompredicates) | [Collections dynamiques](#collections) |
| [Recherche avancée : filtrage et portée de la recherche](#scope) | | [Explication et résolution des problèmes liés aux résultats inattendus](#unexpected-results) |
| [Recherche à partir d’autres solutions et applications](#search-assets-other-surfaces) :<ul><li>[Adobe Asset Link](#aal)</li><li>[Brand Portal](#brand-portal)</li><li>[Application de bureau Experience Manager](#desktop-app)</li><li>[Images Adobe Stock](#adobe-stock)</li><li>[Ressources Dynamic Media](#search-dynamic-media-assets)</li></ul> | | |
| [Sélecteur de ressources](#asset-picker) | | |
| [Limites](#limitations) et [conseils](#tips) | | |
| [Exemples illustrés](#samples) | | |

Recherchez des ressources à l’aide du champ Omni-recherche situé en haut de l’interface web [!DNL Experience Manager]. Accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]** dans [!DNL Experience Manager], cliquez sur ![icône_recherche](assets/do-not-localize/search_icon.png) dans la barre supérieure, entrez le mot-clé de recherche et sélectionnez `Return`. Vous pouvez également utiliser le raccourci `/` (barre oblique) pour ouvrir le champ Omni-recherche. `Location:Assets` est présélectionné afin de limiter les recherches aux ressources de la gestion des ressources numériques. `Path:/content/dam` s’affiche également lorsque vous effectuez une recherche au niveau racine dans le dossier **[!UICONTROL Fichiers]**. Si vous accédez à un autre dossier, `Path:/content/dam/<folder name>` s’affiche dans le champ Omnisearch pour limiter la portée de la recherche au dossier actif. [!DNL Experience Manager] fournit des suggestions lorsque vous commencez à saisir un mot-clé de recherche.

Utilisez le panneau **[!UICONTROL Filtres]** pour rechercher des ressources, des dossiers, des balises et des métadonnées. Vous pouvez filtrer les résultats de recherche en fonction des différentes options (prédicats), telles que le type et la taille de fichier, la date de dernière modification, l’état de la ressource, les données d&#39;aperçu et les licences Adobe Stock. Vous pouvez personnaliser le panneau Filtres et ajouter ou supprimer des prédicats de recherche à l’aide des [facettes de recherche](/help/assets/search-facets.md). Le filtre [!UICONTROL Type de fichier] du panneau [!UICONTROL Filtres] comporte des cases à cocher à états mixtes. Les cases à cocher du premier niveau sont donc partiellement cochées à moins que vous ne sélectionniez tous les prédicats (ou formats) imbriqués.

La fonctionnalité de recherche [!DNL Experience Manager] prend en charge la recherche de collections et la recherche de ressources dans une collection. Voir [Recherche de collections](/help/assets/manage-collections.md).

## Comprendre l’interface de recherche des ressources {#searchui}

Familiarisez-vous avec l’interface de recherche des ressources et les actions disponibles.
<!--
![Understand Experience Manager Assets search results interface](assets/aem_search_results.png)
-->
![Présentation de l’interface des résultats de recherche de Experience Manager Assets](assets/aem-search-interface.png)
*Image : présentation de [!DNL Experience Manager Assets]’interface des résultats de recherche.*

**A.** Enregistrer la recherche en tant que collection dynamique.
**B.** Filtre ou prédicat pour limiter les résultats de la recherche.
**C.** Afficher des fichiers, des dossiers ou les deux.
**D.** L’emplacement de la recherche est DAM.
**Par Exemple** Accéder Aux Recherches Enregistrées.
**F.** Cliquez sur Filtres pour ouvrir ou fermer le rail de gauche.
**Par exemple** affiche Assets comme recherche par défaut.
**H.** L’emplacement de la recherche est DAM.
**I.** Champ Omnisearch avec mot-clé de recherche fourni par l’utilisateur.
**J.** Sélectionnez les résultats de recherche chargés.
**K.** Trier par Créé, Modifié, Nom, Aucun.
**L.** Triez par ordre croissant ou décroissant.
**M.** Nombre de résultats de recherche affichés sur le total des résultats de recherche. **N.** Fermer la recherche.
**O.** Basculer entre les vues Carte et Liste.

### Facettes de recherche dynamique {#dynamicfacets}

Vous pouvez découvrir plus rapidement les ressources souhaitées à partir de la page de résultats de la recherche à l’aide du nombre de résultats de recherche attendus mis à jour dynamiquement dans les facettes de recherche. Le nombre de ressources attendu est mis à jour avant l’application du filtre de recherche. L’affichage du nombre prévu par rapport au filtre vous aide à parcourir rapidement et efficacement les résultats de la recherche.

![Affichage du nombre approximatif de ressources sans filtrer les résultats de la recherche dans les facettes de recherche.](assets/asset_search_results_in_facets_filters.png)

*Figure : Affichage du nombre approximatif de ressources sans filtrer les résultats de la recherche dans les facettes de recherche.*

Par défaut, Experience Manager Assets affiche le nombre de facettes pour deux propriétés :

* Type de ressource (jcr:content/metadata/dc:format)

* Statut d’approbation (jcr:content/metadata/dam:status)

Depuis août 2023, Experience Manager Assets comprend une nouvelle version 9 de l’index `damAssetLucene`. Les versions précédentes, `damAssetLucene-8` et ultérieures, utilisent le mode `statistical` pour vérifier le contrôle d’accès sur un échantillon d’éléments pour chaque nombre de facettes de recherche.

`damAssetLucene-9` modifie le comportement du comptage des facettes de requête d’Oak afin de ne plus évaluer le contrôle d’accès sur les nombres de facettes renvoyés par l’index de recherche sous-jacent, ce qui accélère les temps de réponse de la recherche. Par conséquent, les utilisateurs peuvent se voir présenter des valeurs de nombre de facettes, qui incluent des ressources auxquelles ils n’ont pas accès. Ces utilisateurs ne peuvent pas accéder à ces ressources, les télécharger ni en lire d’autres détails, y compris leurs chemins d’accès, ni obtenir d’autres informations à leur sujet.

Si vous devez passer au comportement précédent (mode `statistical`), consultez la section [Recherche et indexation de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=fr) pour créer une version personnalisée de l’index `damAssetLucene-9`. Adobe ne recommande pas de passer en mode `secure` en raison de l’impact sur les temps de réponse de la recherche avec des jeux de résultats volumineux.

Pour plus d’informations sur les fonctionnalités des facettes d’Oak, y compris une description détaillée de ces modes, voir [Facettes - Documentation d’Oak - Index Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html#facets).

## Suggestions de recherche en cours de frappe {#searchsuggestions}

Lorsque vous commencez à saisir un mot-clé, Experience Manager suggère les mots-clés ou expressions de recherche possibles. Les suggestions sont basées sur les ressources dans Experience Manager. Experience Manager indexe tous les champs de métadonnées pour faciliter la recherche. Pour fournir des suggestions de recherche, le système utilise les valeurs des quelques champs de métadonnées suivants. Pour fournir des suggestions de recherche, pensez à renseigner les champs suivants avec les mots-clés appropriés :

* Balises de ressources. (mappage avec `jcr:content/metadata/cq:tags`)
* Titre de la ressource. (mappage avec `jcr:content/metadata/dc:title`)
* Description de la ressource. (mappage avec `jcr:content/metadata/dc:description`)
* Titre dans le référentiel JCR. La valeur peut être mappée au titre de la ressource. (mappage avec `jcr:content/jcr:title`)
* Description dans le référentiel JCR. La valeur peut être mappée à la description de la ressource. (mappage avec `jcr:content/jcr:description`)

## Présentation des résultats de recherche et du comportement {#searchbehavior}

### Termes et résultats de recherche de base {#searchbasics}

Vous pouvez exécuter des recherches de mots-clés à partir du champ Omni-recherche. La recherche de mots-clés n’est pas sensible à la casse et il s’agit d’une recherche en texte intégral (dans les champs de métadonnées courants). Si plusieurs mots-clés sont utilisés, `AND` est l’opérateur par défaut entre les mots-clés.

Les résultats sont triés par pertinence, en commençant par les correspondances les plus proches. Pour plusieurs mots-clés, les ressources qui contiennent les deux termes dans leurs métadonnées génèrent des résultats plus pertinents. Dans les métadonnées, les mots-clés qui apparaissent sous forme de balises intelligentes sont classés plus haut que les mots-clés qui apparaissent dans d’autres champs de métadonnées. [!DNL Experience Manager] permet de donner plus de poids à un terme de recherche particulier. Il est également possible d’[améliorer le classement](#searchrank) de quelques ressources ciblées pour des termes de recherche spécifiques.

Pour rechercher rapidement les ressources appropriées, l’interface riche fournit des mécanismes de filtrage, de tri et de sélection. Vous pouvez filtrer les résultats selon plusieurs critères et afficher le nombre de ressources recherchées pour différents filtres. Vous pouvez également réexécuter la recherche en modifiant la requête dans le champ Omni-recherche. Lorsque vous modifiez les termes ou filtres de recherche, les autres filtres restent appliqués pour préserver le contexte de la recherche.

Lorsque les résultats sont de nombreuses ressources, [!DNL Experience Manager] affiche les 100 premiers dans la vue Carte et les 200 premiers dans la vue Liste. Des ressources supplémentaires sont chargées lorsque l’utilisateur fait défiler le contenu. Il s’agit d’améliorer les performances. Regardez une démonstration vidéo du [nombre de ressources affichées](https://www.youtube.com/watch?v=LcrGPDLDf4o).

Il arrive que des ressources inattendues apparaissent dans les résultats de la recherche. Pour plus d’informations, voir [Résultats inattendus](#unexpected-results).

[!DNL Experience Manager] peut effectuer des recherches dans de nombreux formats de fichiers et les filtres de recherche peuvent être personnalisés en fonction des besoins de votre entreprise. Contactez votre administrateur pour savoir quelles options de recherche sont mises à disposition pour votre référentiel de gestion des ressources numériques et quelles restrictions votre compte peut comporter.

<!-- 
### Results with and without enhanced Smart Tags {#withsmarttags}

By default, [!DNL Experience Manager] search combines the search terms with an AND clause. For example, consider searching for keywords woman running. Only the assets with both woman and running keywords in the metadata appear in the search results by default. The same behavior is retained when special characters (periods, underscores, or dashes) are used with the keywords. The following search queries return the same results:

* `woman running`
* `woman.running`
* `woman-running`

However, the query `woman -running` returns assets without `running` in their metadata.
Using Smart Tags adds an extra `OR` clause to find any of the search terms as the applied smart tags. An asset tagged with either `woman` or `running` using Smart Tags also appear in such a search query. So the search results are a combination of,

* Assets with `woman` and `running` keywords in the metadata (default behavior).

* Assets smart tagged with either of the keywords (Smart Tags behavior).
-->

### Classement et amplification des recherches {#searchrank}

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche dans les balises intelligentes. Dans l’exemple ci-dessus, l’ordre approximatif d’affichage des résultats de recherche est le suivant :

1. Correspondances de `woman running` dans les différents champs de métadonnées.
1. Correspondances de `woman running` dans les balises intelligentes.
1. Correspondances de `woman` ou de `running` dans les balises intelligentes.

Vous pouvez améliorer la pertinence des mots-clés pour des ressources particulières afin d’améliorer les recherches basées sur les mots-clés. En d’autres termes, les images pour lesquelles vous convertissez des mots-clés spécifiques apparaissent en haut des résultats de la recherche lorsque vous effectuez une recherche en fonction de ces mots-clés.

1. Dans l’interface utilisateur [!DNL Assets], ouvrez la page des propriétés de la ressource. Cliquez sur **[!UICONTROL Avancé]** et cliquez sur **[!UICONTROL Ajouter]** sous **[!UICONTROL Élever pour les mots-clés de recherche]**.
1. Dans la boîte de dialogue **[!UICONTROL Rechercher une promotion]**, indiquez un mot-clé pour lequel vous souhaitez améliorer la recherche d’image, puis cliquez sur **[!UICONTROL Ajouter]**. Vous pouvez indiquer plusieurs mots-clés de la même manière.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La ressource pour laquelle vous avez promu ce mot-clé apparaît en tête des résultats de recherche.

Vous pouvez l’utiliser à votre avantage en améliorant le classement de certaines ressources dans les résultats de recherche du mot-clé ciblé. Voir la vidéo d’exemple ci-dessous. Pour plus d’informations, voir [Recherche dans [!DNL Experience Manager]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=fr).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Vidéo : Découvrez comment les résultats de recherche sont classés et comment le classement peut être influencé.*

## Configuration de la taille de lot des ressources pour afficher les résultats de la recherche {#configure-asset-batch-size}

Les administrateurs peuvent désormais configurer la taille du lot des ressources qui s’affichent lorsque vous effectuez une recherche. Les résultats de recherche de ressources s’affichent en multiples de la taille de lot configurée lorsque vous faites défiler la page vers le bas pour charger les résultats. Vous pouvez sélectionner les tailles de lot disponibles (200, 500 et 1 000 ressources). Si vous définissez un nombre de lots inférieur, les temps de réponse de la recherche sont plus rapides.

Par exemple, si vous définissez la limite du nombre de résultats sur une taille de lot de 200 ressources, Experience Manager Assets affiche une taille de lot de 200 ressources dans les résultats de la recherche lorsque vous commencez à effectuer la recherche. Lorsque vous faites défiler vers le bas pour parcourir les résultats de la recherche, le lot suivant de 200 ressources s’affiche. Le processus se poursuit jusqu’à ce que toutes les ressources correspondant à la requête soient affichées.

Pour configurer la taille de lot de ressources :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Assets]** > **[!UICONTROL Configurations Assets]** > **[!UICONTROL Configuration Assets Omnisearch]**.

1. Sélectionnez la limite du nombre de résultats et cliquez sur **[!UICONTROL Enregistrer]**.

   ![Configuration de la taille de lot des ressources](/help/release-notes/assets/assets-batch-size-configuration.png)

## Recherche avancée {#scope}

[!DNL Experience Manager] fournit diverses méthodes, telles que des filtres qui s’appliquent aux ressources recherchées, pour vous aider à localiser plus rapidement les ressources qu’il vous faut. Quelques méthodes fréquemment utilisées sont décrites ci-dessous. Vous trouverez ci-dessous plusieurs [exemples illustrés](#samples).

**Recherche de fichiers ou de dossiers** : dans les résultats de recherche, reportez-vous aux fichiers, aux dossiers ou aux deux. Dans le panneau **[!UICONTROL Filtres]**, vous pouvez sélectionner l’option appropriée. Voir [Interface de recherche](#searchui).

**Recherche de ressources dans un dossier** : vous pouvez limiter la recherche à un dossier spécifique. Dans le panneau **[!UICONTROL Filtres]**, ajoutez le chemin d’un dossier. Vous ne pouvez sélectionner qu’un dossier à la fois.

![Limitation des résultats de recherche à un dossier en ajoutant un chemin de dossier dans le panneau Filtres](assets/limiting-search.gif)
<!--
![Limit search results to a folder by adding a folder path in Filters panel](assets/search_folder_select.gif)
-->

*Figure : Limitation des résultats de recherche à un dossier en ajoutant un chemin de dossier dans le panneau Filtres.*

### Rechercher des images similaires {#visualsearch}

Pour rechercher des images visuellement similaires à une image sélectionnée par l’utilisateur, cliquez sur l’option **[!UICONTROL Rechercher des images similaires]** dans le mode Carte d’une image ou dans la barre d’outils. [!DNL Experience Manager] affiche les images avec balises intelligentes du référentiel DAM qui sont semblables à une image sélectionnée par l’utilisateur ou l’utilisatrice.

![Rechercher des images similaires à l’aide de l’option en mode Carte](assets/search_find_similar.png)

*Figure : Rechercher des images similaires à l’aide de l’option en mode Carte.*

### Images Adobe Stock {#adobe-stock}

Dans l’interface utilisateur d’[!DNL Experience Manager], les utilisateurs peuvent rechercher des [ressources Adobe Stock](/help/assets/aem-assets-adobe-stock.md) et obtenir des licences pour les ressources requises. Ajoutez `Location: Adobe Stock` dans la barre OmniSearch. Vous pouvez également utiliser le panneau Filtres pour trouver toutes les ressources qui sont ou non sous licence, ou effectuer des recherches dans une ressource spécifique à l’aide du numéro de fichier Adobe Stock.

### Ressources Dynamic Media {#dmassets}

Vous pouvez filtrer les images Dynamic Media en sélectionnant **[!UICONTROL Dynamic Media]** > **[!UICONTROL Visionneuses]** dans le panneau **[!UICONTROL Filtres]**. Il filtre et affiche des ressources telles que des ensembles d’images, des carrousels, des visionneuses de supports variés et des visionneuses à 360°.

### Recherche GQL à l’aide de valeurs spécifiques dans les champs de métadonnées {#gql-search}

Vous pouvez rechercher des ressources en fonction des valeurs exactes de champs de métadonnées, tels que le titre, la description et l’auteur. La fonction de recherche en texte intégral GQL récupère uniquement les ressources dont la valeur de métadonnées correspond exactement à votre requête. Les noms des propriétés (auteur, titre, etc.) et les valeurs sont sensibles à la casse.

| Champ de métadonnées | Valeur et utilisation des facettes |
|---|---|
| Titre | titre :John |
| Créateur | créateur :John |
| Emplacement | emplacement :NA |
| Description | description:&quot;Sample Image&quot; |
| Outil créateur | creatortool:&quot;Adobe Photoshop&quot; |
| Détenteur de copyright | copyrightowner:&quot;Adobe Systems&quot; |
| Contributeur | contributeur :John |
| Conditions d’utilisation | usageterms:&quot;CopyRights Reserved&quot; |
| Créé | a créé :YYYY-MM-DDTHH |
| Date d’expiration | expire:YYYY-MM-DDTHH |
| Heure d’activation | ontime:YYYY-MM-DDTHH |
| Heure de désactivation | hors temps:YYYY-MM-DDTHH |
| Plage de temps (expiration : dateontime,offtime) | champ de facette : lowerbound..upperbound |
| Chemin | /content/dam/&lt;nom_dossier> |
| Titre du PDF | pdftitle:&quot;Adobe Document&quot; |
| Objet | subject:&quot;Training&quot; |
| Balises | tags:&quot;Location And Travel&quot; |
| Type | type:&quot;image\png&quot; |
| Largeur de l’image | largeur:lowerbound..upperbound |
| Hauteur de l’image | hauteur:lowerbound..upperbound |
| Personne | personne :John |

Les propriétés `path`, `limit`, `size` et `orderby` ne peuvent pas être combinées à l’aide de l’opérateur `OR` avec une autre propriété.

<!-- TBD: Where are the limit, size, orderby properties defined?
-->

Le mot-clé d’une propriété générée par un utilisateur correspond au libellé de son champ dans l’éditeur de propriétés en minuscules et sans espace.

Voici quelques exemples de formats de recherche pour des requêtes complexes :

* Pour afficher toutes les ressources avec plusieurs champs de facettes (par exemple : title=John Doe et creator tool=Adobe Photoshop) :`title:"John Doe" creatortool:Adobe*`
* Pour afficher toutes les ressources lorsque la valeur de la facette est une expression et non un seul mot (par exemple : le titre est Scott Reynolds) : `title:"Scott Reynolds"`
* Pour afficher les ressources avec plusieurs valeurs d’une seule propriété (le titre est Scott Reynolds ou John Doe, par exemple) : `title:"Scott Reynolds" OR "John Doe"`
* Pour afficher les ressources avec des valeurs de propriété commençant par une chaîne spécifique (par exemple : le titre est Scott Reynolds) : `title:Scott*`
* Pour afficher les ressources avec des valeurs de propriété se terminant par une chaîne spécifique (par exemple : le titre est Scott Reynolds) : `title:*Reynolds`
* Pour afficher les ressources avec une valeur de propriété contenant une chaîne spécifique (par exemple : le titre est Basel Meeting Room) : `title:*Meeting*`
* Pour afficher les ressources qui contiennent une chaîne spécifique et qui possèdent une valeur de propriété en particulier (par exemple : rechercher une chaîne Adobe parmi les ressources dont le titre est John Doe) : `*Adobe* title:"John Doe"`

## Recherche de ressources à partir d’autres offres ou interfaces [!DNL Experience Manager]  {#search-assets-other-surfaces}

[!DNL Adobe Experience Manager] connecte le référentiel de gestion des ressources numériques à d’autres solutions [!DNL Experience Manager] afin de fournir un accès plus rapide aux ressources numériques et de rationaliser les workflows de création. Toute découverte de ressources commence par la navigation ou la recherche. Le comportement de recherche reste largement le même sur les différentes surfaces et solutions. Certaines méthodes de recherche changent lorsque l’audience cible, les cas d’utilisation et l’interface utilisateur varient d’une solution [!DNL Experience Manager] à l’autre. Les méthodes spécifiques sont documentées pour les solutions individuelles dans les liens ci-dessous. Les conseils et comportements universellement applicables sont décrits dans cet article.

### Recherche de ressources à partir du panneau Adobe Asset Link {#aal}

Grâce à Adobe Asset Link, les professionnels de la création peuvent désormais accéder au contenu stocké dans [!DNL Experience Manager Assets], sans quitter les applications Adobe Creative Cloud prises en charge. Ils peuvent parcourir, rechercher, extraire et archiver des ressources de manière transparente à l’aide du panneau intégré à l’application dans les applications [!DNL Adobe Creative Cloud] : [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] et [!DNL Adobe InDesign]. Asset Link permet également aux utilisateurs de rechercher des résultats visuellement similaires. Les résultats d’affichage de la recherche visuelle sont optimisés par les algorithmes de machine learning d’Adobe Sensei et aident les utilisateurs à trouver des images à l’esthétique similaire. Voir [Rechercher et parcourir des ressources](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) à l’aide d’Adobe Asset Link.

### Recherche de ressources dans l’application de bureau [!DNL Experience Manager]  {#desktop-app}

Les professionnels de la création utilisent l’application de bureau pour rendre les [!DNL Experience Manager Assets] facilement consultables et disponibles sur leur bureau local (Windows ou Mac). Les créatifs peuvent facilement afficher les ressources souhaitées dans le Finder du Mac ou l’Explorateur Windows, ouvertes dans des applications de bureau et modifiées localement ; les modifications sont réenregistrées dans [!DNL Experience Manager] avec une nouvelle version créée dans le référentiel. L’application prend en charge les recherches de base à l’aide d’un ou de plusieurs mots-clés, des caractères génériques `*` et `?`, et de l’opérateur `AND`. Voir [Navigation, recherche et prévisualisation des ressources](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#browse-search-preview-assets) dans l’application de bureau.

### Recherche de ressources dans [!DNL Brand Portal] {#brand-portal}

Les utilisateurs métiers et les spécialistes marketing utilisent Brand Portal pour partager efficacement et en toute sécurité les ressources numériques approuvées avec leurs équipes internes étendues, partenaires et revendeurs. Voir [Recherche de ressources sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html?lang=fr).

### Rechercher des images [!DNL Adobe Stock]  {#adobe-stock1}

Dans l’interface utilisateur d’[!DNL Experience Manager], les utilisateurs peuvent rechercher des ressources Adobe Stock et obtenir des licences pour les ressources requises. Ajoutez `Location: Adobe Stock` dans le champ OmniSearch. Vous pouvez également utiliser le panneau **[!UICONTROL Filtres]** pour trouver toutes les ressources qui sont ou non sous licence, ou effectuer des recherches dans une ressource spécifique à l’aide du numéro de fichier Adobe Stock. Consultez la section [Gestion des images  [!DNL Adobe Stock] dans  [!DNL Experience Manager]](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Recherche de [!DNL Dynamic Media] ressources {#search-dynamic-media-assets}

Vous pouvez filtrer les images Dynamic Media en sélectionnant **[!UICONTROL Dynamic Media]** > **[!UICONTROL Visionneuses]** dans le panneau **[!UICONTROL Filtres]**. Il filtre et affiche des ressources telles que des ensembles d’images, des carrousels, des visionneuses de supports variés et des visionneuses à 360°. Lors de la création de pages web, les auteurs peuvent rechercher des visionneuses dans l’outil de recherche de contenu. Un filtre est disponible pour les visionneuses dans un menu pop-up.

### Recherche de ressources dans l’outil de recherche de contenu lors de la création de pages web {#content-finder}

Les auteurs peuvent utiliser l’outil de recherche de contenu pour rechercher les ressources appropriées dans le référentiel de gestion des ressources numériques et les utiliser dans les pages web qu’ils créent. Les auteurs peuvent également utiliser la fonctionnalité Ressources connectées pour rechercher des ressources disponibles sur un déploiement [!DNL Experience Manager] distant. Les auteurs peuvent ensuite utiliser ces ressources dans des pages web sur un déploiement [!DNL Experience Manager] local. Voir [Utilisation des ressources distantes](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets).

### Recherche de collections {#collections}

La fonctionnalité de recherche [!DNL Experience Manager] prend en charge la recherche de collections et la recherche de ressources dans une collection. Voir [Recherche de collections](/help/assets/manage-collections.md).

## Sélecteur de ressources {#asset-picker}

[Le sélecteur de ressources AEM](/help/assets/overview-asset-selector.md) (appelé sélecteur de ressources dans les versions antérieures de [!DNL Adobe Experience Manager]) vous permet de rechercher, de filtrer et de parcourir les ressources DAM d’une manière spéciale. Le sélecteur de ressources est disponible à l’adresse `https://[aem_server]:[port]/aem/assetpicker.html`. Vous pouvez récupérer les métadonnées des ressources sélectionnées à l’aide du sélecteur de ressources. Vous pouvez le lancer avec les paramètres de requête pris en charge, tels que le type de ressource (image, vidéo, texte) et le mode de sélection (sélections simples ou multiples). Ces paramètres définissent le contexte du sélecteur de ressources pour une instance de recherche particulière et restent inchangés tout au long de la sélection.

Le sélecteur de ressources utilise le message HTML5 `Window.postMessage` pour envoyer au destinataire les données correspondant à la ressource sélectionnée. Il fonctionne uniquement en mode navigation et exclusivement avec la page de résultats Omni-recherche.

Transmettez les paramètres de requête suivants dans une URL pour démarrer le sélecteur de ressources dans un contexte spécifique :

| Nom | Valeurs | Exemple | Objectif |
|---|---|---|---|
| suffixe de la ressource (B) | Chemin du dossier comme suffixe de la ressource dans l’URL : [https://localhost:4502/aem/assetpicker.html/&lt;folder_path>](https://localhost:4502/aem/assetpicker.html) | Pour démarrer le sélecteur de ressources avec un dossier particulier sélectionné, par exemple, le dossier `/content/dam/we-retail/en/activities`, l’URL doit se présentée comme suit : `https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images` | Si vous avez besoin de sélectionner un dossier en particulier au démarrage du sélecteur de ressources, vous pouvez l’indiquer comme suffixe de ressource. |
| `mode` | single, multiple | <ul><li>`https://localhost:4502/aem/assetpicker.html?mode=single`</li><li>`https://localhost:4502/aem/assetpicker.html?mode=multiple`</li></ul> | En mode multiple, vous pouvez sélectionner plusieurs ressources simultanément à l’aide du sélecteur de ressources. |
| `dialog` | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Utilisez ces paramètres pour ouvrir le sélecteur de ressources en tant que boîte de dialogue Granite. Cette option ne peut être appliquée qu’au démarrage du sélecteur de ressources via le champ Chemin de Granite, en la configurant comme URL pickerSrc. |
| `root` | &lt;chemin_dossier> | `https://localhost:4502/aem/assetpicker.html?assettype=images&root=/content/dam/we-retail/en/activities` | Utilisez cette option pour spécifier le dossier racine du sélecteur de ressources. Dans ce cas, le sélecteur de ressources vous permet de sélectionner uniquement les ressources enfants (directes/indirectes) sous le dossier racine. |
| `viewmode` | de recherches | | Pour lancer le sélecteur de ressources en mode recherche, avec les paramètres `assettype` et `mimetype`. |
| `assettype` | Images, documents, multimédia, archives. | <ul><li>`https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives` </li></ul> | Utilisez l’option pour filtrer les types de ressources en fonction de la valeur indiquée. |
| `mimetype` | Type MIME (`/jcr:content/metadata/dc:format`) d’une ressource (le caractère générique est également pris en charge). | <ul><li>`https://localhost:4502/aem/assetpicker.html?mimetype=image/png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&mimetype=*png`</li></ul> | Utilisez-le pour filtrer les ressources basées sur le() type(s) MIME |

Pour accéder à l’interface du sélecteur de ressources, accédez à `https://[aem_server]:[port]/aem/assetpicker`. Recherchez le dossier souhaité, puis sélectionnez une ou plusieurs ressources. Vous pouvez également rechercher la ressource souhaitée dans la zone Omni-recherche, appliquer un filtre selon vos besoins, puis la sélectionner.

![Parcourir et sélectionner une ressource dans le sélecteur de ressources](assets/select-asset.png)

<!--![Browse and select asset in the asset selector](assets/assetpicker.png)-->

*Figure : Parcourir et sélectionner une ressource dans le sélecteur de ressources.*

## Restrictions {#limitations}

La fonctionnalité de recherche dans [!DNL Experience Manager Assets] présente les restrictions suivantes :

* N’entrez pas d’espace de début dans la requête, sinon la recherche ne fonctionne pas.
* [!DNL Experience Manager] peut continuer à afficher le terme de recherche une fois que vous avez sélectionné les propriétés d’une ressource à partir des résultats de recherche, puis annuler la recherche. <!-- (CQ-4273540) -->
* Lors de la recherche de dossiers ou de fichiers et de dossiers, les résultats de recherche ne peuvent être triés selon aucun paramètre.
* Si vous sélectionnez `Return` sans rien taper dans la barre Omni-recherche, [!DNL Experience Manager] renvoie une liste contenant uniquement des fichiers et non des dossiers. Si vous recherchez spécifiquement des dossiers sans utiliser de mot-clé, [!DNL Experience Manager] ne renvoie aucun résultat.
* Vous pouvez effectuer une recherche de texte intégral dans un dossier. Spécifiez un terme pour que la recherche fonctionne.

La recherche visuelle ou par analogie présente les restrictions suivantes :

* Une recherche visuelle fonctionne mieux avec un référentiel volumineux. Bien qu’il n’y ait pas de nombre minimal d’images requis pour obtenir de bons résultats, la qualité des correspondances avec quelques images n’est pas aussi bonne qu’avec un référentiel de taille plus conséquente.
* Vous ne pouvez pas modifier le modèle ni entraîner [!DNL Experience Manager] à rechercher des images similaires. Par exemple, l’ajout ou la suppression de balises intelligentes dans quelques ressources ne modifie pas le modèle. Les ressources sont exclues des résultats de recherche visuellement similaires.

La fonctionnalité de recherche peut présenter des limitations de performances dans les cas suivants :

* Le chargement pour l’affichage des résultats de la recherche est plus rapide dans la vue Carte que dans la vue Liste.

## Conseils de recherche {#tips}

* Si vous surveillez l’état de révision des ressources, utilisez l’option appropriée pour trouver les ressources qui sont approuvées ou en attente d’approbation.
* Utilisez le prédicat Informations pour rechercher les ressources prises en charge en fonction de leurs statistiques d’utilisation obtenues auprès de diverses applications Creative. Les données d’utilisation sont regroupées sous Note d’utilisation, Impressions, Clics et Canaux de médias où les ressources apparaissent dans des catégories.
* Cochez la case **[!UICONTROL Sélectionner tout]** pour sélectionner les ressources recherchées. [!DNL Experience Manager] affiche initialement 100 ressources dans la vue Carte et 200 ressources dans la vue Liste. Des ressources supplémentaires sont chargées lorsque vous faites défiler les résultats de la recherche. Vous pouvez sélectionner plus de ressources que les ressources chargées. Le nombre de ressources sélectionnées est affiché dans l’angle supérieur droit de la page des résultats de la recherche. Vous pouvez agir sur la sélection, par exemple télécharger les ressources sélectionnées, mettre à jour des propriétés de métadonnées en bloc pour les ressources sélectionnées ou ajouter les ressources sélectionnées à une collection. Lorsqu’il y a moins de ressources affichées que de ressources sélectionnées, une action est appliquée à toutes les ressources sélectionnées ou une boîte de dialogue affiche le nombre de ressources auxquelles elle est appliquée. Pour appliquer une action aux ressources qui n’ont pas été chargées, veillez à ce que toutes les ressources soient sélectionnées explicitement.
* Pour rechercher les ressources qui ne contiennent pas les métadonnées obligatoires, voir [Métadonnées obligatoires](#mandatorymetadata).
* La recherche utilise tous les champs de métadonnées. Une recherche générique, telle que la recherche du nombre 12, renvoie généralement de nombreux résultats. Pour de meilleurs résultats, utilisez des guillemets doubles (et non des guillemets simples) ou assurez-vous que le nombre est attaché à un mot sans caractère spécial (par exemple, `shoe12`).
* La recherche en texte intégral prend en charge les opérateurs tels que `-` et `^`. Pour rechercher des informations sous forme de chaînes littérales, indiquez la phrase de recherche entre guillemets. Par exemple, utilisez `"Notebook - Beauty"` au lieu de `Notebook - Beauty`.
* Si les résultats de recherche sont trop nombreux, limitez la [portée de la recherche](#scope) pour trouver les ressources souhaitées. Cela fonctionne mieux lorsque vous avez une idée de la meilleure manière de rechercher les ressources que vous recherchez, par exemple un type de fichier, un emplacement ou des métadonnées spécifiques.

* **Balisage** : les balises permettent de classer les ressources pour une navigation et une recherche plus efficaces. Le balisage permet de propager la taxonomie appropriée à d’autres utilisateurs et workflows. [!DNL Experience Manager] propose des méthodes pour baliser automatiquement les ressources à l’aide des services d’intelligence artificielle d’Adobe Sensei, qui améliorent constamment le balisage de vos ressources au fil de l’utilisation et de l’entraînement. Lorsque vous recherchez des ressources, les balises intelligentes sont prises en compte. Cela fonctionne avec la fonctionnalité de recherche intégrée. Voir [Comportement de la recherche](#searchbehavior). Pour optimiser l’ordre d’affichage des résultats de recherche, vous pouvez [améliorer le classement](#searchrank) de quelques ressources sélectionnées.

* **Indexation** : seules les métadonnées et les ressources indexées sont renvoyées dans les résultats de recherche. Pour une meilleure couverture et de meilleures performances, veillez à une indexation appropriée et suivez les bonnes pratiques. Voir [Indexation](#searchindex).

En savoir plus [Bonnes pratiques de recherche](search-best-practices.md).

## Quelques exemples illustrant la recherche {#samples}

Utilisez des guillemets doubles autour des mots-clés pour rechercher des ressources contenant exactement l’expression dans l’ordre exact spécifié par l’utilisateur.

![Comportement de recherche avec et sans guillemets](assets/search_with_quotes.gif)

*Figure : Comportement de recherche avec et sans guillemets.*

**Recherche avec un caractère générique (astérisque)** : pour élargir la recherche, utilisez un astérisque avant ou après le mot recherché afin de faire correspondre n’importe quel nombre de caractères. Par exemple, la recherche du mot run sans astérisque ne renvoie pas les ressources contenant une variante du mot (y compris dans les métadonnées). L’astérisque remplace n’importe quel nombre de caractères. Par exemple :

* `run` renvoie les ressources contenant exactement le mot-clé « run ».
* `run*` renvoie les ressources concernant `running`, `run`, `runaway`, etc.
* `*run` renvoie les ressources concernant `outrun`, `rerun`, etc.
* `*run*` renvoie toutes les combinaisons possibles.

![Exemple d’utilisation d’un caractère générique (astérisque) dans la recherche de ressources](assets/search_with_asterisk_run.gif)

*Figure : Exemple d’utilisation d’un caractère générique (astérisque) dans la recherche de ressources.*

**Recherche avec un caractère générique (point d’interrogation)** : pour élargir la recherche, utilisez un ou plusieurs caractères « ? ». pour correspondre au nombre exact de caractères. Par exemple, dans l’illustration suivante :

* la requête `run???` ne correspond à aucune ressource ;

* la requête `run????` correspond au mot `running` avec quatre caractères après `run` ;

* la requête `??run` correspond au mot `rerun` avec deux caractères avant `run`.

![Exemple d’utilisation d’un caractère générique (point d’interrogation) dans la recherche de ressources](assets/search_with_questionmark_run.gif)

*Figure : Exemple d’utilisation d’un caractère générique (point d’interrogation) dans la recherche de ressources.*

**Exclusion d’un mot-clé** : utilisez le tiret pour rechercher des ressources qui ne contiennent pas de mot-clé. Par exemple, la requête `running -shoe` renvoie les ressources qui contiennent `running`, mais pas `shoe`. De même, la requête `camp -night` renvoie les ressources qui contiennent `camp`, mais pas `night`. La requête `camp-night` renvoie des ressources contenant `camp` et `night`.

![Utilisation du tiret pour rechercher des ressources ne contenant pas de mot-clé exclu](assets/search_dash_exclude_keyword.gif)

*Figure : Utilisation du tiret pour rechercher des ressources ne contenant pas de mot-clé exclu.*

## Recherche IA {#ai-search}

La recherche par IA est une fonctionnalité de recherche avancée qui comprend la signification et l’intention derrière la requête d’un utilisateur ou d’une utilisatrice plutôt que de s’appuyer sur des correspondances exactes de mots-clés. Il utilise l’intelligence artificielle (IA) et le machine learning pour fournir des résultats plus précis et contextuels.

Contrairement à la recherche traditionnelle par mot-clé, qui recherche des termes exacts, la recherche par IA interprète les relations entre les mots, les concepts et l’intention de l’utilisateur. Cela permet de s’assurer que les utilisateurs et les utilisatrices trouvent ce qu’ils recherchent, même si leur requête est formulée différemment, contient des fautes de frappe ou est dans une autre langue.

Voici quelques-uns de ses principaux avantages :

* **Prise en charge multilingue** : effectuez des recherches dans plusieurs langues sans nécessiter de traduction exacte. Les utilisateurs peuvent trouver du contenu pertinent quel que soit leur langage de requête.

* **Gère les fautes d’orthographe** : interprète les fautes de frappe et d’orthographe pour garantir des résultats précis même avec une saisie imparfaite.

* **Comprend les synonymes** : fournit des résultats pour les termes et expressions associés, de sorte que les utilisateurs n’ont pas besoin de deviner le bon mot-clé.

* **Recherche contextuelle** : reconnaît l’intention derrière une requête, pas seulement les mots exacts.

### Exemples de recherche dans l’IA {#examples-ai-search}

**Exemple d’invite** : *Femme buvant du café*

La recherche traditionnelle par mot-clé recherche les correspondances exactes des métadonnées de ressource, telles que `Woman`, `drinking`, `Coffee`, et renvoie les ressources qui incluent tous ces termes dans les métadonnées.

Cependant, la recherche par l’IA correspond à des mots similaires tels que `Girl`, `Lady` dans le cas de `Woman` et `Cappuccino` et `Latte` dans le cas de `Coffee`.

De même, vous pouvez spécifier cette invite en espagnol ou mal orthographier `Woman` comme `Wman` et obtenir toujours les mêmes résultats.


### Activer ou désactiver la recherche par l’IA dans la vue Administration {#enable-disable-ai-search}

Exécutez les étapes suivantes pour activer ou désactiver la recherche par l’IA dans la vue Administration :

1. Accédez à **[!UICONTROL Outils]** >> **[!UICONTROL Assets]** >> **[!UICONTROL Configurations Assets]** >> **[!UICONTROL Configuration Assets Omnisearch]**.

1. Dans la section **[!UICONTROL Recherche]**, sélectionnez **[!UICONTROL Recherche par l’IA]** pour activer la recherche par l’IA ou **[!UICONTROL Mot-clé]** pour la désactiver.

   ![Activer ou désactiver la recherche IA](/help/assets/assets/enable-ai-search-admin-view.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Tâches de configuration et d’administration liées à la fonctionnalité de recherche {#configadmin}

### Configurations d’index de recherche {#searchindex}

La découverte de ressources repose sur l’indexation du contenu de la gestion des ressources numériques, y compris sur les métadonnées. La précision et la rapidité de la découverte de ressources reposent sur une indexation optimisée et des configurations appropriées. Voir [Indexation](/help/operations/indexing.md).

### Métadonnées obligatoires {#mandatorymetadata}

Les utilisateurs de l’entreprise, les administrateurs ou les bibliothécaires de la gestion des ressources numériques peuvent définir certaines métadonnées comme des métadonnées obligatoires qui sont indispensables au fonctionnement des processus d’entreprise. Pour diverses raisons, il se peut que certaines ressources ne disposent pas de ces métadonnées, telles que les ressources héritées ou les ressources migrées en bloc. Les ressources contenant des métadonnées manquantes ou non valides sont détectées et consignées en fonction de la propriété de métadonnées indexée. Pour configurer cette propriété, consultez la section [Métadonnées obligatoires](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

### Modification des facettes de recherche {#searchfacets}

Pour accélérer la découverte, [!DNL Experience Manager Assets] propose des facettes de recherche à l’aide desquelles vous pouvez filtrer les résultats de la recherche. Le panneau Filtres inclut quelques facettes standard par défaut. L’équipe d’administration peut personnaliser le panneau Filtres pour modifier les facettes par défaut à l’aide des prédicats intégrés. [!DNL Experience Manager] fournit une collection fournie de prédicats intégrés et un éditeur pour personnaliser les facettes. Consultez la section [Facettes de recherche](/help/assets/search-facets.md).

### Extraction de texte lors du chargement de ressources {#extracttextupload}

Vous pouvez configurer [!DNL Experience Manager] pour extraire le texte des ressources lorsque les utilisateurs chargent des ressources, telles que des fichiers PSD ou PDF. [!DNL Experience Manager] indexe le texte extrait et aide les utilisateurs à rechercher ces ressources en fonction du texte extrait. Consultez la section [Chargement de ressources](/help/assets/manage-digital-assets.md#uploading-assets).

### Prédicats personnalisés pour filtrer les résultats de la recherche {#custompredicates}

Les prédicats sont utilisés pour créer des facettes. Les administrateurs peuvent personnaliser les facettes de recherche dans le panneau Filtres à l’aide de prédicats préconfigurés. Ces prédicats peuvent être personnalisés à l’aide de superpositions. Voir la section [Création de prédicats personnalisés](/help/assets/search-facets.md).

Vous pouvez rechercher des ressources numériques en fonction d’une ou de plusieurs des propriétés suivantes. Les filtres qui s’appliquent à certaines de ces propriétés sont disponibles par défaut et certains autres filtres peuvent être créés de manière personnalisée pour s’appliquer aux autres propriétés.

| Champ de recherche | Valeurs de propriété de recherche |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Types MIME | Images, Documents, Multimédia, Archives ou Autre. |
| Date de dernière modification | Heure, Jour, Semaine, Mois ou Année. |
| Taille de fichier | Petit, moyen ou grand. |
| Statut de publication | Publié ou Non publié. |
| Statut d’approbation | Approuvé ou refusé. |
| Orientation | Horizontal, Vertical ou Carré. |
| Style | Couleur ou Noir et blanc. |
| Hauteur de la vidéo | Indiqué sous la forme d’une valeur minimale et d’une valeur maximale. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |
| Largeur de la vidéo | Indiqué sous la forme d’une valeur minimale et d’une valeur maximale. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |
| Format vidéo | DVI, Flash, MPEG4, MPEG, OGG Theora, QuickTime, Windows Media. La valeur est stockée uniquement dans les métadonnées de la source vidéo et de tout rendu. |
| Codec vidéo | x264. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |
| Débit vidéo | Indiqué sous la forme d’une valeur minimale et d’une valeur maximale. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |
| Codec audio | Libvorbis, Lame MP3, codage AAC. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |
| Débit audio | Indiqué sous la forme d’une valeur minimale et d’une valeur maximale. La valeur est stockée uniquement dans les métadonnées des rendus vidéo. |

## Utilisation des résultats de recherche de ressources {#aftersearch}

Vous pouvez effectuer les opérations suivantes avec les ressources que vous avez recherchées dans [!DNL Experience Manager] :

* Afficher les propriétés de métadonnées et d’autres informations
* Télécharger une ou plusieurs ressources
* Utiliser les actions de bureau pour ouvrir ces ressources dans l’application de bureau
* Créer des collections dynamiques
* Créer une version
* Démarrer un workflow
* Associer ou dissocier des ressources
* Appliquez des filtres à l’aide du panneau Filtres qui s’affiche automatiquement après avoir effectué la recherche, afin d’en limiter les résultats.
* Accès à l’emplacement de la ressource

### Tri des résultats de la recherche {#sort}

Trier les résultats de la recherche pour découvrir plus rapidement les ressources requises. Vous pouvez trier les résultats de recherche dans la vue Liste et uniquement lorsque vous sélectionnez **[[!UICONTROL Fichiers]](#searchui)** dans le panneau **[!UICONTROL Filtres]**. [!DNL Assets] utilise le tri côté serveur pour trier rapidement toutes les ressources (quel que soit leur nombre) dans un dossier ou les résultats d’une requête. Le tri côté serveur fournit des résultats plus rapides et plus précis que le tri côté client.

Dans la vue Liste, vous pouvez trier les résultats de recherche tout comme vous pouvez trier les ressources de n’importe quel dossier. Le tri fonctionne sur ces colonnes : Nom, Titre, État, Dimensions, Taille, Évaluation, Utilisation, (Date de) création, (Date de) publication, Workflow et Extraits.

<!--For limitations of sort functionality, see [limitations](#limitations).-->

### Consultation des informations détaillées d’une ressource {#checkinfo}

Vous pouvez consulter les informations détaillées d’une ressource recherchée à partir de la page des résultats de recherche.

Pour afficher toutes les métadonnées d’une ressource, sélectionnez-la, puis cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils.

Pour consulter les commentaires sur une ressource ou son historique de versions, cliquez sur la ressource afin d’ouvrir l’aperçu de grande taille. Ouvrez la chronologie dans le rail de gauche et sélectionnez **[!UICONTROL Commentaires]** ou **[!UICONTROL Versions]**. Vous pouvez également trier l’activité de la chronologie comme les commentaires ou les versions dans un ordre chronologique.

![Tri des entrées de chronologie d’une ressource recherchée](assets/sort_timeline_search_results.gif)

*Figure : Tri des entrées de chronologie d’une ressource recherchée.*

### Téléchargement des ressources recherchées {#download}

Vous pouvez télécharger les ressources recherchées et leurs rendus de la même façon que vous téléchargez des ressources ordinaires à partir de dossiers. Sélectionnez une ou plusieurs ressources dans les résultats de la recherche, puis cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils. Voir [Téléchargement de ressources](/help/assets/download-assets-from-aem.md)

### Mise à jour des propriétés de métadonnées en masse {#metadata-updates}

Il est possible d’effectuer des mises à jour en masse des champs de métadonnées courants de plusieurs ressources. Dans les résultats de recherche, sélectionnez une ou plusieurs ressources. Cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils et mettez à jour les métadonnées selon les besoins. Cliquez sur **[!UICONTROL Enregistrer et fermer]** lorsque vous avez terminé. Les métadonnées figurant précédemment dans les champs mis à jour sont remplacées.

Pour les ressources se trouvant dans un dossier ou une collection unique, il est plus facile de [mettre à jour les métadonnées en masse](/help/assets/bulk-metadata-edit.md) sans utiliser la fonction de recherche. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est plus rapide de mettre à jour les métadonnées en masse par l’intermédiaire d’une recherche.

### Collections dynamiques {#smart-collections}

Une collection est un ensemble ordonné de ressources pouvant inclure des ressources provenant de différents emplacements, car les collections ne contiennent que des références à ces ressources. Les collections sont de deux types :

* Une liste de référence statique de ressources, dossiers et autres collections
* Une liste dynamique (collection dynamique) qui peuple la collection de ressources en fonction de critères de recherche

Vous pouvez créer des collections dynamiques en fonction des critères de recherche. Dans le panneau **[!UICONTROL Filtres]**, sélectionnez **[!UICONTROL Fichiers]** et cliquez sur **[!UICONTROL Enregistrer la collection dynamique]**. Voir [Gérer les collections](/help/assets/manage-collections.md).

### Créer une version {#create-version}

Créez une version pour les ressources qui s’affichent dans les résultats de recherche. Sélectionnez la ressource et cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Version]**. Ajoutez un libellé facultatif ou un commentaire, puis cliquez sur **[!UICONTROL Créer]**. Vous pouvez également sélectionner plusieurs ressources et créer simultanément des versions pour elles.

### Créer un workflow {#create-workflow}

Comme pour la fonction de création de version, vous pouvez créer un workflow pour les ressources qui s’affichent dans les résultats de recherche. Sélectionnez les ressources, puis cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Workflow]**. Sélectionnez le modèle de workflow, spécifiez un titre pour le workflow, puis cliquez sur **[!UICONTROL Démarrer]**.

### Lier et dissocier des ressources {#relate-unrelate-assets}

Liez et dissociez les ressources qui s’affichent dans les résultats de recherche. Sélectionnez les ressources, puis cliquez sur **[!UICONTROL Lier]** ou **[!UICONTROL Dissocier]**.

### Accéder à l’emplacement du dossier de ressources {#navigate-asset-folder-location}

Accédez à l’emplacement du dossier pour les ressources affichées dans les résultats de la recherche. Sélectionnez la ressource et cliquez sur **[!UICONTROL Afficher l’emplacement du fichier]**.

## Résultats de recherche inattendus et problèmes {#unexpected-results}

<!--
**Partially related or unrelated search results**: Experience Manager may display seemingly partially related or unrelated assets, alongside the desired assets in the search results. If you enable Enhanced Smart Tags, the search behavior changes slightly. See how it changes [after smart tagging](#withsmarttags).
-->

| Erreur, problèmes, symptômes | Raison possible | Solution possible ou explication du problème |
|---|---|---|
| Résultats incorrects lors de la recherche de ressources avec des métadonnées manquantes. | Lors de la recherche de ressources qui ne contiennent pas les métadonnées obligatoires, [!DNL Experience Manager] peut afficher certaines ressources qui ont des métadonnées valides. Les résultats reposent sur la propriété de métadonnées indexées. | Une fois les métadonnées mises à jour, une nouvelle indexation est nécessaire pour refléter l’état correct des métadonnées des ressources. Voir [Métadonnées obligatoires](metadata-schemas.md#define-mandatory-metadata). |
| Trop de résultats de recherche. | Paramètre de recherche étendu. | Envisagez de limiter la [portée de la recherche](#scope). L’utilisation de balises intelligentes peut produire plus de résultats de recherche que vous ne le pensiez. Voir [Comportement de la recherche avec des balises intelligentes](#withsmarttags). |
| Résultats de recherche sans rapport ou partiellement liés. | Le comportement de la recherche change avec le balisage intelligent. | Comprendre [comment change la recherche après le balisage intelligent](#withsmarttags). |
| Aucune suggestion de saisie semi-automatique pour les ressources. | Les ressources qui viennent d’être chargées ne sont pas encore indexées. Les métadonnées ne sont pas immédiatement disponibles comme suggestions lorsque vous commencez à saisir un mot-clé de recherche dans la barre Omni-recherche. | [!DNL Experience Manager] attend jusqu’à l’expiration d’un délai d’attente (par défaut, une heure) avant d’effectuer une tâche en arrière-plan afin d’indexer les métadonnées pour toutes les ressources chargées/mises à jour dernièrement et de les ajouter à la liste de suggestions. |
| Aucun résultat de recherche. | <ul><li>Les ressources correspondant à votre requête n’existent pas. </li><li> Espace ajouté avant la requête de recherche. </li><li> Un champ de métadonnées non pris en charge contient le mot-clé que vous avez recherché.</li><li> Recherche effectuée pendant qu’une ressource était désactivée. </li></ul> | <ul><li>Rechercher avec un autre mot-clé. Vous pouvez également utiliser le balisage intelligent ou la recherche par analogie pour améliorer les résultats de la recherche. </li><li>[Limite connue](#limitations).</li><li>Certains champs de métadonnées ne sont pas pris en compte pour les recherches. Voir [Portée](#scope).</li><li>Effectuer une recherche plus tard ou modifier l’heure d’activation et de désactivation des ressources requises.</li></ul> |
| Aucun filtre de recherche ou prédicat n’est disponible. | <ul><li>Le filtre de recherche n’est pas configuré.</li><li>Il n’est pas disponible pour votre connexion.</li><li>(Moins probable) Les options de recherche ne sont pas personnalisées sur le déploiement que vous utilisez.</li></ul> | <ul><li>Contacter l’administrateur pour vérifier la disponibilité de personnalisations de la recherche.</li><li>Contacter l’administrateur pour vérifier si votre compte dispose du privilège ou d’autorisations permettant d’utiliser la personnalisation.</li><li>Contacter l’administrateur et vérifier les personnalisations disponibles pour le déploiement [!DNL Assets] que vous utilisez.</li></ul> |
| Lors de la recherche d’images similaires visuellement, une image attendue est manquante. | <ul><li>L’image n’est pas disponible dans [!DNL Experience Manager].</li><li>L’image n’est pas indexée. Généralement lorsqu’elle a été téléchargée récemment.</li><li>L’image ne présente pas de balises intelligentes.</li></ul> | <ul><li>Ajoutez l’image à [!DNL Assets].</li><li>Contactez votre administrateur pour indexer à nouveau le référentiel. Veillez également à utiliser l’index approprié.</li><li>Contactez votre administrateur ou administratrice pour procéder au balisage intelligent des ressources appropriées.</li></ul> |
| Lors de la recherche d’images similaires visuellement, une image inappropriée est affichée. | Comportement de recherche visuelle. | [!DNL Experience Manager] affiche autant de ressources potentiellement pertinentes que possible. Les images moins pertinentes, le cas échéant, sont ajoutées aux résultats, mais avec un classement inférieur dans les résultats de recherche. La qualité des correspondances et la pertinence des ressources recherchées diminuent à mesure que vous descendez dans les résultats de la recherche. |
| Lors de la sélection de résultats de la recherche et d’action sur ces résultats, aucune action n’est réalisée sur certaines ressources recherchées. | L’option [!UICONTROL Sélectionner tout] ne sélectionne que les 100 premiers résultats de recherche dans la vue Carte et les 200 premiers résultats de recherche dans la vue Liste. | |

**Voir également**

* [Bonnes pratiques de recherche](search-best-practices.md)
* [Traduire les ressources](translate-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* Guide de mise en œuvre des recherches[[!DNL Experience Manager] &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html?lang=fr)
>* [Configuration avancée pour améliorer les résultats de recherche](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=fr)
