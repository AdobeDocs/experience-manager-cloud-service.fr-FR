---
title: Utilisation de la fonction de conseil en contenu pour accéder à AEM Assets dans Adobe Express
description: Utilisez le gestionnaire de contenu pour découvrir AEM Assets et y accéder directement dans l’intégration native d’Adobe Express.
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '2587'
ht-degree: 0%

---

# Utilisation de la fonction de conseil en contenu pour accéder à AEM Assets dans Adobe Express {#native-integration-adobe-express-using-content-advisor}

Adobe Experience Manager (AEM) Assets s’intègre de manière native à Adobe Express, ce qui vous permet de découvrir, d’accéder et d’utiliser des ressources d’AEM Assets directement dans l’interface Express à l’aide de la fonction de conseil sur le contenu.

Content Advisor transforme la manière dont vous découvrez et utilisez des ressources dans Adobe Express en apportant une découverte de ressources intelligente et contextuelle directement à votre workflow de création. Au lieu de rechercher des ressources en saisissant des mots-clés, le gestionnaire d’accès recherche les ressources appropriées et approuvées en fonction du contenu de la zone de travail, du résumé de campagne et de l’intention, ce qui vous permet de trouver plus rapidement la ressource appropriée.

Grâce à des suggestions intelligentes, à l’accès aux rendus Dynamic Media et à une visibilité complète sur les métadonnées des ressources, le gestionnaire de contenu vous permet de localiser, d’évaluer et d’utiliser efficacement les ressources d’AEM Assets sans quitter Adobe Express. Cela permet une création de contenu plus rapide, une réutilisation des ressources améliorée et une utilisation cohérente des ressources approuvées et conformes à la marque.

![Image de bannière du gestionnaire d’accès](assets/content-advisor-banner-image.png)

Vous pouvez également placer des ressources dans la zone de travail Express et enregistrer le contenu nouveau ou modifié dans AEM Assets, assurant ainsi une gestion et une gouvernance des ressources centralisées. L’intégration native à Adobe Express offre les principaux avantages suivants :

* Création de contenu accélérée avec découverte de ressources et recommandations contextuelles.

* Augmentation de la réutilisation du contenu en modifiant les ressources existantes et en enregistrant de nouvelles ressources dans AEM Assets.

* Accès plus rapide aux rendus Dynamic Media optimisés pour les canaux approuvés.

* Réduction du temps et des efforts nécessaires pour créer de nouvelles ressources ou de nouvelles versions tout en préservant la cohérence de la marque.

## Conditions préalables {#prerequisites}

Autorisations d&#39;accès à Adobe Express et à au moins un environnement dans AEM Assets. L’environnement peut être n’importe lequel des référentiels as a Cloud Service d’Assets.

## Utilisation d’AEM Assets dans l’éditeur Adobe Express {#use-aem-assets-in-express}

Pour commencer à utiliser AEM Assets dans l’éditeur Adobe Express, procédez comme suit :

1. Ouvrez l’application web Adobe Express.

2. Ouvrez une nouvelle zone de travail vierge en chargeant un nouveau modèle ou un nouveau projet, ou en créant une ressource.

3. Cliquez sur **[!UICONTROL Assets]** disponible dans le volet de navigation de gauche. Adobe Express affiche le [gestionnaire d’accès](#intelligent-asset-discovery-content-advisor), qui répertorie les référentiels auxquels vous avez accès, ainsi que la liste des ressources et des dossiers disponibles au niveau racine.

4. Recherchez ou recherchez des ressources dans le référentiel à l’aide du [gestionnaire d’accès](#intelligent-asset-discovery-content-advisor), puis faites-les glisser et déposez-les sur la zone de travail. Vous pouvez également cliquer sur les ressources pour les placer sur la zone de travail. Vous pouvez également filtrer les ressources ![filtrer](assets/do-not-localize/filter.svg) selon différents critères, tels que le statut d’approbation, le type de fichier, le type MIME et les dimensions.

   >[!NOTE]
   >
   >Le filtrage par dimension ne s’applique pas aux vidéos.

   ![Inclure des ressources à partir du module complémentaire Assets](assets/native-express-content-advisor-home.png)

## Détection intelligente des ressources avec le gestionnaire de contenu {#intelligent-asset-discovery-content-advisor}

Le gestionnaire de contenu vous aide à découvrir des ressources pertinentes à l’aide de recommandations intelligentes et contextuelles basées sur le contenu de la zone de travail ou le résumé de la campagne. Il vous permet également de sélectionner des rendus Dynamic Media prêts pour le canal optimisés pour votre cas d’utilisation.


Le gestionnaire d&#39;accès affiche la liste des fichiers, dossiers et collections dans les vues Liste et Grille. Il vous permet d’ajouter des ressources aux formats PNG, JPEG, PSD, MP4, SVG et PDF à la zone de travail Express. Vous pouvez également prévisualiser les fichiers PDF défilables ou tout autre type de format en cliquant sur l’icône ![Icône Infos](assets/info-icon.svg) disponible sur la carte de la ressource.

Cliquez sur l’icône ![Icône Infos](assets/info-icon.svg) pour afficher également les métadonnées de ressource disponibles dans l’onglet **[!UICONTROL De base]** ou afficher les rendus Dynamic Media disponibles dans l’onglet [Dynamic Media](#dynamic-media-renditions-content-advisor). Faites glisser et déposez le contenu suggéré sur la zone de travail. Vous pouvez également cliquer sur la ressource pour la placer automatiquement sur la zone de travail.

![Métadonnées de ressource dans Adobe Express](assets/express-native-integration-metadata.png)


>[!IMPORTANT]
> 
>Veillez à sélectionner un référentiel **auteur** dans la liste déroulante **Référentiel**. Un référentiel **diffusion** n’affiche pas les fonctionnalités du gestionnaire de contenu.
>
> En outre, le référentiel **diffusion** ne dispose pas de ressources organisées dans des dossiers et des collections. Toutes les ressources s’affichent au niveau racine dans une structure plate.

Le gestionnaire d’accès propose les fonctionnalités clés suivantes :

* [Recherche optimisée par l&#39;IA pour une découverte de ressources plus intelligente](#content-advisor-ai-search)

* [Suggestions intelligentes basées sur le contexte et l’intention](#smart-suggestions-content-advisor)

* [Des résumés de campagne pour découvrir les ressources pertinentes](#campaign-briefs-content-advisor)

* [Rendus de ressources Dynamic Media disponibles](#dynamic-media-renditions-content-advisor)

* [Accès aux métadonnées des ressources cohérent avec la vue Assets](#asset-metadata-content-advisor)

* [Filtres d’accès cohérents avec la vue Assets](#filters-content-advisor)

* [Accès et réutilisation des recherches récentes et enregistrées](#saved-searches-content-advisor)

* [Recherche de ressources dans et entre les collections](#search-collections-content-advisor)

### Recherche optimisée par l&#39;IA pour une découverte de ressources plus intelligente {#content-advisor-ai-search}

Content Advisor utilise une fonctionnalité de recherche avancée qui comprend la signification et l’intention derrière la requête d’un utilisateur plutôt que de se fier à des correspondances exactes de mots-clés. Il utilise l’intelligence artificielle (IA) et le machine learning pour fournir des résultats plus précis et contextuels.

Contrairement à la recherche traditionnelle par mot-clé, qui recherche des termes exacts, Recherche optimisée par l&#39;IA interprète les relations entre les mots, les concepts et l’intention de l’utilisateur. Cela permet de s’assurer que les utilisateurs et les utilisatrices trouvent ce qu’ils recherchent, même si leur requête est formulée différemment, contient des fautes de frappe ou est dans une autre langue.

![Recherche optimisée par l&#39;IA pour les ressources dans Adobe Express](assets/express-native-integration-ai-search.png)

Voici quelques-uns de ses principaux avantages :

* Prise en charge multilingue : effectuez des recherches dans plusieurs langues sans nécessiter de traductions exactes. Les utilisateurs peuvent trouver du contenu pertinent quel que soit leur langage de requête.

* Gère les fautes d’orthographe : interprète les fautes de frappe et d’orthographe, en garantissant des résultats précis même avec une saisie imparfaite.

* Comprend les synonymes : fournit des résultats pour les termes et expressions associés, de sorte que les utilisateurs n’ont pas besoin de deviner le bon mot-clé.

* Recherche contextuelle : reconnaît l’intention derrière une requête, pas seulement les mots exacts.

>[!IMPORTANT]
> 
>* La version AEM minimale requise pour accéder à Recherche optimisée par l&#39;IA dans le gestionnaire d’accès est `21994`.


### Suggestions intelligentes basées sur le contexte et l’intention {#smart-suggestions-content-advisor}

Le gestionnaire de contenu affiche des suggestions intelligentes en fonction du contexte et de l’intention du contenu dans la zone de travail express. Cela vous permet de découvrir et d’utiliser rapidement des ressources qui correspondent à vos besoins en matière de contenu, sans avoir à effectuer de recherche manuelle fastidieuse.

![Contenu suggéré du gestionnaire de contenu dans Adobe Express](assets/express-native-integration-suggested-content.png)

>[!IMPORTANT]
> 
>* Le gestionnaire d’accès affiche des suggestions intelligentes en fonction du contexte et de l’intention du contenu disponible dans les calques de texte ou du titre dans la zone de travail express. Il n’affiche pas les résultats en fonction des images disponibles dans la zone de travail.
>* Vous devez signer un Cavalier GenAI pour accéder à cette fonctionnalité dans le gestionnaire de contenu. Pour signer GenAI rider, contactez votre représentant Adobe.
>* La version minimale requise d’AEM pour accéder à cette fonctionnalité est `21994`.
>* Les suggestions intelligentes ne se mettent pas automatiquement à jour lorsque vous mettez à jour la zone de travail. Cliquez sur l’icône d’actualisation dans le panneau **Contenu suggéré** pour afficher la liste mise à jour des suggestions,

### Des résumés de campagne pour découvrir les ressources pertinentes {#campaign-briefs-content-advisor}

Le gestionnaire d’accès vous permet de télécharger un document de résumé de campagne pour découvrir les ressources pertinentes sans saisir manuellement les mots-clés de recherche. Le conseiller d’accès analyse les informations du résumé de la campagne afin de comprendre l’intention de la campagne et recommande les ressources appropriées disponibles dans AEM Assets.

![Inclusion de ressources à partir du module complémentaire Assets.](assets/upload-brief-native-express.png)

>[!IMPORTANT]
>
>* Le gestionnaire d’accès analyse les informations disponibles sous forme de texte dans le résumé de la campagne afin de recommander les ressources appropriées. Il n’analyse pas les informations disponibles sous forme d’images dans le résumé de la campagne.
>* Les types de fichiers pris en charge que vous pouvez charger en tant que résumé de campagne incluent les documents PDF, DOCX et TXT.
>* Vous devez signer un Cavalier GenAI pour accéder à cette fonctionnalité dans le gestionnaire de contenu. Pour signer GenAI rider, contactez votre représentant Adobe.
>* La version minimale requise d’AEM pour accéder à cette fonctionnalité est `21994`.

### Rendus de ressources Dynamic Media disponibles {#dynamic-media-renditions-content-advisor}

Les rendus Dynamic Media fournissent des versions de ressources prêtes à l’emploi et optimisées pour les canaux, notamment les [paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md), [recadrages intelligents](/help/assets/dynamic-media/image-profiles.md), les types de format et les profils de couleurs. Ces rendus permettent de s’assurer que la ressource sélectionnée répond aux exigences de canal et de conception sans nécessiter de modification manuelle ou de duplication de ressources.

Vous pouvez également appliquer des modificateurs Dynamic Media pour prévisualiser les réglages en temps réel avant de placer le rendu sur la zone de travail Express, ce qui permet de sélectionner plus rapidement le rendu le plus approprié tout en préservant la cohérence et la qualité des ressources.

Cliquez sur l’icône ![Icône Infos](assets/info-icon.svg) sur la carte de la ressource et sélectionnez l’onglet **[!UICONTROL Dynamic Media]** pour afficher les rendus disponibles pour une ressource. Vous pouvez choisir d’afficher les rendus [Dynamic Media en mode Scene7](/help/assets/dynamic-media/dynamic-media.md) ou [Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md). Lorsque vous sélectionnez **[!UICONTROL OpenAPI]** pour une ressource, les rendus disponibles s’affichent uniquement si la ressource est approuvée et disponible pour Dynamic Media avec OpenAPI.

Vous devez disposer d’une licence Dynamic Media AEM valide pour afficher l’onglet Dynamic Media .

![Affichage des rendus Dynamic Media](assets/native-express-dynamic-media.png)

Cliquez sur l’icône ![icône d’aperçu](assets/do-not-localize/preview-icon.svg) pour prévisualiser le rendu ou cliquez sur le nom du rendu pour le placer automatiquement sur la zone de travail. Vous pouvez également prévisualiser le rendu, puis le faire glisser et le déposer pour placer l’image sur la zone de travail.

![Prévisualisation des rendus Dynamic Media](assets/native-express-dynamic-media-preview.png)

Cliquez sur **[!UICONTROL Ajouter des modificateurs]**, spécifiez un modificateur dans la zone de texte, puis appuyez sur Entrée pour appliquer la transformation aux rendus en temps réel. De même, vous pouvez ajouter plusieurs modificateurs à un rendu et prévisualiser ces transformations. Effectuez un glisser-déposer de la ressource de l’aperçu dans la zone de travail. Le rendu après l’application de ces modificateurs n’est pas enregistré. Consultez la liste des modificateurs pris en charge pour [Dynamic Media Scene7](https://experienceleague.adobe.com/fr/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference) et [Dynamic Media avec OpenAPI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat).

>[!IMPORTANT]
> 
>Dynamic Media permet de surmonter la limite de 80 Mo de la taille du fichier de chargement dans Adobe Express (web) en fournissant des rendus optimisés de ressources volumineuses. Les rendus Dynamic Media réduisent considérablement la taille du fichier tout en préservant la qualité visuelle. Par exemple, une ressource 300MB TIFF peut être diffusée sous la forme d’un rendu de 2,5 Mo sans compromettre la qualité, ce qui permet d’utiliser efficacement les ressources haute résolution dans Adobe Express.

### Accès aux métadonnées des ressources cohérent avec la vue Assets {#asset-metadata-content-advisor}

Le gestionnaire d’accès permet d’accéder aux propriétés des ressources définies dans AEM Assets, y compris aux métadonnées disponibles dans la vue Assets. Le gestionnaire d’accès utilise la même configuration de métadonnées que dans la vue Assets, répliquant la liste des onglets et du contenu de métadonnées dans la page des détails de la ressource de la vue Assets. Vous pouvez ainsi consulter les détails clés de la ressource, tels que le titre, la description, le format, la taille et d’autres métadonnées avant de sélectionner une ressource. L’accès aux propriétés de la ressource vous permet de choisir la ressource correcte et approuvée pour votre contenu.

![Assets afficher les métadonnées dans le gestionnaire de contenu](assets/native-express-asset-metadata.png)

Cliquez sur l’icône ![Icône Infos](assets/info-icon.svg) sur la carte de la ressource et sélectionnez l’onglet **[!UICONTROL De base]** pour afficher les métadonnées de la ressource. Vous pouvez également afficher d’autres onglets de métadonnées de ressource, tels que Produit, Campagne et Balises, cohérents avec les métadonnées de ressource qui existent dans la vue Assets.

Le gestionnaire d&#39;accès affiche les propriétés (métadonnées) des fichiers dans une vue en lecture seule. Les propriétés ne s’affichent pas pour les collections et les dossiers.

### Filtres d’accès cohérents avec la vue Assets {#filters-content-advisor}

Content Advisor offre les mêmes fonctionnalités de filtrage dans Express que celles disponibles dans la vue Assets, ce qui vous permet d’affiner les ressources à l’aide de filtres prédéfinis. Les mêmes fonctionnalités de filtrage que celles disponibles dans la vue Assets s’appliquent également aux filtres spécifiques aux types de contenu, tels que les fichiers, les dossiers et les collections. Cela garantit une expérience de découverte de ressources cohérente et vous permet de localiser efficacement les ressources appropriées dans Adobe Express.

Si aucun filtre n&#39;est configuré dans la vue Assets via le schéma de filtre, la fonction de conseil en contenu affiche les filtres prêts à l&#39;emploi, notamment le type de fichier, le format de fichier, le statut de la ressource, la taille du fichier, la largeur de l&#39;image, la hauteur de l&#39;image, la date de modification et la date de création.

### Accès et réutilisation des recherches récentes et enregistrées {#saved-searches-content-advisor}

Les recherches enregistrées créées dans la vue Assets sont également disponibles, ce qui vous permet de réutiliser des critères de recherche prédéfinis. Les recherches enregistrées fonctionnent de manière cohérente entre la vue Assets et le gestionnaire de contenu sur tous les navigateurs. Vous pouvez ainsi localiser efficacement les ressources à l’aide de modèles de recherche cohérents dans AEM Assets et Adobe Express.

Pour enregistrer votre recherche fréquemment utilisée à l’aide du gestionnaire d’accès :

1. Spécifiez un terme de recherche (facultatif), cliquez sur l’icône filtres et sélectionnez les options en fonction de vos besoins pour créer une requête.

1. Cliquez sur **[!UICONTROL Appliquer]** pour afficher les résultats.

1. Cliquez sur l’icône Filtres > **Gérer les recherches enregistrées** > **Créer une recherche enregistrée**.

1. Indiquez le nom de la recherche et cliquez sur ![Icône Infos](assets/do-not-localize/checkmark-icon.svg) pour l’enregistrer. La recherche s’affiche dans la liste des éléments.

   ![Grille de contenu Recherches enregistrées](assets/native-express-saved-searches.png)

Pour appliquer l’un des éléments de recherche enregistrés, cliquez sur l’icône Filtres, sélectionnez l’élément de recherche dans la liste déroulante **[!UICONTROL Recherches enregistrées]** et cliquez sur **[!UICONTROL Appliquer]**.

Le gestionnaire d’accès enregistre vos recherches récentes et vous permet également d’enregistrer les recherches fréquemment utilisées pour un accès rapide ultérieur. La liste des recherches récentes n’est pas cohérente entre la vue Assets et le gestionnaire de contenu. Un même utilisateur peut avoir un ensemble différent de recherches récentes dans la vue Assets et le gestionnaire de contenu. Si vous utilisez le mode Incognito pour accéder au gestionnaire d’accès, la liste des recherches récentes n’est pas disponible. En outre, les recherches récentes ne sont pas partagées entre différents navigateurs pour le même utilisateur et sont spécifiques à l’environnement AEM.



La fonction Recherche enregistrée par défaut, disponible dans la vue Assets, n’est pas encore disponible dans le gestionnaire de contenu.

### Recherche de ressources dans et entre les collections {#search-collections-content-advisor}

Le gestionnaire d’accès vous permet de rechercher des ressources ou des collections dans toutes les collections ou de limiter votre recherche à une collection spécifique. Cela vous permet de localiser et d’utiliser rapidement les ressources des collections sélectionnées tout en préservant leur contexte organisationnel prévu.

## Remplacer l’image à l’aide du chargement AEM {#replace-image-using-aem-upload}

De plus, vous pouvez remplacer les images ajoutées à l’aide de **[!UICONTROL AEM Upload]**. Pour cela, procédez comme suit :

1. Parcourez ou recherchez des ressources et effectuez un glisser-déposer sur la zone de travail.

1. Sélectionnez l’image à remplacer. Cliquez sur **[!UICONTROL Remplacer]** et sélectionnez **[!UICONTROL AEM Assets]** parmi diverses autres options.

   ![AEM Replace](assets/aem-replace.png)

1. [Gestionnaire de contenu](#intelligent-asset-discovery-content-advisor) s’ouvre dans le volet de navigation de gauche. Adobe Express affiche la liste des référentiels auxquels vous avez accès, ainsi que la liste des ressources et des dossiers disponibles au niveau racine. Sélectionnez une ressource à partir de là pour prévisualiser le remplacement sur la zone de travail, puis cliquez sur **[!UICONTROL Remplacer]** pour confirmer.

   >[!NOTE]
   >
   > Les types de fichiers SVG ne sont pas pris en charge.

## Enregistrement de projets Adobe Express dans AEM Assets {#save-express-projects-in-assets}

Après avoir incorporé les modifications appropriées dans la zone de travail Express, vous pouvez l’enregistrer dans AEM Assets.

1. Cliquez sur **[!UICONTROL Partager]** pour ouvrir la boîte de dialogue **[!UICONTROL Partager]**.

   ![Enregistrement de ressources dans AEM](assets/adobe-express-share.png)

2. Sélectionnez **AEM Assets**. Adobe Express affiche la boîte de dialogue de chargement.

3. Sélectionnez **Page actuelle** ou **Toutes les pages**. Spécifiez un nom et un format pour la ou les ressources à exporter. Vous pouvez exporter le contenu de la zone de travail aux formats PNG, JPEG, PDF, MP4, MP4+PNG ou MP4+JPEG. Le format s’ajuste automatiquement en fonction des ressources sur la ou les pages de la zone de travail.
Sélectionner **Page active** enregistre la ressource sur la page active dans le dossier de destination. Si vous sélectionnez **Toutes les pages** et que le format d’exportation n’est pas PDF, toutes les pages de la zone de travail sont enregistrées en tant que fichiers distincts dans un nouveau dossier de votre dossier de destination. Si le format d’exportation est PDF, toutes les pages de la zone de travail sont enregistrées en tant que fichier PDF unique dans le dossier de destination.

4. Cliquez sur l’icône de dossier sous **Dossier de destination** pour sélectionner un emplacement et enregistrer la ou les ressources.

   ![Enregistrement de ressources dans AEM](/help/assets/assets/page-selection-and-destination-folder.png)

5. Facultatif : vous pouvez ajouter des métadonnées de campagne pour votre chargement à l’aide du champ **Nom du projet ou de la campagne**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Vous pouvez définir plusieurs noms de projet ou de campagne pour votre chargement. Pour enregistrer le nom, saisissez simplement le nom et appuyez sur Entrée.
Adobe recommande, en règle générale, de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour les ressources que vous avez chargées.

6. De même, définissez des valeurs pour les champs **[!UICONTROL Mots-clés]** et **[!UICONTROL Canaux]**.

7. Cliquez sur **[!UICONTROL Charger]** pour charger la ou les ressources dans AEM Assets.

   >[!NOTE]
   >
   > Si vous enregistrez une ou plusieurs ressources dans le référentiel de diffusion Content Hub, le nom du projet ou de la campagne est un champ obligatoire. Dans ce cas, il n’est pas non plus nécessaire de sélectionner un dossier de destination, car il est automatiquement dérivé des métadonnées.

## Formats de fichiers pris en charge {#supported-file-formats-import-assets}

Adobe Express prend en charge de manière native les formats disponibles à l’adresse [Consultez les exigences minimales en matière d’image](https://helpx.adobe.com/fr/express/web/image-creation-and-editing/change-file-formats/image-requirements.html). Toutefois, AEM Assets prend en charge les types de formats suivants :

| Format pris en charge | Dimensions/résolution max. | Taille de fichier max |
|------------------|---------------------------------------------|---------------|
| JPEG | 65 MP (par exemple, 8 K × 8 K ou 16 K × 4 K) | Ordinateur de bureau de 80 Mo, mobile de 40 Mo |
| PNG | 65 MP (par exemple, 8 K × 8 K ou 16 K × 4 K) | Ordinateur de bureau de 80 Mo, mobile de 40 Mo |
| SVG | — | 250 KO |
| MP4 | 3 840 × 3 840 pixels | 200 MO |
| PSD | 65 MP (par exemple, 8 K × 8 K ou 16 K × 4 K) | Ordinateur de bureau de 80 Mo, mobile de 40 Mo |
| PDF | — | — |


## Limites {#limitations}

1. Pour l’importation et l’exportation, le type de fichier vidéo pris en charge est MP4.

2. Pour l’importation vidéo **MP4** les vidéos avec arrière-plans transparents (couche alpha) ne sont pas prises en charge.
   <!--
   1. The maximum file size supported is 200 MB. If this limit exceeds, an alert message displays.
   2. The maximum supported resolution is 3840 X 3840 pixels.
   3. Videos with transparent backgrounds (alpha channel) are not supported.
   -->

3. Pour l’exportation de vidéo **MP4**, la taille de fichier maximale prise en charge est de 200 Mo. Si cette limite est dépassée, une alerte suggère de réduire la vidéo à 200 Mo ou moins, ou de la charger manuellement dans le dossier de destination AEM Assets après l’avoir téléchargée.

<!--
## Content Advisor Properties {#content-advisor-props}

You can configure following properties for the content advisor:

* `featureSet` : This property enables the Content Advisor MFE.

    ```
    featureSet: [
        ...defaultFeatures, /* to include all default features */
        'advisor', /* enables Content Advisor features */
        'content-fragments', /* enables Content Fragments */
    ],
    ```

* `rail:true/false` : If marked true, Content Advisor is rendered in a left rail view. If it is marked false, the Content Advisor is rendered in modal view.

## Browse assets using Content Advisor {#browse-assets-content-advisor}

<!--In the Modal View of Content Advisor, you can access both [Assets](#using-assets-tab) and [Content Fragments](#using-content-fragments) within a unified interface.

### Assets tab{#assets-tab}

The **[!UICONTROL Assets]** tab allows you to browse or filter available assets, preview them before selection, and choose appropriate **[!UICONTROL Dynamic Media]** [renditions](renditions.md) or [smart crops](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles) as needed. Assets, folders, and collections are presented together in a single, streamlined experience. The interface also provides contextual recommendations based on the integrated application context, helping you quickly identify relevant content.

Within assets tab, you can access content by browsing [Files and folders](#content-advisor-files-and-folders) or viewing [Collections](#content-advisor-collections).

### Files and Folders tab{#content-advisor-files-and-folders}

Browsing content using Files and Folders allows you navigate your assets in a familiar hierarchical structure, making it easy to locate assets within the repository. To browse assets within files and folders, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Files & Folders]**. A hierarchical structure is then displayed, allowing you to easily locate and select the desired assets.

![Browse assets using files and folder](assets/browse-assets-content-advisor.png)

### Collections tab{#content-advisor-collections}

Browsing content using Collections allows you to access curated groups of assets within Collections. To browse assets within Collections, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Collections]**. The interface then displays curated groups of assets, enabling you to browse the content you need.

![Browse assets using Collections](assets/browse-assets-collections.png)

<!--
### Content Fragments tab{#content-fragments}

The [Content Fragments](/help/assets/content-fragments/content-fragments.md) tab displays structured assets, allowing you to browse, search, and filter fragments efficiently within the same interface. To browse assets using Content Fragments, navigate to the **[!UICONTROL Content Fragments]** tab to access and explore the fragments available in the repository.

![Browse assets using Content Fragments](assets/browse-assets-content-fragment.png)
-->


