---
title: Métadonnées XMP
description: Découvrez la norme de métadonnées XMP (Extensible Metadata Platform) pour la gestion des métadonnées. Elle est utilisée par AEM comme format normalisé pour la création, le traitement et l’échange de métadonnées.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c3da535db4bf2b0f71e338f542d388437d6c1623
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 76%

---


# Métadonnées XMP {#xmp-metadata}

XMP (« Extensible Metadata Platform », plate-forme de métadonnées extensible) est la norme de métadonnées utilisée par AEM Assets pour toute la gestion des métadonnées. XMP fournit un format standard pour la création, le traitement et l’échange de métadonnées pour toute une variété d’applications.

En plus d’un codage de métadonnées universel qui peut être incorporé dans tous les formats de fichier, XMP fournit un [modèle de contenu](#xmp-core-concepts) riche et est [pris en charge par Adobe](#advantages-of-xmp) et d’autres sociétés. Ainsi, les utilisateurs XMP, en association avec AEM Assets, disposent d’une plate-forme puissante sur laquelle s’appuyer.

## Présentation et écosystème XMP {#xmp-ecosystem}

AEM Assets prend en charge la norme des métadonnées XMP en mode natif. XMP est une norme destinée au traitement et au stockage de métadonnées normalisées et propriétaires dans les ressources numériques. La norme XMP est conçue pour être la norme commune permettant à plusieurs applications de fonctionner efficacement avec les métadonnées.

Les professionnels de la production, par exemple, utilisent la prise en charge du format XMP intégré au sein des applications d’Adobe pour communiquer les informations entre divers formats de fichier. Le référentiel AEM Assets extrait les métadonnées XMP et les utilise pour gérer le cycle de vie du contenu. Il offre également la possibilité de créer des workflows d’automatisation.

XMP normalise la façon dont les métadonnées sont définies, créées et traitées en fournissant un modèle de données, un modèle de stockage et des schémas. Tous ces concepts sont abordés dans cette section.

Toutes les métadonnées héritées d’EXIF, d’ID3 ou de Microsoft Office sont automatiquement converties au format XMP, qui peut être étendu pour prendre en charge le schéma de métadonnées spécifiques au client comme les catalogues de produits.

Dans la norme XMP, les métadonnées sont constituées d’un ensemble de propriétés. Ces propriétés sont toujours associées à une entité spécifique appelée ressource ; c’est-à-dire qu’elles portent sur celle-ci. Dans le cas de XMP, il s’agit toujours de la ressource (ou actif).

XMP définit un modèle de [métadonnées](https://fr.wikipedia.org/wiki/Métadonnée) exploitable avec n’importe quel ensemble défini d’éléments de métadonnées. XMP définit également des [schémas](https://en.wikipedia.org/wiki/XML_schema) spécifiques pour des propriétés de base utiles pour consigner l’historique d’une ressource lorsqu’elle passe par diverses étapes de traitement, de la photographie, en passant par la [numérisation](https://fr.wikipedia.org/wiki/Scanner_(informatique)) ou la création en tant que texte, à travers des étapes de retouche photo (comme le [recadrage](https://fr.wikipedia.org/wiki/Recadrage_(image)) ou l’ajustement de couleur), pour former une image finale. XMP permet à chaque programme ou appareil d’ajouter ses propres informations à une ressource numérique. Ces informations peuvent être ensuite conservées dans le fichier numérique final.

XMP est le plus souvent sérialisé et stocké à l’aide d’un sous-ensemble du [W3C](https://fr.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://fr.wikipedia.org/wiki/Resource_Description_Framework) (RDF), exprimé à son tour en format [XML](https://fr.wikipedia.org/wiki/Extensible_Markup_Language).

### Avantages du mode XMP {#advantages-of-xmp}

La norme XMP présente les avantages suivants par rapport aux autres normes de codage et schémas :

* Les métadonnées basées sur la norme XMP sont très puissantes et précises.
* La norme XMP permet de définir plusieurs valeurs pour une propriété.
* XMP dispose d’un encodage normalisé, ce qui vous permet d’échanger facilement des métadonnées.
* Le format XMP est extensible. Vous pouvez ajouter d’autres informations à vos ressources.

La norme XMP a été conçue pour être extensible, ce qui vous permet d’ajouter des types de métadonnées personnalisés dans les données XMP. En revanche, ce n’est pas le cas d’EXIF qui présente une liste des propriétés qui ne peut pas être étendue.

>[!NOTE]
>
>En règle générale, XMP ne permet pas l’incorporation des types de données binaires. Pour gérer des données binaires dans XMP, comme des images miniatures, celles-ci doivent être codées dans un format XML tel que `Base64`.

### Notions fondamentales relatives à XMP {#xmp-core-concepts}

**Espaces de noms et schémas**

Un schéma XMP est un ensemble de noms de propriétés défini dans un espace de noms XML commun qui comprend
le type des données et des informations descriptives. Un schéma XMP est identifié par l’URI de l’espace de noms XML. L’utilisation des espaces de noms permet d’empêcher tout conflit entre les propriétés dans différents schémas qui portent le même nom, mais ont un sens différent.

Par exemple, la propriété **Créateur** de deux schémas conçus indépendamment peut signifier la personne ayant créé la ressource ou l’application l’ayant créée (Adobe Photoshop, par exemple).

**Propriétés et valeurs XMP**

XMP peut inclure des propriétés de l’un ou de plusieurs des schémas. Par exemple, un sous-ensemble classique utilisé par de nombreuses applications Adobe peut comprendre les éléments suivants :

* Schéma Dublin Core : `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* Schéma de base XMP : `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* Schéma de gestion des droits XMP : `xmpRights:WebStatement`, `xmpRights:Marked`
* Schéma de gestion des médias XMP : `xmpMM:DocumentID`

**Variantes linguistiques**

XMP vous offre la possibilité d’ajouter une propriété `xml:lang` aux propriétés de texte pour spécifier la langue du texte.

## Écriture différée XMP sur les rendus {#xmp-writeback-to-renditions}

Cette fonction d’écriture différée XMP dans [!DNL Adobe Experience Manager Assets] reproduit les modifications de métadonnées apportées aux rendus de la ressource d’origine.
Lorsque vous modifiez les métadonnées d’un fichier depuis le composant Ressources ou lors du téléchargement du fichier, les modifications sont initialement stockées dans le noeud de métadonnées de la hiérarchie des ressources.

La fonction Écriture différée XMP permet de propager les modifications de métadonnées à l’ensemble des rendus de la ressource ou uniquement à certains d’entre eux. La fonctionnalité n&#39;écrit que les propriétés de métadonnées qui utilisent l&#39;espace de nommage `jcr`, c&#39;est-à-dire qu&#39;une propriété nommée `dc:title` est réécrite, mais qu&#39;une propriété nommée `mytitle` ne l&#39;est pas.

Par exemple, imaginez un scénario où vous modifiez la propriété [!UICONTROL Title] de l’actif intitulé `Classic Leather` en `Nylon`.

![métadonnées](assets/metadata.png)

Dans ce cas, [!DNL Assets] enregistre les modifications apportées à la propriété **[!UICONTROL Title]** dans le paramètre `dc:title` pour les métadonnées de fichier stockées dans la hiérarchie de ressources.

![métadonnées stockées dans le noeud de ressources du référentiel](assets/metadata_stored.png)

>[!NOTE]
>
>La fonction d&#39;écriture différée n&#39;est pas activée par défaut dans [!DNL Assets]. Voir comment [activer l’écriture différée des métadonnées](#enable-xmp-writeback).

### Activer l’écriture différée XMP {#enable-xmp-writeback}

[!UICONTROL Le processus d’] écriture différée des métadonnées DAM permet d’enregistrer en écriture les métadonnées d’un fichier. Pour activer l’écriture différée, procédez comme suit :

1. En tant qu’administrateur, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Lanceurs]**.
1. Sélectionnez le [!UICONTROL lanceur] pour lequel la colonne **[!UICONTROL Workflow]** affiche **[!UICONTROL DAM MetaData Writeback]**. Cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils.

   ![Sélectionnez le lanceur d’écriture différée des métadonnées DAM pour modifier ses propriétés et l’activer.](assets/launcher-properties-metadata-writeback1.png)

1. Sélectionnez **[!UICONTROL Activer]** dans la page **[!UICONTROL Propriétés du lanceur]**. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

Pour appliquer ce flux de travail à une ressource une seule fois, appliquez le flux de travail [!UICONTROL DAM Metadata Writeback] depuis le rail de gauche. Pour appliquer le processus à toutes les ressources téléchargées, ajoutez-le à un profil de post-traitement.

<!-- Commenting for now. Need to document how to enable metadata writeback. See CQDOC-17254.

### Enable XMP writeback {#enable-xmp-writeback}
-->

<!-- asgupta, Engg: Need attention here to update the configuration manager changes. -->

<!-- 
To enable the metadata changes to be propagated to the renditions of the asset when uploading it, modify the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration in Configuration Manager.

1. To open Configuration Manager, access `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration.
1. Select the **[!UICONTROL Propagate XMP]** option, and then save the changes.

### Enable XMP write-back for specific renditions {#enable-xmp-writeback-for-specific-renditions}

To let the XMP write-back feature propagate metadata changes to select renditions, specify these renditions to the [!UICONTROL XMP Writeback Process] workflow step of DAM Metadata WriteBack workflow. By default, this step is configured with the original rendition.

For the XMP write-back feature to propagate metadata to the rendition thumbnails 140.100.png and 319.319.png, perform these steps.

1. Tap/click the AEM logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Workflow]** &gt; **[!UICONTROL Models]**.
1. From the Models page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, tap/click the **[!UICONTROL Process]** tab.
1. In the **[!UICONTROL Arguments]** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, and then tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Save the changes.
1. To regenerate the Pyramid TIFF (PTIFF) renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata write-back workflow. PTIFF renditions are only created and stored locally in a Dynamic Media Hybrid implementation.

1. Save the workflow.

The metadata changes are propagated to the renditions renditions thumbnail.140.100.png and thumbnail.319.319.png of the asset, and not the others.
-->
