---
title: Configuration et utilisation des microservices de ressources
description: Configurez et utilisez les microservices de ressources natifs du cloud pour traiter les ressources à l’échelle.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a316bc6f0c1f0d09f6531b6e1b244596c6010355
workflow-type: tm+mt
source-wordcount: '2530'
ht-degree: 44%

---


# Utiliser les microservices de ressources et les profils de traitement {#get-started-using-asset-microservices}

Les micro-services de ressources permettent un traitement évolutif et résilient des ressources à l’aide d’applications natives au cloud (également appelées travailleurs). Adobe gère les services pour une gestion optimale des différents types de ressources et des options de traitement.

Asset microservices lets you process a [broad range of file types](/help/assets/file-format-support.md) covering more formats out-of-the-box than what is possible with previous versions of [!DNL Experience Manager]. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles qu’ImageMagick.

Le traitement des ressources dépend de la configuration des Profils **[!UICONTROL de]** traitement. Experience Manager fournit une configuration par défaut de base et permet aux administrateurs d’ajouter une configuration de traitement des ressources plus spécifique. Les administrateurs créent, conservent et modifient les configurations des workflows de post-traitement, y compris la personnalisation facultative. La personnalisation des workflows permet aux développeurs d’étendre l’offre par défaut.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Une vue de haut niveau du traitement des ressources](assets/asset-microservices-flow.png "Une vue de haut niveau du traitement des ressources")

>[!NOTE]
>
>The asset processing described here replaces the `DAM Update Asset` workflow model that exists in the previous versions of [!DNL Experience Manager]. La plupart des étapes standard liées aux métadonnées et à la génération du rendu sont remplacées par le traitement des microservices de ressources, tandis que les étapes restantes, le cas échéant, peuvent être remplacées par la configuration du workflow de post-traitement.

## Comprendre les options de traitement des ressources {#get-started}

Experience Manager permet d’effectuer les niveaux de traitement suivants.

| Option | Description | Cas d’utilisation couverts |
|---|---|---|
| [Configuration par défaut](#default-config) | Il est disponible en l’état et ne peut pas être modifié. Cette configuration fournit une fonctionnalité de génération de rendu de base. | <ul> <li>Standard thumbnails used by [!DNL Assets] user interface (48, 140, and 319 pixels) </li> <li> Grande prévisualisation (rendu Web - 1 280 pixels) </li><li> Extraction des métadonnées et du texte.</li></ul> |
| [Configuration personnalisée](#standard-config) | Configuré par les administrateurs via l’interface utilisateur. Fournit davantage d’options pour la génération de rendu en étendant l’option par défaut. Etendez l’option prête à l’emploi pour fournir différents formats et rendus. | <ul><li>Rendu FPO. </li> <li>Modification du format de fichier et de la résolution des images</li> <li> S’appliquer de manière conditionnelle aux types de fichiers configurés. </li> </ul> |
| [Profil personnalisé](#custom-config) | Configuré par les administrateurs via l’interface utilisateur pour utiliser du code personnalisé par le biais d’applications personnalisées pour appeler le service [](https://docs.adobe.com/content/help/en/asset-compute/using/introduction.html)Asset Compute. Prend en charge des exigences plus complexes dans une méthode native de cloud et évolutive. | Voir les cas [d’utilisation](#custom-config)autorisés. |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Formats de fichiers pris en charge {#supported-file-formats}

Les microservices de ressources prennent en charge un large éventail de formats de fichier pour traiter, générer des rendus ou extraire des métadonnées. Voir Formats [de fichiers](file-format-support.md) pris en charge pour la liste complète des types MIME et les fonctionnalités prises en charge pour chaque type.

## Configuration par défaut {#default-config}

Certains paramètres par défaut sont préconfigurés pour garantir que les rendus par défaut requis dans le Experience Manager sont disponibles. La configuration par défaut garantit également la disponibilité des opérations d’extraction des métadonnées et d’extraction de texte. Les utilisateurs peuvent commencer à charger ou à mettre à jour immédiatement les ressources, et le traitement de base est disponible par défaut.

Avec la configuration par défaut, seul le profil de traitement de base est configuré. Un tel profil de traitement n’est pas visible dans l’interface utilisateur et vous ne pouvez pas le modifier. Il s’exécute toujours pour traiter les ressources chargées. Such a default processing profile ensures that the basic processing required by [!DNL Experience Manager] is completed on all assets.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Configuration standard {#standard-config}

[!DNL Experience Manager] offrent des fonctionnalités permettant de générer des rendus plus spécifiques pour des formats courants en fonction des besoins de l’utilisateur. Un administrateur peut créer des Profils [!UICONTROL de] traitement supplémentaires pour faciliter la création de rendu. Les utilisateurs attribuent ensuite un ou plusieurs des profils disponibles à des dossiers spécifiques pour que le traitement supplémentaire soit terminé. Par exemple, le traitement supplémentaire peut générer des rendus pour le Web, les appareils mobiles et les tablettes. La vidéo suivante explique comment créer et appliquer des [!UICONTROL Profils de traitement] et comment accéder aux rendus qui ont été créés.

* **Largeur et hauteur** du rendu : La spécification de largeur et de hauteur du rendu fournit des tailles maximales de l’image de sortie générée. Les microservices de ressources tentent de générer le rendu le plus grand possible, dont la largeur et la hauteur ne sont pas supérieures à la largeur et à la hauteur spécifiées, respectivement. Les proportions sont conservées, c’est-à-dire qu’elles sont identiques à l’original. Une valeur vide signifie que le traitement des ressources utilise, par défaut, la taille en pixels de l’original.

* **Règles** d&#39;inclusion de type MIME : Lorsqu’un fichier avec un type MIME spécifique est traité, le type MIME est d’abord vérifié par rapport à la valeur des types MIME exclus pour la spécification de rendu. En cas de correspondance avec cette liste, ce rendu spécifique n’est pas généré pour la ressource (liste bloquée). Dans le cas contraire, le type MIME est comparé au type MIME inclus et, si une correspondance est trouvée, le rendu est généré (liste autorisée).

* **Rendu** FPO spécial : Lorsque vous placez des fichiers de grande taille [!DNL Experience Manager] dans [!DNL Adobe InDesign] des documents, un professionnel de la création attend un certain temps après avoir [placé un fichier](https://helpx.adobe.com/fr/indesign/using/placing-graphics.html). Pendant ce temps, l’utilisateur ne peut pas utiliser [!DNL InDesign]. Cela interrompt le flux créatif et a un impact négatif sur l’expérience utilisateur. Adobe enables temporarily placing small-sized renditions in [!DNL InDesign] documents to begin with, which can be replaced with full-resolution assets on-demand later. [!DNL Experience Manager] fournit des rendus utilisés uniquement pour placement (FPO). Ces rendus FPO ont une taille de fichier réduite, mais présentent les mêmes proportions.

Le profil de traitement peut inclure un rendu FPO (For Placement Only). See [!DNL Adobe Asset Link] [documentation](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) to understand if you need to turn it on for your processing profile. Pour plus d’informations, voir la [documentation complète d’Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html).

### Créer un profil standard {#create-standard-profile}

Pour créer un profil de traitement standard, procédez comme suit :

1. Les administrateurs ont accès à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > Profils **[!UICONTROL de]** traitement. Cliquez sur **[!UICONTROL Créer]**.
1. Fournissez un nom qui vous aide à identifier de manière unique le profil lors de l’application à un dossier.
1. Pour générer des rendus FPO, dans l’onglet **[!UICONTROL Standard]** , activez **[!UICONTROL Créer un rendu FPO]**. Saisissez une valeur de **[!UICONTROL qualité]** comprise entre 1 et 100.
1. Pour générer d’autres rendus, cliquez sur **[!UICONTROL Ajouter nouveau]** et fournissez les informations suivantes :

   * Nom de fichier de chaque rendu.
   * Format de fichier (PNG, JPEG, GIF ou WebP) de chaque rendu.
   * Largeur et hauteur en pixels de chaque rendu. Si les valeurs ne sont pas spécifiées, la taille en pixels de l’image d’origine est utilisée.
   * Qualité en pourcentage de chaque rendu JPEG et WebP.
   * Types MIME inclus et exclus pour définir l’applicabilité d’un profil.

   ![processing-profiles-adding](assets/processing-profiles-image.png)

1. Cliquez sur **[!UICONTROL Save]**.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Cas d’utilisation et de profil personnalisés {#custom-config}

Il [!DNL Asset Compute Service] prend en charge divers cas d’utilisation, tels que le traitement par défaut, le traitement de formats spécifiques à l’Adobe, tels que les fichiers Photoshop, et l’implémentation de traitements personnalisés ou spécifiques à l’organisation. La personnalisation du processus de mise à jour des actifs de gestion des actifs de gestion des actifs requise par le passé est gérée automatiquement ou via la configuration des profils de traitement. Si ces options de traitement ne répondent pas aux besoins de l&#39;entreprise, l&#39;Adobe recommande de développer et d&#39;utiliser [!DNL Asset Compute Service] pour étendre les fonctionnalités par défaut. Pour un aperçu, voir [comprendre l&#39;extensibilité et quand l&#39;utiliser](https://docs.adobe.com/content/help/en/asset-compute/using/extend/understand-extensibility.html).

>[!NOTE]
>
>Adobe recommande d&#39;utiliser une application personnalisée uniquement lorsque les besoins de l&#39;entreprise ne peuvent pas être satisfaits à l&#39;aide des configurations par défaut ou du profil standard.

Il peut transformer des formats d’image, de vidéo, de document et d’autres formats de fichier en différents rendus, y compris des miniatures, du texte extrait, des métadonnées et des archives.

Les développeurs peuvent utiliser le [!DNL Asset Compute Service] pour [créer des applications](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html) personnalisées qui répondent aux cas d’utilisation pris en charge. [!DNL Experience Manager] Vous pouvez appeler ces applications personnalisées à partir de l’interface utilisateur en utilisant des profils personnalisés configurés par les administrateurs. [!DNL Asset Compute Service] prend en charge les cas d’utilisation suivants d’appel de services externes :

* Utilisez [!DNL Adobe Photoshop]l’API [](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout) ImageCutout et enregistrez le résultat en tant que rendu.
* Appelez des systèmes tiers pour mettre à jour des données, par exemple un système PIM.
* Utilisez [!DNL Photoshop] l’API pour générer divers rendus en fonction du modèle Photoshop.
* Utilisez l’API [de Lightroom](https://github.com/AdobeDocs/lightroom-api-docs#supported-features) Adobe pour optimiser les ressources assimilées et les enregistrer en tant que rendus.

>[!NOTE]
>
>Vous ne pouvez pas modifier les métadonnées standard à l’aide des applications personnalisées. Vous pouvez uniquement modifier des métadonnées personnalisées.

### Create a custom profile {#create-custom-profile}

Pour créer un profil personnalisé, procédez comme suit :

1. Les administrateurs ont accès à **[!UICONTROL Outils > Ressources > Profils]** de traitement. Cliquez sur **[!UICONTROL Créer]**.
1. Cliquez sur l’onglet **[!UICONTROL Personnalisé]** . Click **[!UICONTROL Add New]**. Indiquez le nom de fichier souhaité pour le rendu.
1. Fournissez les informations suivantes.

   * Nom de fichier de chaque rendu et extension de fichier prise en charge.
   * [URL de point de terminaison d’une application](https://docs.adobe.com/content/help/en/asset-compute/using/extend/deploy-custom-application.html)personnalisée Firefox. L’application doit provenir de la même organisation que le compte du Experience Manager.
   * Ajoutez Paramètres du service pour [transmettre des informations ou des paramètres supplémentaires à l’application](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html#pass-custom-parameters)personnalisée.
   * Types MIME inclus et exclus pour limiter le traitement à quelques formats de fichier spécifiques.

   Cliquez sur **[!UICONTROL Save]**.

Les applications personnalisées sont des applications [Project Firefly](https://github.com/AdobeDocs/project-firefly) sans en-tête. L’application personnalisée récupère tous les fichiers fournis s’ils sont configurés avec un profil de traitement. L’application doit filtrer les fichiers.

>[!CAUTION]
>
>Si l’application et le [!DNL Experience Manager] compte Firefly ne proviennent pas de la même organisation, l’intégration ne fonctionne pas.

### Exemple d’un profil personnalisé {#custom-profile-example}

Pour illustrer l’utilisation des profils personnalisés, prenons un exemple d’utilisation pour appliquer du texte personnalisé aux images de campagne. Vous pouvez créer un profil de traitement qui utilise l’API Photoshop pour modifier les images.

L’intégration du service Asset Compute permet au Experience Manager de transmettre ces paramètres à l’application personnalisée à l’aide du champ Paramètres [!UICONTROL du] service. L’application personnalisée appelle ensuite l’API Photoshop et transmet ces valeurs à l’API. Par exemple, vous pouvez transmettre le nom de la police, la couleur du texte, le poids de texte et la taille du texte pour ajouter le texte personnalisé aux images de campagne.

![profil de traitement personnalisé](assets/custom-processing-profile.png)

*Figure : Utilisez le champ Paramètres [!UICONTROL du] service pour transmettre des informations supplémentaires aux paramètres prédéfinis générés dans l’application personnalisée. Dans cet exemple, lorsque des images de campagne sont téléchargées, les images sont mises à jour avec `Jumanji` du texte en `Arial-BoldMT` police.*

## Utiliser des profils de traitement pour traiter des ressources {#use-profiles}

Créez les profils de traitement personnalisé supplémentaire et appliquez-les à des dossiers spécifiques pour qu’Experience Manager traite les ressources chargées ou mises à jour dans ces dossiers. Le profil de traitement standard intégré par défaut est toujours exécuté, mais il n’est pas visible dans l’interface utilisateur. Si vous ajoutez un profil personnalisé, les deux profils sont utilisés pour traiter les ressources chargées.

Appliquez des profils de traitement aux dossiers en utilisant l’une des méthodes suivantes :

* Administrators can select a processing profile definition in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**, and use **[!UICONTROL Apply Profile to Folder(s)]** action. Cette action ouvre un navigateur de contenu qui vous permet d’accéder à des dossiers spécifiques, de les sélectionner et de confirmer l’application du profil.
* Users can select a folder in the Assets user interface, use **[!UICONTROL Properties]** action to open folder properties screen, click on the **[!UICONTROL Processing Profiles]** tab, and in the popup list, select the appropriate processing profile for that folder. Pour enregistrer les modifications, cliquez sur **[!UICONTROL Enregistrer et fermer]**.
   ![Application d’un profil de traitement à un dossier à partir de l’onglet Propriétés du fichier](assets/folder-properties-processing-profile.png)

>[!TIP]
>
>Un seul profil de traitement peut être appliqué à un dossier. Pour générer davantage de rendus, ajoutez d’autres définitions de rendu au profil de traitement existant.

Une fois qu’un profil de traitement a été appliqué à un dossier, toutes les nouvelles ressources chargées (ou mises à jour) dans ce dossier ou dans l’un de ses sous-dossiers sont traitées à l’aide du profil de traitement supplémentaire configuré. Ce dernier s’ajoute au profil par défaut standard.

>[!NOTE]
>
>Un profil de traitement appliqué à un dossier fonctionne pour l’ensemble de l’arborescence, mais il peut être remplacé par un autre qui est appliqué à un sous-dossier. Lorsque des ressources sont chargées dans un dossier, Experience Manager recherche un profil de traitement dans les propriétés du dossier conteneur. Si aucun dossier parent n’est appliqué, un dossier parent dans la hiérarchie est vérifié pour appliquer un profil de traitement.

Pour vérifier que les ressources sont traitées, prévisualisation les rendus générés dans la vue [!UICONTROL Rendus] dans le rail de gauche. Ouvrez la prévisualisation de ressources et ouvrez le rail de gauche pour accéder à la vue **[!UICONTROL Rendus]** . Les rendus spécifiques situés dans le profil de traitement, pour lesquels le type de la ressource correspond aux règles d’inclusion du type MIME, doivent être visibles et accessibles.

![rendus supplémentaires](assets/renditions-additional-renditions.png)

*Figure : Exemple de deux rendus supplémentaires générés par un profil de traitement appliqué au dossier parent.*

## Workflows de post-traitement {#post-processing-workflows}

S’il s’avère qu’un traitement supplémentaire des ressources est nécessaire, mais qu’il ne peut pas être effectué à l’aide des profils de traitement, des workflows de post-traitement peuvent être ajoutés à la configuration. Cela permet d’ajouter un traitement entièrement personnalisé en plus du traitement configurable à l’aide des microservices de ressources.

Les workflows de post-traitement, s’ils sont configurés, sont automatiquement exécutés par AEM une fois le traitement des microservices terminé. Il n’est pas nécessaire d’ajouter manuellement des lanceurs de workflows pour les déclencher. Voici quelques exemples :

* Étapes du workflow personnalisé de traitement des ressources.
* Intégrations pour ajouter des métadonnées ou des propriétés à des ressources provenant de systèmes externes (par exemple, des informations sur des produits ou des processus).
* Traitement supplémentaire effectué par des services externes.

L’ajout d’une configuration de workflow de post-traitement à Experience Manager comprend les étapes suivantes :

* Création d’un ou de plusieurs modèles de workflow. Les documents parlent de *modèles de workflow de post-traitement*, mais il s’agit de modèles de workflow Experience Manager standard.
* Ajout d’étapes de workflow spécifiques à ces modèles. Les étapes sont exécutées sur les ressources en fonction d’une configuration de modèle de workflow.
* Ajoutez l’étape [!UICONTROL Processus terminé du workflow Ressource de mise à jour DAM] à la fin. En ajoutant cette étape, vous êtes certain que Experience Manager sait à quel moment le traitement se termine et la ressource peut être marquée comme traitée ; en d’autres termes, *Nouvelle* s’affiche sur la ressource.
* Création d’une configuration pour le service d’exécution de workflow personnalisé, lequel permet de configurer l’exécution d’un modèle de workflow de post-traitement selon le chemin d’accès (emplacement du dossier) ou une expression régulière.

### Création de modèles de workflow de post-traitement {#create-post-processing-workflow-models}

Les modèles de workflow de post-traitement sont des modèles AEM standard. Créez des modèles différents si un autre traitement doit être exécuté pour différents emplacements de référentiel ou types de ressource.

Les étapes de traitement doivent être ajoutées en fonction des besoins. Vous pouvez utiliser n’importe quelle étape prise en charge, ainsi que n’importe quelle étape de workflow implémentée sur mesure.

Assurez-vous que la dernière étape de chaque workflow de post-traitement est `DAM Update Asset Workflow Completed Process`. La dernière étape permet de s’assurer qu’Experience Manager sait quand le traitement des ressources est terminé.

### Configuration de l’exécution du workflow de post-traitement {#configure-post-processing-workflow-execution}

Pour configurer les modèles du workflow de post-traitement à exécuter pour les ressources chargées ou mises à jour dans le système une fois le traitement des microservices de ressources terminé, il convient de configurer le service d’exécution de workflow personnalisé.

Ce service (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) est un service OSGi qui propose deux options de configuration :

* Workflows de post-traitement par chemin d’accès (`postProcWorkflowsByPath`) : plusieurs modèles de workflow peuvent être répertoriés en fonction de différents chemins de référentiel. Les chemins d’accès et les modèles doivent être séparés par un signe « deux-points ». Les chemins de référentiel simples sont pris en charge et doivent être associés à un modèle de workflow dans le chemin d’accès `/var`. Par exemple : `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Workflows de post-traitement par expression (`postProcWorkflowsByExpression`) : plusieurs modèles de workflows peuvent être répertoriés en fonction de différentes expressions régulières. Les expressions et les modèles doivent être séparés par un signe « deux-points ». L’expression régulière doit pointer directement vers le nœud Ressource et non vers l’un des rendus ou fichiers. Par exemple : `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>La configuration du service d’exécution de workflow personnalisé est la configuration d’un service OSGi. Pour en savoir plus sur le déploiement d’une configuration OSGi, voir [Déploiement sur Experience Manager](/help/implementing/deploying/overview.md).
>Contrairement aux déploiements des Managed Services et On-Premise Services d’AEM, la console web OSGi n’est pas directement disponible dans les déploiements Cloud Service.

Pour plus d’informations sur les étapes de workflow standard pouvant être utilisées dans le workflow de post-traitement, voir [Étapes du workflow de post-traitement](developer-reference-material-apis.md#post-processing-workflows-steps) (en anglais) dans la documentation de référence du développeur.

## Bonnes pratiques et restrictions {#best-practices-limitations-tips}

* Pour la conception des workflows, prenez en compte vos besoins pour tous les types de rendus. Si vous ne prévoyez pas la nécessité d’un rendu futur, supprimez son étape de création dans le workflow. Il est impossible par la suite de supprimer les rendus en masse. Les rendus superflus peuvent occuper beaucoup d’espace de stockage suite à une utilisation prolongée d’[!DNL Experience Manager]. Pour les ressources individuelles, vous pouvez supprimer manuellement les rendus à l’aide de l’interface utilisateur. Si plusieurs ressources sont concernées, vous pouvez, au choix, personnaliser [!DNL Experience Manager] pour supprimer des rendus spécifiques, ou supprimer les ressources et les charger à nouveau.
* Actuellement, la prise en charge se limite à la génération de rendus. La génération de nouveaux actifs n’est pas prise en charge.

>[!MORELIKETHIS]
>
>* [Présentation du service](https://docs.adobe.com/content/help/en/asset-compute/using/introduction.html)Asset Compute.
>* [Comprendre l&#39;extensibilité et quand l&#39;utiliser](https://docs.adobe.com/content/help/en/asset-compute/using/extend/understand-extensibility.html).
>* [Comment créer des applications](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html)personnalisées.
>* [Types MIME pris en charge pour divers cas](/help/assets/file-format-support.md)d’utilisation.


<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
