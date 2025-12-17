---
title: Améliorez la découverte de contenu avec les métadonnées générées par l’IA
description: Découvrez comment améliorer la découverte de contenu avec les métadonnées générées par l’IA
source-git-commit: 3f44e74488fc73c406fefb6decc41782859d029b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 4%

---


# Améliorez la découverte de contenu avec les métadonnées générées par l’IA {#ai-smart-tags}

Au lieu de recourir à une entrée manuelle, l’IA attribue automatiquement des balises descriptives aux ressources numériques. Ces balises générées par l’IA améliorent la qualité des métadonnées, ce qui facilite la recherche, la classification et la recommandation des ressources. Cette approche améliore non seulement l’efficacité en éliminant le balisage manuel, mais garantit également la cohérence et l’évolutivité sur de grands volumes de contenu numérique. Par exemple, si la ressource est une image, l’IA peut identifier des objets, des scènes, des émotions ou même des logos de marque et générer des balises pertinentes telles que « coucher de soleil », « plage », « vacances » ou « sourire ». Le contenu généré par l’IA peut améliorer la recherche de ressources à l’aide de techniques de recherche sémantique et lexicale. En savoir plus [Rechercher dans Assets](search-assets-view.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![Métadonnées générées par l’IA](/help/assets/assets/enhanced-smart-tags.png)

## Comment activer les métadonnées générées par l’IA ? {#enable-ai-generated-metadata}

Pour activer les métadonnées générées par l’IA :

* La version minimale requise d’AEM est `20626`.


## Utilisation de métadonnées générées par l’IA {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Pour utiliser la fonctionnalité de balises intelligentes améliorée, procédez comme suit :

1. Dans l’interface [!DNL Experience Manager], accédez au dossier souhaité, puis cliquez sur **[!UICONTROL Ajouter Assets]**. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> Les formats de fichiers image compatibles sont `png`, `jpg`, `jpeg`, `psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef`, `arw` et `bmp`.

1. Patientez jusqu’à ce que la ressource nouvellement chargée soit traitée. Une fois l’opération terminée, accédez aux détails de la ressource.

1. Accédez à l’onglet **[!UICONTROL Généré par l’IA]**. Si [!DNL Experience Manager] version est incompatible ou n’est pas mise à jour, cet onglet n’est pas visible.  Les champs suivants sont disponibles :

   * **[!UICONTROL Titre généré] :** le titre fournit un titre clair et concis qui capture l’idée principale d’une ressource téléchargée, ce qui facilite sa compréhension en un coup d’œil. Lors de l’ajout d’une ressource, si vous fournissez un titre (en `dc:title`), il sera affiché dans la vue de navigation des ressources. Si rien n’est indiqué, un titre généré par l’IA est automatiquement attribué.
   * **[!UICONTROL Description générée] :** la description fournit un résumé bref mais informatif de la ressource, aidant les utilisateurs et les modules de recherche à appréhender rapidement sa pertinence.
   * **[!UICONTROL Mots-clés générés] :** les mots-clés sont des termes ciblés qui représentent les thèmes principaux d’une ressource, facilitant le balisage et le filtrage de contenu.

1. [Facultatif] Vous pouvez ajouter des balises supplémentaires ou créer les vôtres si vous pensez qu’il manque des balises pertinentes. Pour ce faire, écrivez vos balises dans le champ **[!UICONTROL Mots-clés générés]** et cliquez sur **[!UICONTROL Enregistrer]**.

Pour plus d’informations sur la désactivation des métadonnées générées par l’IA, voir [Désactiver les métadonnées générées par l’IA](/help/assets/enhance-content-discovery-with-ai-generated-metadata.md#disable-ai-generated-metadata).
