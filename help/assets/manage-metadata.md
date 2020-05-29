---
title: Gestion des métadonnées des ressources numériques dans  [!DNL Adobe Experience Manager].
description: Découvrez les types de métadonnées ainsi que l’organisation et le traitement des fichiers par  [!DNL Adobe Experience Manager Assets] helps manage metadata for assets to allow easier categorization and organization of assets. [!DNL Experience Manager] en fonction de leurs métadonnées.
contentOwner: AG
mini-toc-levels: 1
translation-type: ht
source-git-commit: 643d31998989e9ebe73e124313379fb64ec86cd5
workflow-type: ht
source-wordcount: '1830'
ht-degree: 100%

---


# Gestion des métadonnées des ressources numériques {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] conserve les métadonnées de chaque fichier. Cela permet d’obtenir une catégorisation et une organisation plus simples des ressources, ainsi que d’aider les personnes qui recherchent une ressource spécifique. Grâce à la possibilité d’extraire les métadonnées à partir des fichiers chargés sur [!DNL Experience Manager Assets], la gestion des métadonnées s’intègre aux workflows créatifs. La possibilité de conserver et de gérer les métadonnées de vos fichiers permet aussi d’organiser et de traiter automatiquement les fichiers en fonction de leurs métadonnées.

>[!MORELIKETHIS]
>
>* [Métadonnées XMP](xmp-metadata.md)
>* [Modification ou ajout de métadonnées](meta-edit.md)


<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## Pourquoi les métadonnées sont nécessaires {#why-metadata}

Les métadonnées sont des données de description des données. À cet égard, elles font référence à vos ressources numériques (ou actifs), par exemple une image. Les métadonnées sont essentielles pour gérer efficacement des ressources.

Elles constituent un ensemble de toutes les données disponibles pour cette image, mais sans qu’elles y soient contenues. Voici quelques exemples de métadonnées :

* Nom de la ressource.
* Heure et date de la dernière modification.
* Taille de la ressource au moment du stockage dans le référentiel.
* Nom du dossier où elle se trouve.
* Ressources connexes ou balises appliquées.

Les propriétés de métadonnées de base décrites ci-dessus sont utilisées par [!DNL Experience Manager] pour gérer les ressources et permettre aux utilisateurs de les visualiser. Par exemple, ordonner les ressources selon la date de leur dernière modification est utile pour identifier des ressources ajoutées récemment.

Vous pouvez ajouter d’autres données de niveau supérieur à des ressources numériques, par exemple :

* Type de ressource (s’agit-il d’une image, d’une vidéo, d’un clip audio ou d’un document ?).
* Propriétaire.
* Intitulé.
* Description.
* Balises affectées à cette ressource.

D’autres métadonnées permettent de classer les fichiers de manière plus détaillée à mesure que le volume d’informations numériques augmente. Il est ainsi possible de gérer quelques centaines de fichiers en ne prenant en compte que leurs noms. Pour autant, cette approche n’est pas évolutive. Elle est insuffisante si le nombre de personnes concernées et la quantité de ressources gérées augmentent.

Avec l’ajout de métadonnées, la valeur d’une ressource numérique augmente, car elle devient :

* plus accessible : les systèmes et les utilisateurs peuvent la trouver facilement ;
* plus facile à gérer : vous pouvez rechercher plus facilement des ressources avec un même ensemble de propriétés et leur apporter des modifications ;
* complète : la ressource contient davantage d’informations et de contexte grâce à un plus grand nombre de métadonnées.

Ainsi, [!DNL Assets] vous fournit les moyens adéquats pour créer, gérer et échanger des métadonnées pour vos ressources numériques.

## Types de métadonnées {#types-of-metadata}

Les deux types de métadonnées de base sont les métadonnées techniques et les métadonnées descriptives.

Les métadonnées techniques sont utiles pour les applications logicielles qui traitent des ressources numériques. Elles ne doivent pas être gérées manuellement. [!DNL Experience Manager Assets] et d’autres logiciels déterminent automatiquement les métadonnées techniques qui peuvent changer lorsque la ressource est modifiée. Les métadonnées techniques disponibles d’une ressource dépendent largement de son type de fichier. Voici quelques exemples de métadonnées techniques :

* taille d’un fichier ;
* dimensions (hauteur et largeur) d’une image ;
* débit d’un fichier audio ou vidéo ;
* résolution (niveau de détail) d’une image.

Les métadonnées descriptives concernent le domaine d’application, par exemple l’entreprise d’où provient un fichier et ne peuvent pas être déterminées automatiquement. Elles sont créées manuellement ou semi-automatiquement. Par exemple, une caméra GPS peut automatiquement suivre la latitude et la longitude et ajouter un balisage géographique à l’image.

La création manuelle d’informations descriptives de métadonnées coûte cher. Des normes ont donc été mises en place pour faciliter l’échange de métadonnées entre les systèmes logiciels et les organisations. [!DNL Experience Manager Assets] prend en charge l’ensemble des normes pertinentes pour la gestion des métadonnées.

## Normes de codage {#encoding-standards}

Il existe différentes manières d’incorporer des métadonnées dans des fichiers. Un certain nombre de normes de codage sont prises en charge :

* XMP : utilisé par [!DNL Assets] pour stocker les métadonnées extraites dans le référentiel.
* ID3 : pour les fichiers audio et vidéo.
* Exif : pour les fichiers image.
* Autres normes/normes héritées : [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) est une norme ouverte utilisée par [!DNL Experience Manager Assets] pour la gestion des métadonnées. La norme permet le codage universel des métadonnées en l’incorporant dans tous les formats de fichier. Adobe et d’autres entreprises prennent en charge la norme XMP, car elle offre un modèle de contenu enrichi. Les utilisateurs de XMP standard et de [!DNL Experience Manager Assets] disposent d’une plate-forme puissante sur laquelle s’appuyer. Pour plus d’informations, voir la section [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Les données stockées dans ces balises ID3 s’affichent lors de la lecture d’un fichier audio numérique sur un ordinateur ou un lecteur MP3 portable.

Les balises ID3 sont destinées au format de fichier MP3. Informations supplémentaires sur les formats :

* Les balises ID3 fonctionnent dans les fichiers MP3 et mp3PRO.
* Le format WAV ne contient pas de balises.
* Le format WMA possède des balises propriétaires qui n’autorisent pas l’implémentation Open Source.
* Le format Ogg Vorbis utilise des commentaires Xiph incorporés dans le conteneur Ogg.
* Le format AAC utilise un format de balisage propriétaire.

### Exif {#exif}

Le format de fichier d’image échangeable (Exif) est le plus utilisé dans la photographie numérique pour les métadonnées. Il permet d’incorporer un vocabulaire fixe de propriétés de métadonnées dans de nombreux formats de fichiers, tels que JPEG, TIFF, RIFF et WAV. Le format Exif stocke chaque métadonnée sous la forme d’une paire constituée du nom et de la valeur de la métadonnée. Ces paires de nom et de valeur de métadonnées sont également appelées des balises, que l’on ne doit pas confondre avec le balisage dans [!DNL Experience Manager]. Les caméras numériques modernes créent des métadonnées Exif que les logiciels graphiques modernes savent prendre en charge. Le format Exif est le plus petit dénominateur commun pour la gestion des métadonnées, en particulier concernant les images.

Le fait que ce format ne soit pas pris en charge par quelques formats de fichiers image très appréciés comme BMP, GIF ou PNG constitue une limite majeure.

Les champs de métadonnées définis par Exif sont généralement de nature technique et d’une utilité limitée pour la gestion descriptive des métadonnées. D’où l’intérêt de [!DNL Experience Manager Assets] pour mapper les propriétés Exif dans des [schémas de métadonnées courants](metadata-schemas.md) et dans XMP.

#### Autres métadonnées {#other-metadata}

Les autres métadonnées qui peuvent être incorporées à partir de fichiers comprennent celles de [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

## Gestion des métadonnées des ressources numériques {#manage-assets-metadata}

Enterprise Manager Assets vous permet de modifier les métadonnées de plusieurs ressources simultanément afin de propager rapidement et en masse les modifications de métadonnées communes vers les ressources. Utilisez la page [!UICONTROL Propriétés] pour modifier les propriétés de métadonnées en une valeur commune, ou ajoutez ou modifiez des balises. Pour personnaliser la page Propriétés de métadonnées, notamment ajouter, modifier et supprimer des propriétés de métadonnées, utilisez l’éditeur de schéma.

>[!NOTE]
>
>Les méthodes de modification en masse fonctionnent pour les ressources disponibles dans un dossier ou une collection. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est possible de mettre à jour [les métadonnées en masse après une recherche](/help/assets/search-assets.md#metadataupdates).

1. Accédez à l’emplacement des ressources que vous souhaitez modifier.
1. Sélectionnez les ressources dont vous souhaitez modifier les propriétés communes.
1. Sur la barre d’outils, appuyez/cliquez sur **[!UICONTROL Propriétés]** pour ouvrir la page [!UICONTROL Propriétés] des ressources sélectionnées.

   >[!NOTE]
   >
   >Lorsque vous sélectionnez plusieurs ressources, la plus petite forme parent commune est sélectionnée. En d’autres termes, la page [!UICONTROL Propriétés] affiche uniquement les champs de métadonnées communs aux pages [!UICONTROL Propriétés] de toutes les ressources individuelles.

1. Modifiez les propriétés de métadonnées des ressources sélectionnées dans les différents onglets.
1. Pour afficher l’éditeur de métadonnées pour une ressource spécifique, désélectionnez les autres ressources de la liste. Les champs de l’éditeur de métadonnées sont renseignés avec les métadonnées de la ressource particulière.

   >[!NOTE]
   >
   >* Dans la page [!UICONTROL Propriétés], vous pouvez supprimer des ressources de la liste des ressources en les désélectionnant. La liste des ressources contient toutes les ressources sélectionnées par défaut. Les métadonnées des ressources que vous supprimez de la liste ne sont pas mises à jour.
   >* En haut de la liste des ressources, cochez la case située en regard de l’option **[!UICONTROL Titre]** pour passer de la sélection des ressources à l’effacement de la liste, et inversement.


1. Pour sélectionner un schéma de métadonnées différent pour les ressources, appuyez/cliquez sur **[!UICONTROL Paramètres]** dans la barre d’outils, puis sélectionnez le schéma souhaité. Enregistrez les modifications.
1. Pour ajouter les nouvelles métadonnées aux métadonnées existantes dans les champs contenant plusieurs valeurs, sélectionnez **[!UICONTROL Mode d’ajout]**. Si vous ne sélectionnez pas cette option, les nouvelles métadonnées remplacent les métadonnées existantes dans les champs. Appuyez/cliquez sur **[!UICONTROL Envoyer]**.

   >[!CAUTION]
   >
   >Pour les champs à une seule valeur, les nouvelles métadonnées ne sont pas ajoutées à la valeur existante dans le champ même si vous sélectionnez **[!UICONTROL Mode d’ajout]**.

## Configuration du nombre maximal de paramètres pour la mise à jour des métadonnées en masse {#configlimit}

Pour éviter une situation de déni de service (DOS), AEM limite le nombre de paramètres pris en charge dans une requête Sling. Lors de la mise à jour simultanée de plusieurs fichiers, vous pouvez atteindre le nombre maximal de paramètres et les métadonnées ne sont pas mises à jour pour d’autres fichiers. AEM génère l’avertissement suivant dans les journaux :

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Pour modifier le nombre maximal de paramètres, accédez à la console web (**[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**), puis changez la valeur de **[!UICONTROL Maximum POST Parameters]** (nombre maximal de paramètres POST) dans la configuration OSGi de **[!UICONTROL Apache Sling Request Parameter Handling]** (gestion des paramètres de requête Sling Apache).

## Schémas de métadonnées {#metadata-schemata}

Les schémas de métadonnées sont des ensembles prédéfinis de définitions de propriétés de métadonnées qui peuvent être utilisés dans différentes applications. Les propriétés sont toujours associées à une ressource, ce qui signifie que les propriétés « concernent » cette ressource.

Vous pouvez également concevoir vos propres schémas de métadonnées s’il n’en existe aucun qui réponde à vos besoins. Ne dupliquez pas les informations existantes. Au sein d’une organisation, la séparation des schémas facilite le partage des métadonnées. [!DNL Experience Manager] fournit une liste par défaut des schémas de métadonnées les plus utilisés. La liste vous permet de lancer rapidement votre stratégie de métadonnées et de choisir rapidement les propriétés de métadonnées dont vous avez besoin.

Les schémas de métadonnées pris en charge sont répertoriés ci-dessous.

### Métadonnées standard {#standard-metadata}

* DC – [!DNL Dublin Core] est un ensemble de métadonnées important et largement utilisé.
* DICOM – Digital Imaging and Communications in Medicine.
* `Iptc4xmpCore` et `iptc4xmpExt` – International Press Communications Standard contient de nombreuses métadonnées spécifiques à un sujet.
* RDF – Resource Description Framework : pour les métadonnées web de sémantique générique.
* XMP – [!DNL Extensible Metadata Platform].
* `xmpBJ` – Basic Job Ticketing.

### Métadonnées spécifiques à l’application {#application-specific-metadata}

Les métadonnées spécifiques à l’application englobent des métadonnées techniques et descriptives. Si vous utilisez ces types de métadonnées, il se peut que d’autres applications ne soient pas en mesure de les exploiter. Par exemple, il est possible qu’une autre application de rendu d’image ne puisse pas accéder aux métadonnées [!DNL Adobe Photoshop]. Vous pouvez créer une étape de workflow qui transforme une propriété spécifique à l’application en propriété standard.

* ACDSee – métadonnées gérées par le programme. [!DNL ACDSee] Voir [www.acdsee.com/](https://www.acdsee.com/).
* Album – [!DNL Adobe Photoshop Album].
* CQ – utilisées par [!DNL Experience Manager Assets].
* DAM – utilisées par [!DNL Experience Manager Assets].
* DEX – [Optima SC Description explorer](http://www.optimasc.com/products/dex/index.html) est une collection d’outils pour la gestion des métadonnées et des fichiers pour les systèmes d’exploitation Windows.
* CRS – [Adobe Photoshop Camera Raw](https://helpx.adobe.com/fr/camera-raw/using/introduction-camera-raw.html).
* LR – [!DNL Adobe Lightroom].
* MediaPro – [iView MediaPro](https://fr.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto et MP – Microsoft Photo.
* PDF et PDF/X.
* Photoshop et psAux – [!DNL Adobe Photoshop].

### Métadonnées de gestion des droits numériques {#digital-rights-management-metadata}

* CC – [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS – [Picture Licensing Universal System](https://www.useplus.com).
* PRISM – [ Exigences de publication pour les métadonnées standard du secteur (Publishing Requirements for Industry Standard Metadata). ](https://www.idealliance.org/prism-metadata)
* PRL – PRISM Rights Language.
* PUR – PRISM Usage Rights.
* `xmpPlus` – intégration de PLUS avec XMP.

### Métadonnées spécifiques à la photographie {#photography-specific-metadata}

* Exif – de nombreuses informations techniques issues de l’appareil photo, notamment la position GPS.
* CRS – [!DNL Camera Raw] schéma.
* `iptc4xmpCore` et `iptc4xmpExt`.
* TIFF – métadonnées d’image (pas seulement pour les images TIFF).

### Métadonnées spécifiques à l’impression {#print-specific-metadata}

* PDF et PDF/X – Adobe PDF et applications tierces.
* PRISM – [ Exigences de publication pour les métadonnées standard du secteur (Publishing Requirements for Industry Standard Metadata). ](https://www.prismstandard.org)
* XMP – [!DNL Extensible Metadata Platform].
* `xmpPG` – Métadonnées XMP pour le texte paginé.

### Métadonnées multimédias {#multimedia-specific-metadata}

* `xmpDM` – [!DNL Dynamic Media].
* `xmpMM` – Gestion des médias.

## Workflows pilotés par les métadonnées {#metadata-driven-workflows}

La création de workflows pilotés par les métadonnées permet d’automatiser certains processus, ce qui en améliore l’efficacité. Dans un workflow piloté par les métadonnées, le système de gestion des workflows exécute ainsi une action prédéfinie après avoir lu un workflow. Voici quelques exemples d’utilisation des workflows pilotés par les métadonnées :

* Le workflow peut vérifier si une image contient un titre. Dans le cas contraire, le système vous avertit d’ajouter un titre.
* Le workflow peut vérifier si une mention de droit d’auteur relative à un fichier permet la distribution ou non. Ainsi, le système envoie la ressource à un serveur ou à un autre.
* Un workflow peut rechercher des ressources sans métadonnées obligatoires prédéfinies ou des ressources contenant des métadonnées *non valides*.
