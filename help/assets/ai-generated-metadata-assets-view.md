---
title: Améliorez la découverte de contenu avec les métadonnées générées par l’IA
description: Découvrez comment améliorer la découverte de contenu avec les métadonnées générées par l’IA
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 51d8500e-8a19-40b3-a222-4c7e27eeb667
source-git-commit: bcdfc9bb418ab405faa82c55820a6ec6062c2b17
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 19%

---

# Améliorez la découverte de contenu avec les métadonnées générées par l’IA {#ai-smart-tags}

Au lieu de recourir à une entrée manuelle, l’IA attribue automatiquement des balises descriptives aux ressources numériques. Ces balises générées par l’IA améliorent la qualité des métadonnées, ce qui facilite la recherche, la classification et la recommandation des ressources. Non seulement cette approche améliore l’efficacité en éliminant le balisage manuel, mais elle garantit également la cohérence et l’évolutivité sur de gros volumes de contenu numérique. Par exemple, si la ressource est une image, l’IA peut identifier des objets, des scènes, des émotions ou même des logos de marque et générer des balises pertinentes telles que « coucher de soleil », « plage », « vacances » ou « sourire ». Le contenu généré par l’IA peut améliorer la recherche de ressources à l’aide de techniques de recherche sémantique et lexicale. En savoir plus [Rechercher dans Assets](search-assets-view.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![Métadonnées générées par l’IA](/help/assets/assets/enhanced-smart-tags.png)

## Comment activer les métadonnées générées par l’IA ? {#enable-ai-generated-metadata}

Pour activer les métadonnées générées par l’IA :

* La version minimale requise d’AEM est `20626`.


## Utilisation de métadonnées générées par l’IA {#using-ai-generated-smart-tags}

<!--
[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Pour utiliser la fonctionnalité de balises intelligentes améliorée, procédez comme suit :

1. Dans l&#39;interface [!DNL Experience Manager], positionnez-vous dans le dossier de votre choix et cliquez sur **[!UICONTROL Ajouter Assets]**. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> Les formats de fichiers image compatibles sont `png`, `jpg`, `jpeg`, `psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef` et `arw` `bmp`.

1. Patientez jusqu’à ce que la ressource nouvellement chargée soit traitée. Une fois l’opération terminée, accédez aux détails de la ressource.

1. Accédez à l’onglet **[!UICONTROL Généré par l’IA]**. Si [!DNL Experience Manager] version est incompatible ou n’est pas mise à jour, cet onglet n’est pas visible.  Les champs suivants sont disponibles :

   * **[!UICONTROL Titre généré] :** le titre fournit un titre clair et concis qui capture l’idée principale d’une ressource téléchargée, ce qui facilite sa compréhension en un coup d’œil. Lors de l’ajout d’une ressource, si vous fournissez un titre (en `dc:title`), il sera affiché dans la vue de navigation des ressources. Si rien n’est indiqué, un titre généré par l’IA est automatiquement attribué.
   * **[!UICONTROL Description générée] :** la description fournit un résumé bref mais informatif de la ressource, aidant les utilisateurs et les modules de recherche à appréhender rapidement sa pertinence.
   * **[!UICONTROL Mots-clés générés] :** les mots-clés sont des termes ciblés qui représentent les thèmes principaux d’une ressource, facilitant le balisage et le filtrage de contenu.

1. [Facultatif] Vous pouvez ajouter des balises supplémentaires ou créer les vôtres si vous pensez qu’il manque des balises pertinentes. Pour ce faire, écrivez vos balises dans le champ **[!UICONTROL Mots-clés générés]** et cliquez sur **[!UICONTROL Enregistrer]**.

Pour plus d’informations sur la désactivation des métadonnées générées par l’IA, voir [Désactiver les métadonnées générées par l’IA](/help/assets/enhance-content-discovery-with-ai-generated-metadata.md#disable-ai-generated-metadata).


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

