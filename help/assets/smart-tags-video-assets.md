---
title: Balisez intelligemment vos fichiers vidéo.
description: Le balisage intelligent des ressources vidéo automatise le balisage des ressources en appliquant des balises contextuelles et descriptives à l’aide des services Adobe Sensei.
translation-type: tm+mt
source-git-commit: 5be8ab734306ad1442804b3f030a56be1d3b5dfa
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---


# Marquez intelligemment vos fichiers vidéo {#video-smart-tags}

Le besoin croissant de nouveaux contenus nécessite des efforts manuels réduits pour fournir en un rien de temps des expériences numériques attrayantes. [!DNL Adobe Experience Manager] en tant que  [!DNL Cloud Service] support du balisage automatisé des ressources vidéo assisté par l&#39;intelligence artificielle. Le balisage manuel des vidéos peut prendre du temps. Cependant, la fonctionnalité de balisage dynamique vidéo optimisée pour Adobe Sensei utilise des modèles d’intelligence artificielle pour analyser le contenu vidéo et ajouter des balises aux fichiers vidéo. Ainsi, les utilisateurs de la gestion des actifs numériques ont moins de temps à fournir des expériences enrichissantes à leurs clients. Le service d’apprentissage automatique d’Adobe génère deux jeux de balises pour une vidéo. Pendant ce temps, une visionneuse correspond aux objets, scènes et attributs de cette vidéo ; l&#39;autre jeu concerne des actions telles que la boisson, la course et le jogging.

Les formats de fichiers vidéo (et leurs codecs) pris en charge pour le balisage intelligent sont MP4 (H264/AVC), MKV (H264/AVC), MOV (H264/AVC, Motion JPEG), AVI (indeo4), FLV (H264/AVC, vp6f) et WMV (WMV). WMV2). En outre, la fonctionnalité permet le balisage des vidéos jusqu&#39;à une taille de 300 Mo. Le balisage automatisé des fichiers vidéo se produit sous forme de traitement standard des fichiers (avec création de miniatures et extraction de métadonnées) après le téléchargement d’une vidéo ou lorsqu’un retraitement est déclenché. Les balises actives s’affichent dans l’ordre décroissant de leur [score de confiance](#confidence-score-video-tag) dans la ressource [!UICONTROL Propriétés]. Le balisage vidéo est activé par défaut dans [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service]. Cependant, vous pouvez [exclure le balisage dynamique vidéo](#opt-out-video-smart-tagging) sur un dossier.

## Balisage intelligent des vidéos lors du transfert {#smart-tag-assets-on-ingestion}

Lorsque vous [téléchargez des fichiers vidéo](add-assets.md#upload-assets) vers [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service], les vidéos sont traitées ![](assets/do-not-localize/assetprocessing.png). Une fois le traitement terminé, consultez l&#39;onglet [!UICONTROL Basic] de la page de propriétés [!UICONTROL de l&#39;actif ]. Les balises actives sont automatiquement ajoutées à la vidéo sous [!UICONTROL Balises dynamiques]. asset compute Service utilise Adobe Sensei pour créer ces balises actives.

![Les balises actives sont ajoutées aux vidéos et affichées dans l’onglet Simple des propriétés du fichier.](assets/smart-tags-added-to-videos.png)

Les balises actives appliquées sont triées par ordre décroissant de [score de confiance](#confidence-score-video-tag), combinés pour les balises d’objet et d’action, dans [!UICONTROL Balises dynamiques].

>[!IMPORTANT]
>
>Il est conseillé de revoir ces balises générées automatiquement afin de vous assurer qu’elles sont conformes à votre marque et à ses valeurs.

## Marquage intelligent des vidéos existantes dans DAM {#smart-tag-existing-videos}

Les ressources vidéo existantes dans la gestion des actifs numériques ne sont pas balisées automatiquement. Vous devez [!UICONTROL retraiter les ressources] manuellement pour générer des balises actives pour elles.

Pour baliser de manière dynamique des fichiers vidéo ou des dossiers (y compris des sous-dossiers) de fichiers qui existent déjà dans le référentiel de ressources, procédez comme suit :

1. Sélectionnez le logo [!DNL Adobe Experience Manager], puis sélectionnez des ressources dans la page [!UICONTROL Navigation].

1. Sélectionnez [!UICONTROL Fichiers] pour afficher l’interface Ressources.

1. Accédez au dossier auquel vous souhaitez appliquer des balises actives.

1. Sélectionnez le dossier entier ou des fichiers vidéo spécifiques.

1. Sélectionnez ![Icône Retraiter les actifs](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Retraiter les actifs] et sélectionnez l&#39;option [!UICONTROL Processus complet].

![Retraiter les ressources pour ajouter des balises aux vidéos du référentiel DAM existant](assets/reprocess.gif)

Une fois le processus terminé, accédez à la page [!UICONTROL Propriétés] de toute ressource vidéo du dossier. Les balises ajoutées automatiquement sont affichées dans la section [!UICONTROL Balises dynamiques] de l&#39;onglet [!UICONTROL Basique]. Ces balises actives appliquées sont triées par ordre décroissant de [score de confiance](#confidence-score-video-tag).

## Rechercher des vidéos balisées {#search-smart-tagged-videos}

Pour rechercher des ressources vidéo en fonction des balises actives générées automatiquement, utilisez [Omnisearch](search-assets.md#search-assets-in-aem) :

1. Sélectionnez l&#39;icône de recherche ![icône de recherche](assets/do-not-localize/search_icon.png) pour afficher le champ Omnisearch.

1. Spécifiez une balise, dans le champ Omnisearch, que vous n&#39;avez pas explicitement ajoutée à une vidéo.

1. Recherche basée sur la balise .

Les résultats de la recherche affichent les fichiers vidéo en fonction de la balise que vous avez spécifiée.

Les résultats de la recherche sont une combinaison de fichiers vidéo avec des mots-clés recherchés dans les métadonnées et de fichiers vidéo avec des balises intelligentes avec les mots-clés recherchés. Cependant, les résultats de la recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées sont affichés en premier, suivis des résultats de la recherche qui correspondent à tous les termes de recherche dans les balises actives. Pour plus d’informations, voir [Comprendre [!DNL Experience Manager] les résultats de la recherche avec des balises actives](smart-tags.md#understandsearch).

## Modération des balises actives vidéo {#moderate-video-smart-tags}

[!DNL Adobe Experience Manager] vous permet de traiter les balises actives pour :

* supprimez les balises inexactes attribuées à vos vidéos de marque.

* affinez les recherches de vidéos basées sur des balises en vous assurant que la vidéo s’affiche dans les résultats de recherche pour les balises les plus pertinentes. Il élimine donc les risques que des vidéos sans rapport entre elles ne s’affichent dans les résultats de la recherche.

* attribuez un rang supérieur à une balise pour accroître sa pertinence par rapport à une vidéo. La promotion d’une balise pour une vidéo augmente les chances d’affichage de la vidéo dans les résultats de la recherche lorsqu’une recherche est effectuée en fonction de cette balise.

Pour en savoir plus sur la manière de modérer les balises actives pour les ressources, voir [Gestion des balises actives](smart-tags.md#manage-smart-tags-and-searches).

![Modération des balises actives vidéo](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Les balises modérées à l’aide des étapes de [Gérer les balises actives](smart-tags.md#manage-smart-tags-and-searches) ne sont pas mémorisées lors du retraitement de la ressource. Le jeu de balises d’origine s’affiche à nouveau.

## opt-out de balisage intelligent vidéo {#opt-out-video-smart-tagging}

Comme le balisage automatisé des vidéos s’exécute en parallèle à d’autres tâches de traitement des fichiers, telles que la création de miniatures et l’extraction des métadonnées, cela peut prendre du temps. Pour accélérer le traitement des fichiers, vous pouvez opt-out de balisage dynamique vidéo au téléchargement au niveau du dossier.

Opt-out de génération de balises actives vidéo automatisée pour les fichiers téléchargés dans un dossier spécifique :

1. Ouvrez l’onglet [!UICONTROL Traitement des ressources] dans le dossier [!UICONTROL Propriétés].

1. Dans le menu [!UICONTROL Balises dynamiques pour les vidéos], l’option [!UICONTROL Héritée] est sélectionnée par défaut et la balise active vidéo est activée.

   Lorsque l&#39;option [!UICONTROL Héritée] est sélectionnée, le chemin d&#39;accès au dossier hérité est également visible avec les informations indiquant s&#39;il est défini sur [!UICONTROL Activer] ou [!UICONTROL Désactiver].

   ![Désactivation du balisage dynamique vidéo](assets/disable-video-tagging.png)

1. Sélectionnez [!UICONTROL Désactiver] pour opt-out balisage intelligent des vidéos téléchargées dans le dossier.

>[!IMPORTANT]
>
>Si vous avez choisi de ne pas baliser les vidéos sur un dossier au moment du téléchargement et que vous souhaitez marquer les vidéos de manière intelligente après le téléchargement, **[!UICONTROL Activez les balises dynamiques pour les vidéos]** à partir de l&#39;onglet [!UICONTROL Traitement des ressources] du dossier [!UICONTROL Propriétés] et utilisez [[!UICONTROL l&#39;option d&#39;ajout ]](#smart-tag-existing-videos). balises actives de la vidéo.

## Note de confiance {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] applique un seuil de confiance minimum pour les balises actives object et action afin d’éviter d’avoir trop de balises pour chaque ressource vidéo, ce qui ralentit l’indexation. Les résultats de la recherche de ressources sont classés en fonction des scores de confiance, ce qui améliore généralement les résultats de la recherche au-delà de ce qu’une inspection des balises affectées de toute ressource vidéo suggère. Les balises inexactes présentent souvent des scores de confiance faibles, de sorte qu’elles apparaissent rarement en haut de la liste Balises dynamiques pour les ressources.

Le seuil par défaut pour les balises d’action et d’objet dans [!DNL Adobe Experience Manager] est 0,7 (doit être compris entre 0 et 1). Si certaines ressources vidéo ne sont pas balisées par une balise spécifique, cela indique que l’algorithme a moins de 70 % d’assurance sur les balises prédites. Le seuil par défaut peut ne pas toujours être optimal pour tous les utilisateurs. Vous pouvez donc modifier la valeur du score de confiance dans la configuration OSGI.

Pour ajouter la configuration OSGI du score de confiance au projet déployé dans [!DNL Adobe Experience Manager] sous la forme [!DNL Cloud Service] à [!DNL Cloud Manager] :

* Dans le projet [!DNL Adobe Experience Manager] (`ui.config` depuis l&#39;archétype 24, ou précédemment `ui.apps`) la configuration `config.author` OSGi, incluez un fichier de configuration nommé `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` avec le contenu suivant :

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```

>[!NOTE]
>
>Une fiabilité de 100 % (fiabilité maximale) est affectée aux balises manuelles. Par conséquent, s’il existe des ressources vidéo avec des balises manuelles qui correspondent à la requête de recherche, elles s’affichent avant les balises actives correspondant à la requête de recherche.

## Restrictions {#video-smart-tagging-limitations}

* La formation du service de balises actives (ou des balises actives améliorées) au balisage de vos ressources vidéo n’est pas encore prise en charge.

* La progression du balisage n’est pas affichée.

* Seules les vidéos de taille inférieure ou égale à 300 Mo peuvent être marquées. Le service Adobe Sensei active les balises des vidéos répondant à ces critères et ignore le balisage des autres vidéos dans un dossier.

* Seules les vidéos dans ces formats de fichier (et codecs pris en charge) : MP4 (H264/AVC), MKV (H264/AVC), MOV (H264/AVC, Motion JPEG), AVI (indeo4), FLV (H264/AVC, vp6f) et WMV (WMV). V2) : peut être balisé.

>[!MORELIKETHIS]
>
>* [Gestion des balises actives et des recherches de ressources](smart-tags.md#manage-smart-tags-and-searches)
>* [Entraînez le service de balises intelligentes et balisez vos images](smart-tags.md)

