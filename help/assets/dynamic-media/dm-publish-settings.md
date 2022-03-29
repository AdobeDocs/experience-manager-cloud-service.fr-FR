---
title: Configurer la configuration de publication Dynamic Media pour Image Server
description: Découvrez comment configurer une publication dans Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: b0891095-e4a9-4dd5-8dfd-a576bc47d082
source-git-commit: 1730efd1fddd119f2b7950a0e7638ba5624fbb44
workflow-type: tm+mt
source-wordcount: '3456'
ht-degree: 99%

---

# Configurer la configuration de publication Dynamic Media pour Image Server

<!-- hide: yes
hidefromtoc: yes -->

La configuration de la publication Dynamic Media n’est disponible que si :

* Vous disposez d’une configuration de **[!UICONTROL Dynamic Media]** *existante* (dans **[!UICONTROL Cloud Services]**) dans Adobe Experience Manager as a Cloud Service. Voir [Création d’une configuration Dynamic Media dans Services cloud](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
* Vous êtes un administrateur système d’Experience Manager disposant de droits d’administrateur.

La configuration de la publication Dynamic Media est destinée aux développeurs et programmeurs chevronnés de sites web. Adobe Dynamic Media recommande que les utilisateurs qui modifient ces paramètres de publication soient familiarisés avec Adobe Dynamic Media, les normes et conventions de protocole HTTP et la technologie d’imagerie de base.

La page Configuration de la publication Dynamic Media établit les paramètres par défaut qui déterminent la manière dont les ressources sont diffusées des serveurs Dynamic Media d’Adobe vers les sites web ou les applications. Si aucun paramètre n’est spécifié, le serveur Dynamic Media Adobe diffuse une ressource selon un paramètre par défaut configuré sur la page Configuration de la publication Dynamic Media.

Voir aussi [Facultatif - Paramétrage et configuration des paramètres Dynamic Media](/help/assets/dynamic-media/config-dm.md#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings) pour d’autres tâches de configuration facultatives.

>[!NOTE]
>
>Mise à niveau de Dynamic Media Classic vers Dynamic Media sur Adobe Experience Manager as a Cloud Service ? La page [Paramètres généraux](/help/assets/dynamic-media/dm-general-settings.md) et la page Configuration de la publication dans Dynamic Media sont pré-renseignées avec les valeurs issues de votre compte Dynamic Media Classic. Les exceptions correspondent à toutes les valeurs répertoriées dans la zone **[!UICONTROL Options de chargement par défaut]** de la page Paramètres généraux. Ces valeurs se trouvent déjà dans Experience Manager. Ainsi, toutes les modifications que vous apportez sous **[!UICONTROL Options de chargement par défaut]**, dans l’un des cinq onglets, par le biais de l’interface utilisateur Experience Manager, sont reflétées dans Dynamic Media, et non dans Dynamic Media Classic. Tous les autres paramètres et valeurs de la page [Paramètres généraux](/help/assets/dynamic-media/dm-general-settings.md) et de la page Configuration de la publication sont conservés entre Dynamic Media Classic et Dynamic Media sur Experience Manager.

**Pour configurer le serveur d’images de la configuration de la publication Dynamic Media :**

1. En mode création d’Experience Manager, sélectionnez le logo d’Experience Manager pour accéder à la console de navigation globale.
1. Dans le rail de gauche, sélectionnez l’icône Outils, puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Configuration de la publication Dynamic Media]**.
1. Dans la page Serveur d’images, définissez le contexte de publication de votre Serveur d’images, puis utilisez les cinq onglets pour configurer les paramètres de publication par défaut.

   * [Serveur d’images](#image-server)
      * Onglet [Sécurité](#security-tab)
      * Onglet [Gestion des catalogues](#catalog-management-tab)
      * Onglet [Attributs de requête](#request-attributes-tab)
      * Onglet [Attributs de miniature courants](#common-thumbnail-attributes-tab)
      * Onglet [Attributs de gestion des couleurs](#color-management-attributes-tab)

   ![Page de configuration de la publication Dynamic Media](/help/assets/assets-dm/dm-publish-setup.png)
   *Page de configuration de la publication Dynamic Media, avec l’onglet **[!UICONTROL Attributs de requête]**sélectionné.*<br><br>

1. Lorsque vous avez terminé, près du coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.

## Serveur d’images {#image-server}

La page Serveur d’images définit les paramètres par défaut de la diffusion des images à partir des serveurs d’images. Les paramètres sont disponibles dans cinq catégories.

| Contexte de publication | Description |
| --- | --- |
| Diffusion d’images | Indique le contexte pour les paramètres de publication. |
| Diffusion d’images test | Indique le contexte pour tester les paramètres de publication.<br>Pour les nouveaux comptes Dynamic Media uniquement, le champ **[!UICONTROL Adresse du client]** par défaut est automatiquement défini sur `127.0.0.1`.<br>Voir la section [Test des ressources avant de les rendre publiques](#test-assets-before-making-public). |

### Onglet Sécurité {#security-tab}

**[!UICONTROL Adresse du client]** - Permet de spécifier une ou plusieurs adresses IP ou plages d’adresses IP. Lorsqu’elles sont spécifiées, les requêtes adressées à ce catalogue d’images provenant d’un client à une adresse IP non répertoriée sont rejetées. Cette règle s’applique à la fois à la diffusion des images et aux images rendues.

![Onglet Sécurité&#x200B;](/help/assets/assets-dm/dm-ipallowlist.png)<br>*Onglet Sécurité affichant le champ &quot;Autoriser&quot; d’IP.*


### Onglet Gestion des catalogues {#catalog-management-tab}

**[!UICONTROL Chemin d’accès au fichier de définition de l’ensemble de règles]** - Spécifie le fichier contenant les définitions des ensembles de règles pour le catalogue d’images.

Voir aussi le paramètre [RuleSetFile](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media.

>[!NOTE]
>
>Si votre compte Dynamic Media Classic dispose déjà d’un **[!UICONTROL Chemin d’accès au fichier de définition de l’ensemble de règles]** sélectionné (comme défini dans **[!UICONTROL Configuration]** > **[!UICONTROL Application]** > **[!UICONTROL Configuration de la publication]**, sous le groupe **[!UICONTROL Gestion des catalogues]**), votre compte Dynamic Media sur Experience Manager récupère le fichier à partir de Dynamic Media Classic. Le fichier est ensuite stocké et rendu disponible dans ce champ, lorsque vous ouvrez la page **[!UICONTROL Configuration de la publication Dynamic Media]** pour la première fois.

### Onglet Attributs de requête {#request-attributes-tab}

Ces paramètres concernent l’aspect par défaut des images.

| Configuration | Description |
| --- | --- |
| **[!UICONTROL Limite de taille des images de réponse]** | Requis.<br>Pour les nouveaux comptes Dynamic Media uniquement, la taille d’affichage par défaut est automatiquement définie sur Largeur : `3000` et Hauteur : `3000` pour la **[!UICONTROL Diffusion d’images]** et la **[!UICONTROL Diffusion d’images test]**.<br>Spécifie la largeur et la hauteur maximales de l’image de réponse renvoyée au client. Le serveur renvoie une erreur si une requête provoque une image de réponse dont la largeur, ou la hauteur, ou les deux, est supérieure à ce paramètre.<br>Voir aussi le paramètre [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Mode d’obfuscation de requête]** | Activez cette option si vous souhaitez qu’un codage base64 soit appliqué aux requêtes valides.<br>Voir aussi le paramètre [RequestObfuscation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Mode de verrouillage de requête]** | Activez cette option si vous souhaitez qu’un simple verrou de hachage soit inclus dans les requêtes.<br>Voir aussi le paramètre [RequestLock](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Attributs de requête par défaut]** |  |
| **[!UICONTROL Suffixe de fichier image par défaut]** | Requis.<br>Extension de fichier de données par défaut ajoutée aux valeurs des champs Path et MaskPath du catalogue si le chemin d’accès ne contient pas de suffixe de fichier.<br>Voir aussi le paramètre [DefaultExt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Nom de police par défaut]** | Indique la police utilisée si aucune police n’est fournie par une requête de calque de texte. S’il est spécifié, il doit s’agir d’une valeur de nom de police valide dans le mappage de polices de ce catalogue d’images ou dans le mappage de polices du catalogue par défaut.<br>Voir aussi le paramètre [DefaultFont](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Image par défaut]** | Fournit une image par défaut à renvoyer en réponse à une demande pour laquelle l’image demandée est introuvable.<br>Voir aussi le paramètre [DefaultImage](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media.<br>**REMARQUE** : si votre compte Dynamic Media Classic possède déjà une **[!UICONTROL Image par défaut]** sélectionnée (comme défini dans **[!UICONTROL Configuration]** > **[!UICONTROL Application]** > **[!UICONTROL Configuration de la publication]**, sous le groupe **[!UICONTROL Attributs de requête par défaut]**), votre compte Dynamic Media sur Experience Manager récupère le fichier à partir de Dynamic Media Classic. Le fichier est ensuite stocké et rendu disponible dans ce champ lorsque vous ouvrez la page **[!UICONTROL Configuration de la publication Dynamic Media]** pour la première fois. |
| **[!UICONTROL Mode d’image par défaut]** | Lorsque le curseur est activé (curseur à droite), l **[!UICONTROL ’image par défaut]** remplace chaque calque manquant dans l’image source par l’image par défaut et renvoie le composite comme d’ordinaire. Lorsque le curseur est désactivé (curseur à gauche), l’image par défaut remplace l’ensemble de l’image composite, même si l’image manquante n’est que l’un des calques.<br>Voir aussi le paramètre [DefaultImageMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Taille d’affichage par défaut]** | Requis.<br>Pour les nouveaux comptes Dynamic Media uniquement, la taille d’affichage par défaut est automatiquement définie sur Largeur : `1280` et Hauteur : `1280` pour la **[!UICONTROL Diffusion d’images]** et la **[!UICONTROL Diffusion d’images test]**.<br>Le serveur oblige les images de réponse à ne pas dépasser cette largeur et cette hauteur si la requête ne spécifie pas explicitement la taille d’affichage à l’aide de `wid=`, `hei=` ou `scl=`.<br>Voir aussi le paramètre [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Taille de miniature par défaut]** | Requis.<br>Utilisé à la place de l’attribut **[!UICONTROL Taille d’affichage par défaut]** pour les requêtes de miniature (`req=tmb`). Le serveur oblige les images de réponse à ne pas dépasser cette largeur et cette hauteur si une requête de miniature (`req=tmb`) ne spécifie pas la taille explicitement à l’aide de `wid=`, `hei=` ou `scl=`.<br>Voir aussi le paramètre [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Couleur d’arrière-plan par défaut]** | Indique la valeur RVB utilisée pour remplir une zone d’une image de réponse qui ne contient pas de données d’image réelles.<br>Voir aussi le paramètre [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Attributs d’encodage JPEG]** |  |
| **[!UICONTROL Qualité]** | <br>Indique l’attribut par défaut des images de réponse au format JPEG.<br>Pour les nouveaux comptes Dynamic Media uniquement, la valeur par défaut **[!UICONTROL Qualité]** est automatiquement définie sur `80` pour la **[!UICONTROL Diffusion d’images]** et la **[!UICONTROL Diffusion d’images test]**.<br>Ce champ est défini entre 1 et 100.<br>Voir aussi le paramètre [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Sous-échantillonnage chromatique]** | Activez ou désactivez le sous-échantillonnage chromatique utilisé par les encodeurs JPEG. |
| **[!UICONTROL Mode de rééchantillonnage par défaut]** | Indique les attributs de rééchantillonnage et d’interpolation par défaut à utiliser pour le redimensionnement des données d’image. Utilisé lorsque `resMode` n’est pas spécifié dans une requête.<br>Pour les nouveaux comptes Dynamic Media uniquement, le mode de rééchantillonnage par défaut est automatiquement défini sur `Sharp2` pour la **[!UICONTROL Diffusion d’images]** et la **[!UICONTROL Diffusion d’images test]**.<br>Voir aussi le paramètre [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |

### Onglet Attributs de miniature courants {#common-thumbnail-attributes-tab}

Ces paramètres concernent l’aspect par défaut et l’alignement des images miniatures.

| Configuration | Description |
| --- | --- |
| **[!UICONTROL Couleur d’arrière-plan par défaut de la miniature]** | Indique la valeur RVB utilisée pour remplir la zone d’une miniature de sortie qui ne contient pas de données d’image réelles. Utilisé uniquement pour les requêtes de miniature (`req=tmb`) et lorsque le paramètre **[!UICONTROL Type de miniature par défaut]** est défini sur **[!UICONTROL Ajuster]** ou **[!UICONTROL Texture]**.<br>Voir aussi le paramètre [ThumbBkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Alignement horizontal]** | Spécifie l’alignement horizontal de l’image miniature dans le rectangle de l’image de réponse spécifié par les valeurs `wid=` et `hei=`.<br>Utilisé uniquement pour les requêtes de miniature (`req=tmb`) et lorsque le paramètre **[!UICONTROL Type de miniature par défaut]** est défini sur **[!UICONTROL Ajuster]**.<br>Vous avez le choix entre trois alignements horizontaux : **[!UICONTROL Alignement centré]**, **[!UICONTROL Alignement à gauche]** et **[!UICONTROL Alignement à droite]**.<br>Voir aussi le paramètre [ThumbHorizAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Alignement vertical]** | Spécifie l’alignement vertical de l’image miniature dans le rectangle de l’image de réponse spécifié par les valeurs `wid=` et `hei=`. Utilisé uniquement pour les requêtes de miniature (`req=tmb`) et lorsque le paramètre **[!UICONTROL Type de miniature par défaut]** est défini sur **[!UICONTROL Ajuster]**.<br>Vous avez le choix entre trois alignements verticaux : **[!UICONTROL Alignement en haut]**, **[!UICONTROL Alignement centré]** et **[!UICONTROL Alignement en bas]**.<br>Voir aussi le paramètre [ThumbVertAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Délai d’expiration par défaut du cache]** | Fournit un intervalle d’expiration par défaut en heures au cas où un enregistrement de catalogue spécifique ne contient pas de valeur d’expiration de catalogue valide. Définissez sur `-1` pour marquer comme n’expire jamais. <br>Voir aussi le paramètre [Expiration](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Type de miniature par défaut]** | Fournit une valeur par défaut pour le type de miniature lorsqu’un enregistrement de catalogue particulier ne contient pas de valeur ThumbType de catalogue valide. Utilisé uniquement pour les requêtes de miniature (`req=tmb`).<br>Vous avez le choix entre trois types de miniatures : **[!UICONTROL Recadrer]**, **[!UICONTROL Ajuster]**, et **[!UICONTROL Texture]**.<br>Voir aussi le paramètre [ThumbType](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Résolution de miniature par défaut]** | Fournit une valeur par défaut pour la résolution de l’objet de miniature lorsqu’un enregistrement de catalogue particulier ne contient pas de valeur ThumbRes de catalogue valide. Utilisé uniquement pour les requêtes de miniature (`req=tmb`) et lorsque le paramètre **[!UICONTROL Type de miniature par défaut]** est défini sur **[!UICONTROL Texture]**.<br>Voir aussi le paramètre [ThumbRes](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |

### Onglet Attributs de gestion des couleurs {#color-management-attributes-tab}

Ces paramètres déterminent les profils de couleurs ICC utilisés pour les images.

**Mode de rendu de conversion des couleurs**
Un mode de rendu de conversion des couleurs permet de remplacer l’intention de rendu par défaut des profils de travail afin de déterminer comment les couleurs sources sont ajustées. Utilisé lorsque :

1. L’un des profils ICC par défaut correspond à l’espace colorimétrique cible d’une conversion de couleurs.
1. Un périphérique de sortie (imprimante ou moniteur) est caractérisé par ce profil.
1. Et l’intention de rendu spécifiée est valide pour ce profil.

Les différents modes de rendu utilisent des règles différentes pour déterminer comment les couleurs source sont ajustées.

Voir aussi le paramètre [IccRenderIntent](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media.

>[!NOTE]
>
>En règle générale, il est préférable d’utiliser l’intention de rendu par défaut pour le paramètre de couleur sélectionné, que Adobe a testé pour répondre aux normes du secteur. Par exemple, si vous choisissez un paramètre de couleur pour l’Amérique du Nord ou l’Europe, l’intention de rendu de conversion des couleurs par défaut est : **[!UICONTROL Colorimétrie relative]**. Si vous choisissez un paramètre de couleur pour le Japon, l’intention de rendu de conversion des couleurs par défaut est : **[!UICONTROL Perception]**.

| Configuration | Caractéristiques |
| --- | --- |
| **[!UICONTROL Espace colorimétrique CMJN par défaut]** | Indique le nom du profil de couleurs ICC à utiliser comme profil de travail pour les données CMJN. Si l’option **[!UICONTROL Aucune spécifiée]** est sélectionnée, la gestion des couleurs est désactivée pour ce catalogue d’images lorsque des images source CMJN sont impliquées. Tous les espaces de travail CMJN dépendent des appareils, ce qui signifie qu’ils sont basés sur des combinaisons d’encre et de papier réelles. Les espaces de travail CMJN fournis par Adobe sont basés sur des conditions d&#39;impression commerciales standard.<br> Voir aussi le paramètre [IccProfileCMYK](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Espace colorimétrique de niveaux de gris par défaut]** | Indique le nom du profil de couleurs ICC à utiliser comme profil de travail pour les données en niveaux de gris. Si l’option **[!UICONTROL Aucune spécification]** est sélectionnée, la gestion des couleurs est désactivée pour ce catalogue d’images lorsque des images source en niveaux de gris sont impliquées.<br>Voir aussi le paramètre [IccProfileGray](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Espace colorimétrique RGB par défaut]** | Indique le nom du profil de couleurs ICC à utiliser comme profil de travail pour les données RGB. Si l’option **[!UICONTROL Aucune spécification]** est sélectionnée, la gestion des couleurs est désactivée pour ce catalogue d’images lorsque des images sources RGB sont impliquées. En règle générale, il est préférable de sélectionner **[!UICONTROL Adobe RGB]** ou **[!UICONTROL sRGB]**, plutôt que le profil d’un périphérique spécifique (tel qu’un profil de moniteur). **[!UICONTROL sRGB]** est recommandé lorsque vous préparez des images pour le Web ou les appareils mobiles, car il définit l’espace colorimétrique du moniteur standard utilisé pour afficher les images sur le Web. **[!UICONTROL sRGB]** est également un bon choix lorsque vous travaillez avec des images provenant d’appareils photo numériques grand public, car la plupart de ces appareils utilisent sRGB comme espace colorimétrique par défaut.<br>Voir aussi le paramètre [IccProfileRGB](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html?lang=fr) dans le guide de référence des visionneuses Dynamic Media. |
| **[!UICONTROL Intention de rendu de conversion des couleurs]** | **[!UICONTROL Perception]** : vise à préserver la relation visuelle entre les couleurs afin qu’elles soient perçues comme naturelles par l’œil humain, même si les valeurs de couleur elles-mêmes peuvent changer. Cette intention est adaptée aux images photographiques avec de nombreuses couleurs qui se situent hors de la gamme. Ce paramètre correspond à l’intention de rendu standard pour l’industrie japonaise de l’imprimerie. |
|  | **[!UICONTROL Colorimétrie relative]** : compare la mise en surbrillance extrême de l’espace colorimétrique source à celle de l’espace colorimétrique de destination et modifie toutes les couleurs en conséquence. Les couleurs hors gamme sont décalées vers la couleur reproductible la plus proche dans l’espace colorimétrique de destination. Le paramètre Colorimétrie relative conserve plus de couleurs d’origine dans une image que le paramètre Perception. Ce paramètre est l’intention de rendu standard pour l’impression en Amérique du Nord et en Europe. |
|  | **[!UICONTROL Saturation]** : tente de produire des couleurs vives dans une image au détriment de la précision des couleurs. Cette intention de rendu convient aux graphiques professionnels tels que les graphiques ou les diagrammes, où les couleurs saturées et vives sont plus importantes que la relation exacte entre les couleurs. |
|  | **[!UICONTROL Colorimétrie absolue]** : laisse inchangées les couleurs qui se trouvent dans la gamme de destination. Les couleurs hors gamme sont tronquées. Aucune mise à l’échelle des couleurs n’est effectuée vers le point blanc de destination. Cette intention vise à maintenir la précision des couleurs au détriment de la préservation des relations entre les couleurs. Elle est adaptée à la vérification afin de simuler la sortie d’un appareil particulier. Il s’agit d’une intention utile à la prévisualisation de l’impact de la couleur du papier sur les couleurs imprimées. |

## Tester les ressources avant leur publication {#test-assets-before-making-public}

Secure Testing vous permet de définir un environnement de test sécurisé et de créer une solution business-to-business robuste, basée sur un ensemble configurable d’adresses IP et de plages. Cette fonctionnalité vous permet de faire correspondre vos déploiements Adobe Dynamic Media avec l’architecture de votre système de gestion de contenu et de votre système d’entreprise.

Grâce à Secure Testing, vous pouvez prévisualiser la version d’évaluation du site web avec du contenu non publié.

Si vous le souhaitez, vous pouvez créer un environnement d’évaluation plutôt que de rendre les ressources disponibles publiquement, pour les raisons suivantes :

* Prévisualiser les sites web avant le lancement public (site web d’évaluation).
* Fournir des ressources nécessitant un accès restreint, telles que les catalogues électroniques qui affichent les prix dans une application web B2B.
* Utiliser des ressources derrière un pare-feu dans le cadre du système de gestion de l’information sur les produits, de l’application du service client, du site de formation, etc.

>[!NOTE]
>
>Secure Testing n’a pas d’impact sur l’accès à Adobe Dynamic Media Classic. La sécurité d’Adobe Dynamic Media Classic reste cohérente et requiert les identifiants habituels pour accéder au produit et aux services web associés.

### Fonctionnement de Secure Testing {#how-test-assets-works}

La plupart des entreprises utilisent Internet derrière un pare-feu. L’accès à Internet est possible par le biais de certains itinéraires et généralement via une plage limitée d’adresses IP publiques.

À partir du réseau de votre entreprise, vous pouvez déterminer votre adresse IP publique à l’aide de sites web tels que [https://www.whatismyip.com/fr](https://www.whatismyip.com/fr/). Vous pouvez également obtenir ces informations auprès de la structure informatique de votre entreprise.

Grâce à Secure Testing, Adobe Dynamic Media établit un serveur d’images dédié pour les environnements d’évaluation ou les applications internes. Toute requête sur ce serveur vérifie l’adresse IP d’origine. Si la requête entrante ne figure pas dans la liste approuvée des adresses IP, une réponse d’échec est renvoyée. L’administrateur d’entreprise Adobe Dynamic Media configure la liste approuvée des adresses IP pour l’environnement Secure Testing de l’entreprise.

L’emplacement de la requête d’origine devant être confirmé, le trafic du service Secure Testing n’est pas acheminé à travers un réseau de distribution de contenu tel que le trafic du serveur d’images Dynamic Media public. Les requêtes effectuées auprès du service Secure Testing présentent une latence légèrement plus élevée par rapport aux serveurs d’images Dynamic Media publics.

Les ressources non publiées sont immédiatement disponibles à partir des services Secure Testing, sans avoir à les publier. Ainsi, vous pouvez exécuter un aperçu avant la publication des ressources sur leur serveur d’images public.

>[!NOTE]
>
>Les services Secure Testing utilisent le serveur de catalogue configuré avec un contexte de publication interne. Par conséquent, si votre entreprise est configurée pour publier sur Secure Testing, toutes les ressources chargées dans Adobe Dynamic Media sont immédiatement disponibles sur les services Secure Testing. Cette fonctionnalité s’applique que les ressources soient marquées ou non pour publication au moment du téléchargement.

Les services Secure Testing prennent actuellement en charge les types de ressources et fonctionnalités suivants :

* Images.
* Vignettes (requêtes de serveur de rendu).
* Requêtes de serveur de rendu (prises en charge, mais doivent être demandées explicitement par le client).
* Visionneuses, notamment visionneuses d’images, catalogue électronique, visionneuses de rendus et de supports.
* Visionneuses de médias riches Adobe Dynamic Media standard.
* Pages JSP OnDemand Adobe Dynamic Media.
* Contenu statique, notamment fichiers PDF et vidéos diffusées progressivement.
* Diffusion vidéo en flux continu HTTP.
* Diffusion vidéo progressive.

Les types de ressources et fonctionnalités suivants ne sont actuellement pas pris en charge :

* Recherche de catalogue électronique ou d’informations sur Adobe Dynamic Media Classic.
* Diffusion vidéo en flux continu RTMP.
* Impression en ligne.
* Services UGC (contenu créé par l’utilisateur).

>[!IMPORTANT]
>
>La prise en charge des ressources d’images vectorielles UGC nouvelles ou existantes dans Adobe Dynamic Media a pris fin le 30 septembre 2021.

### Test du service Secure Testing {#test-secure-testing-service}

Pour vous assurer que le service Secure Testing fonctionne comme prévu, procédez comme suit :

#### Préparer votre compte

1. Contactez l’assistance clientèle Adobe et demandez-lui d’activer Secure Testing sur votre compte.
1. Dans Adobe Experience Manager, sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Configuration de la publication de Dynamic Media]**.
1. Sur la page Serveur d’images, dans la liste déroulante **[!UICONTROL Contexte de publication]**, sélectionnez **[!UICONTROL Test de l’hébergeur d’images]**.
1. Sélectionnez l’onglet **[!UICONTROL Sécurité]**.
1. Pour le filtre **[!UICONTROL Adresse du client]**, sélectionnez **[!UICONTROL Ajouter]**.
1. Dans le champ **[!UICONTROL Adresse IP]**, saisissez une adresse IP.
1. Dans le champ **[!UICONTROL Masque]**, saisissez un masque de réseau.

   >[!NOTE]
   >
   >Si vous ajoutez plusieurs adresses IP et masques de réseau, cela permet effectivement à *toutes* les adresses IP d’effectuer des appels de ressources, et elles s’affichent toutes.

1. Utilisez l’une des méthodes suivantes :

   * Pour ajouter d’autres adresses IP, répétez les trois étapes précédentes.
   * Passez à l’étape suivante.

1. Dans le coin supérieur droit de la page Server d’images, sélectionnez **[!UICONTROL Enregistrer]**.
1. Chargez les images souhaitées dans votre compte Adobe Dynamic Media.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Assurez-vous que certaines des images sont marquées pour la publication et d’autres ne le sont pas, puis soumettez la tâche de publication.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Déterminez le nom de votre service de test sécurisé en accédant à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres généraux de Dynamic Media]**.
1. Sur la page **[!UICONTROL Serveur]**, recherchez le nom du serveur à droite de **[!UICONTROL Nom du serveur publié]**.

Contactez Adobe Care si le nom du serveur est manquant ou si l’URL du serveur ne fonctionne pas.

#### Préparation des variantes du site Web

Vous avez besoin de deux variantes d’un site Web qui lie les ressources publiées et non publiées :

* Version publique : liez les ressources à l’aide de la syntaxe traditionnelle de l’URL Adobe Dynamic Media.
* Version intermédiaire : liez les ressources en utilisant la même syntaxe, mais avec le nom du site de test sécurisé.

#### Exécution des tests

Exécutez les tests suivants :

1. Vérifiez si les ressources sont visibles depuis votre réseau d’entreprise.

   Depuis le réseau d’entreprise identifié par la plage d’adresses IP définie précédemment, la version intermédiaire du site Web affiche toutes les images, qu’elles soient marquées pour la publication ou non. Ainsi, vous pouvez tester sans rendre accidentellement les images disponibles avant l’approbation de l’aperçu ou le lancement du produit.

   Vérifiez que la version publique de votre site affiche les ressources publiées comme vous l’avez déjà fait avec Adobe Dynamic Media.

1. Depuis l&#39;extérieur de votre réseau d’entreprise, vérifiez que les ressources non publiées (c’est-à-dire non marquées pour la publication) sont protégées contre l’accès par des tiers.

   Accédez à votre réseau depuis l’extérieur (depuis votre ordinateur personnel, par exemple, ou via une connexion 4G/5G), puis vérifiez que la version publique du site affiche toutes les ressources publiées, mais aucun contenu non publié.

   Vérifiez que la version intermédiaire n’affiche aucune ressource, car vous accédez au service Secure Testing depuis une adresse IP non approuvée.
