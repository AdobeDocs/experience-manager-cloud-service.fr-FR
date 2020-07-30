---
title: Configuration et utilisation des microservices de ressources pour le traitement des ressources
description: Découvrez comment configurer et utiliser les microservices de ressources basés sur le cloud pour traiter des ressources à grande échelle.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 253231d2c9bafbba72696db36e9ed46b8011c9b3
workflow-type: tm+mt
source-wordcount: '2246'
ht-degree: 56%

---


# Utiliser les microservices de ressources et les profils de traitement {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Les microservices de ressources permettent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services pour une gestion optimale des différents types de ressources et des options de traitement.

Le traitement des ressources dépend de la configuration définie dans les **[!UICONTROL Profils de traitement]**. Ceux-ci fournissent une configuration par défaut et permettent à l’administrateur d’ajouter une configuration plus précise pour le traitement des ressources. Les administrateurs peuvent créer et gérer les configurations des workflows de post-traitement, y compris la personnalisation facultative. La personnalisation des workflows autorise une extensibilité et une personnalisation complète.

Les microservices de ressources vous permettent de traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles qu’ImageMagick.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Une vue de haut niveau du traitement des ressources](assets/asset-microservices-flow.png "Une vue de haut niveau du traitement des ressources")

>[!NOTE]
>
>The asset processing described here replaces the `DAM Update Asset` workflow model that exists in the previous versions of [!DNL Experience Manager]. La plupart des étapes standard liées aux métadonnées et à la génération du rendu sont remplacées par le traitement des microservices de ressources, tandis que les étapes restantes, le cas échéant, peuvent être remplacées par la configuration du workflow de post-traitement.

## Comprendre les options de traitement des ressources {#get-started}

Experience Manager permet d’effectuer les niveaux de traitement suivants.

| Configuration | Description | Cas d’utilisation couverts |
|---|---|---|
| [Configuration par défaut](#default-config) | Il est disponible en l’état et ne peut pas être modifié. Cette configuration fournit une fonctionnalité de génération de rendu de base. | Miniatures standard utilisées par l’interface [!DNL Assets] utilisateur (48, 140 et 319 px); Grande prévisualisation (rendu Web - 1 280 px); extraction des métadonnées et du texte. |
| [Configuration standard](#standard-config) | Configuré par les administrateurs via l’interface utilisateur uniquement. Fournit davantage d’options pour la génération de rendu que la configuration par défaut ci-dessus. | modifier le format et la résolution des images ; générer des rendus FPO. |
| [Configuration personnalisée](#custom-config) | Configuré par les administrateurs via l’interface utilisateur pour appeler des travailleurs personnalisés qui prennent en charge des exigences plus complexes. Exploitation d’un cloud natif [!DNL Asset Compute Service]. | Voir les cas [d’utilisation](#custom-config)autorisés. |

Pour créer des profils de traitement personnalisés répondant à des besoins spécifiques (pour les intégrer à d’autres systèmes, par exemple), reportez-vous à la section [Workflows de post-traitement](#post-processing-workflows).

## Formats de fichiers pris en charge {#supported-file-formats}

Les microservices de ressources prennent en charge un large éventail de formats de fichiers pour la génération de rendus ou l’extraction de métadonnées. Pour consulter la liste complète, voir [Formats de fichiers pris en charge](file-format-support.md).

## Configuration par défaut {#default-config}

Certains paramètres par défaut sont préconfigurés pour garantir que les rendus par défaut requis dans le Experience Manager sont disponibles. La configuration par défaut garantit également la disponibilité des opérations d’extraction des métadonnées et d’extraction de texte. Les utilisateurs peuvent commencer à charger ou à mettre à jour immédiatement les ressources, et le traitement de base est disponible par défaut.

Avec la configuration par défaut, seul le profil de traitement de base est configuré. Un tel profil de traitement n’est pas visible dans l’interface utilisateur et vous ne pouvez pas le modifier. Il s’exécute toujours pour traiter les ressources chargées. Such a default processing profile ensures that the basic processing required by [!DNL Experience Manager] is completed on all assets.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## profil standard {#standard-config}

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
   * Format de fichier (PNG, JPEG ou GIF) de chaque rendu.
   * Largeur et hauteur en pixels de chaque rendu. Si les valeurs ne sont pas spécifiées, la taille en pixels de l’image d’origine est utilisée.
   * Qualité en pourcentage de chaque rendu JPEG.
   * Types MIME inclus et exclus pour définir l’applicabilité d’un profil.

![processing-profiles-adding](assets/processing-profiles-adding.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

La vidéo suivante montre l&#39;utilité et l&#39;utilisation du profil standard.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Cas d’utilisation et de profil personnalisés {#custom-config}

**Éléments**&#x200B;à déterminer :

* Liens croisés globaux avec le contenu d’extensibilité.
* Indiquez comment obtenir l’URL du collaborateur. URL du collaborateur pour les environnements Dev, Stage et Prod.
* Mappage des mentions des paramètres de service. Lien vers un article de service de calcul.
* Revue du flux partagé sur le ticket Jira.

Certains cas complexes d’utilisation du traitement des actifs ne peuvent pas être réalisés à l’aide de configurations par défaut, car les besoins des organisations sont variés. offres d&#39;Adobe [!DNL Asset Compute Service] pour de tels cas d&#39;utilisation. Il s’agit d’un service évolutif et extensible permettant de traiter des ressources numériques. Il peut transformer des formats d’image, de vidéo, de document et d’autres formats de fichier en différents rendus, y compris des miniatures, du texte extrait et des métadonnées et des archives.

Les développeurs peuvent utiliser le service Asset Compute pour créer des agents personnalisés spécialisés qui répondent à des cas d’utilisation complexes et prédéfinis. [!DNL Experience Manager] peuvent appeler ces travailleurs personnalisés à partir de l’interface utilisateur en utilisant des profils personnalisés configurés par les administrateurs. [!DNL Asset Compute Service] prend en charge les cas d’utilisation suivants :

* Générez des balises actives personnalisées et améliorées pour les ressources numériques à l’aide de Adobe Sensei.
* Générez le masque de recadrage d’un sujet à l’aide de l’Adobe Sensei.
* Récupérez les informations de métadonnées de produit du système PIM et faites en sorte que les métadonnées fassent partie du fichier binaire lors de l’assimilation de la ressource.
* Modifiez la couleur d’arrière-plan d’une image transparente à l’aide de [!DNL Adobe Photoshop] l’API.
* Retouchez une image à l’aide de [!DNL Photoshop] l’API.
* Désélectionnez une image à l’aide de [!DNL Adobe Lightroom] l’API.

>[!NOTE]
>
>Vous ne pouvez pas modifier les métadonnées standard à l’aide des travailleurs personnalisés. Vous pouvez uniquement modifier des métadonnées personnalisées.

### Create a custom profile {#create-custom-profile}

Pour créer un profil personnalisé, procédez comme suit :

1. Les administrateurs ont accès à **[!UICONTROL Outils > Ressources > Profils]** de traitement. Cliquez sur **[!UICONTROL Créer]**.
1. Click on **[!UICONTROL Custom]** tab. Click **[!UICONTROL Add New]**. Indiquez le nom de fichier souhaité pour le rendu.
1. Fournissez les informations suivantes et cliquez sur **[!UICONTROL Enregistrer]**.

   * Nom de fichier de chaque rendu et extension de fichier prise en charge.
   * URL de point de terminaison d’une application personnalisée Firefox. L’application doit provenir de la même organisation que le compte du Experience Manager.
   * Ajoutez les paramètres du service si nécessaire.
   * Types MIME inclus et exclus pour définir l’applicabilité d’un profil.

![profil de traitement personnalisé](assets/custom-processing-profile.png)

>[!CAUTION]
>
>Si l’application et le [!DNL Experience Manager] compte Firefly ne proviennent pas de la même organisation, l’intégration ne fonctionne pas.

## Utiliser des profils de traitement pour traiter des ressources {#use-profiles}

Créez les profils de traitement personnalisé supplémentaire et appliquez-les à des dossiers spécifiques pour qu’Experience Manager traite les ressources chargées ou mises à jour dans ces dossiers. Le profil de traitement standard intégré par défaut est toujours exécuté, mais il n’est pas visible dans l’interface utilisateur. Si vous ajoutez un profil personnalisé, les deux profils sont utilisés pour traiter les ressources chargées.

Appliquez des profils de traitement aux dossiers en utilisant l’une des méthodes suivantes :

* Les administrateurs peuvent sélectionner une définition de profil de traitement dans **[!UICONTROL Outils > Ressources > Profils de traitement]** et utiliser l’action **[!UICONTROL Appliquer le profil au(x) dossier(s)]**. Cette action ouvre un navigateur de contenu qui vous permet d’accéder à des dossiers spécifiques, de les sélectionner et de confirmer l’application du profil.
* Users can select a folder in the Assets user interface, use **[!UICONTROL Properties]** action to open folder properties screen, click on the **[!UICONTROL Processing Profiles]** tab, and in the popup list, select the correct processing profile for that folder. Pour enregistrer les modifications, cliquez sur **[!UICONTROL Enregistrer et fermer]**.

>[!NOTE]
>
>Un seul profil de traitement peut être appliqué à chaque dossier. Pour générer davantage de rendus, ajoutez d’autres définitions de rendu au profil de traitement existant.

Une fois qu’un profil de traitement a été appliqué à un dossier, toutes les nouvelles ressources chargées (ou mises à jour) dans ce dossier ou dans l’un de ses sous-dossiers sont traitées à l’aide du profil de traitement supplémentaire configuré. Ce traitement s’ajoute au profil par défaut standard. Si vous appliquez plusieurs profils à un dossier, les ressources chargées ou mises à jour sont traitées à l’aide de chacun d’eux.

>[!NOTE]
>
>Un profil de traitement appliqué à un dossier fonctionne pour l’arborescence entière, mais peut être remplacé par un autre profil appliqué à un sous-dossier. Lorsque des ressources sont chargées dans un dossier, Experience Manager recherche un profil de traitement dans les propriétés du dossier conteneur. Si aucun dossier parent n’est appliqué, un dossier parent dans la hiérarchie est contrôlé pour qu’un profil de traitement s’applique.

Les utilisateurs peuvent vérifier que le traitement a bien eu lieu en ouvrant une ressource récemment chargée dont le traitement est terminé, en ouvrant l’aperçu de la ressource et en cliquant sur la vue **[!UICONTROL Rendus]** du rail de gauche. Les rendus spécifiques situés dans le profil de traitement, pour lesquels le type de la ressource correspond aux règles d’inclusion du type MIME, doivent être visibles et accessibles.

![rendus supplémentaires](assets/renditions-additional-renditions.png)

*Figure : Exemple de deux rendus supplémentaires générés par un profil de traitement appliqué au dossier parent.*

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
