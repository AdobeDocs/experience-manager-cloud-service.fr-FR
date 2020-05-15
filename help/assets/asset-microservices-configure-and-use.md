---
title: Configuration et utilisation des microservices de ressources pour le traitement des ressources
description: Découvrez comment configurer et utiliser les microservices de ressources basés sur le cloud pour traiter des ressources à grande échelle.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 367456bfad25a83a36ffe45e2d6092367740cd92
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 92%

---


# Prise en main des microservices de ressources {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services pour une gestion optimale des différents types de ressources et des options de traitement.

Le traitement des ressources dépend de la configuration définie dans les **[!UICONTROL Profils de traitement]**. Ceux-ci fournissent une configuration par défaut et permettent à l’administrateur d’ajouter une configuration plus précise pour le traitement des ressources. Les administrateurs peuvent créer et gérer les configurations des workflows de post-traitement, y compris la personnalisation facultative. La personnalisation des workflows autorise une extensibilité et une personnalisation complète.

Les microservices de ressources vous permettent de traiter un [large éventail de types](/help/assets/file-format-support.md) de fichiers couvrant davantage de formats prêts à l’emploi que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles que ImageMagick.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![vue de haut niveau du](assets/asset-microservices-flow.png "traitement des actifsvue de haut niveau du traitement des actifs")

>[!NOTE]
>
> Le traitement des ressources décrit ici remplace le modèle de workflow `DAM Update Asset` existant dans les versions précédentes d’Experience Manager. La plupart des étapes standard liées aux métadonnées et à la génération du rendu sont remplacées par le traitement des microservices de ressources, tandis que les étapes restantes, le cas échéant, peuvent être remplacées par la configuration du workflow de post-traitement.

## Prise en main du traitement des ressources {#get-started}

Une préconfiguration par défaut est utilisée pour le traitement des ressources avec les microservices de ressources, ce qui garantit la disponibilité des rendus par défaut requis par le système. De ce fait, les opérations d’extraction de métadonnées et de texte sont également disponibles. Les utilisateurs peuvent commencer à charger ou à mettre à jour immédiatement les ressources, et le traitement de base est disponible par défaut.

Pour répondre à des besoins spécifiques en termes de génération de rendu ou de traitement des ressources, un administrateur AEM peut créer des [!UICONTROL Profils de traitement] supplémentaires. Les utilisateurs peuvent affecter un ou plusieurs des profils disponibles à des dossiers spécifiques afin qu’un traitement supplémentaire soit réalisé ; par exemple, pour générer des rendus spécifiques au web, à des appareils mobiles et à des tablettes. La vidéo suivante explique comment créer et appliquer des [!UICONTROL Profils de traitement] et comment accéder aux rendus qui ont été créés.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

Pour modifier le profil existant, reportez-vous à la section [Configurations des microservices de ressources](#configure-asset-microservices).
Pour créer des profils de traitement personnalisés répondant à des besoins spécifiques (pour les intégrer à d’autres systèmes, par exemple), reportez-vous à la section [Workflows de post-traitement](#post-processing-workflows).

## Configurations des microservices de ressources {#configure-asset-microservices}

Pour configurer des microservices de ressources, les administrateurs peuvent utiliser l’interface de configuration disponible sous **[!UICONTROL Outils > Ressources > Profils de traitement]**.

### Configuration par défaut {#default-config}

Avec la configuration par défaut, seul le profil de traitement standard est configuré. Le traitement standard n’est pas visible dans l’interface utilisateur et vous ne pouvez pas le modifier. Il s’exécute toujours pour traiter les ressources chargées. Un profil de traitement standard permet de s’assurer que l’intégralité du traitement de base requis par Experience Manager est terminé sur toutes les ressources.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png) -->

Le profil de traitement standard fournit la configuration de traitement suivante :

* Miniatures standard utilisées par l’interface utilisateur d’Assets (48, 140 et 319 pixels)
* Aperçu grand format (rendu web : 1 280 pixels)
* Extraction de métadonnées
* Extraction de texte

### Formats de fichiers pris en charge {#supported-file-formats}

Les microservices de ressources prennent en charge un large éventail de formats de fichiers pour la génération de rendus ou l’extraction de métadonnées. Pour consulter la liste complète, voir [Formats de fichiers pris en charge](file-format-support.md).

### Ajout de profils de traitement {#processing-profiles}

Vous pouvez ajouter des profils de traitement à l’aide de l’action **[!UICONTROL Créer]**.

Chaque configuration de profil de traitement comprend une liste de rendus. Pour chaque rendu, vous pouvez spécifier les éléments suivants :

* Nom du rendu.
* Format de rendu pris en charge, tel que JPEG, PNG ou GIF.
* Largeur et hauteur de rendu en pixels. Si cette valeur n’est pas spécifiée, la taille totale en pixels de l’image d’origine est utilisée.
* Qualité de rendu du format JPEG, exprimée en pourcentage.
* Types MIME inclus et exclus pour définir l’applicabilité d’un profil.

![processing-profiles-adding](assets/processing-profiles-adding.png)

Lorsque vous créez et enregistrez un nouveau profil de traitement, il est ajouté à la liste des profils de traitement configurés. Vous pouvez appliquer ces profils de traitement aux dossiers dans la hiérarchie de dossiers afin qu’ils opèrent dans le traitement et le chargement des ressources.

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) -->

#### Largeur et hauteur du rendu {#rendition-width-height}

La spécification de hauteur et de largeur du rendu fournit des tailles maximales de l’image de sortie générée. Le microservice de ressources tente de générer le rendu le plus grand possible, avec une largeur et une hauteur ne dépassant pas les valeurs spécifiées. Les proportions sont conservées, c’est-à-dire qu’elles sont identiques à l’original.

Une valeur vide signifie que le traitement des ressources utilise, par défaut, la taille en pixels de l’original.

#### Règles d’inclusion du type MIME {#mime-type-inclusion-rules}

Lors du traitement d’une ressource avec un type MIME spécifique, ce dernier est d’abord comparé à la valeur des types MIME exclus pour la spécification de rendu. En cas de correspondance avec cette liste, ce rendu spécifique n’est pas généré pour la ressource (il est mis sur liste noire ou « blacklisté »).

Dans le cas contraire, le type MIME est comparé au type MIME inclus et, si une correspondance est trouvée, le rendu est généré (il est alors mis sur liste blanche ou « whitelisté »).

#### Rendu FPO spécial {#special-fpo-rendition}

Lorsque vous transférez des ressources volumineuses d’AEM vers des documents Adobe InDesign, un professionnel de la création doit attendre un temps conséquent avant de [placer une ressource](https://helpx.adobe.com/fr/indesign/using/placing-graphics.html). Pendant ce temps, l’utilisateur ne peut pas utiliser InDesign. Cela interrompt le flux créatif et a un impact négatif sur l’expérience utilisateur. Adobe permet de placer temporairement dans des documents InDesign les rendus de petite taille, qui peuvent être remplacés ultérieurement par des ressources pleine résolution à la demande. Experience Manager fournit des rendus utilisés uniquement pour placement (FPO). Ces rendus FPO ont une taille de fichier réduite, mais présentent les mêmes proportions.

Le profil de traitement peut inclure un rendu FPO (For Placement Only). Consultez la [documentation](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) d’Adobe Asset Link pour savoir si vous devez l’activer pour votre profil de traitement. Pour plus d’informations, voir la [documentation complète d’Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html).

## Utilisation de microservices de ressources pour traiter des ressources {#use-asset-microservices}

Créez les profils de traitement personnalisé supplémentaire et appliquez-les à des dossiers spécifiques pour qu’Experience Manager traite les ressources chargées ou mises à jour dans ces dossiers. Le profil de traitement standard intégré par défaut est toujours exécuté, mais il n’est pas visible dans l’interface utilisateur. Si vous ajoutez un profil personnalisé, les deux profils sont utilisés pour traiter les ressources chargées.

Pour que les profils de traitement soient appliqués aux dossiers, deux méthodes sont possibles :

* Les administrateurs peuvent sélectionner une définition de profil de traitement dans **[!UICONTROL Outils > Ressources > Profils de traitement]** et utiliser l’action **[!UICONTROL Appliquer le profil au(x) dossier(s)]**. Cette action ouvre un navigateur de contenu qui vous permet d’accéder à des dossiers spécifiques, de les sélectionner et de confirmer l’application du profil.
* Les utilisateurs peuvent sélectionner un dossier dans l’interface utilisateur d’Assets, exécuter l’action **[!UICONTROL Propriétés]** pour ouvrir l’écran des propriétés du dossier, cliquer sur l’onglet **[!UICONTROL Profils de traitement]** puis, dans le menu déroulant, sélectionner le profil de traitement approprié pour ce dossier. L’option choisie sera enregistrée lors de l’exécution de l’action **[!UICONTROL Enregistrer et fermer]**.

>[!NOTE]
>
>Un seul profil de traitement peut être appliqué à chaque dossier. Si davantage de rendus doivent être générés, vous pouvez ajouter des définitions de rendu au profil de traitement.

Une fois qu’un profil de traitement a été appliqué à un dossier, toutes les nouvelles ressources chargées (ou mises à jour) dans ce dossier ou dans l’un de ses sous-dossiers sont traitées à l’aide du profil de traitement supplémentaire configuré. Ce dernier s’ajoute au profil par défaut standard. Si vous appliquez plusieurs profils à un dossier, les ressources chargées ou mises à jour sont traitées à l’aide de chacun d’eux.

>[!NOTE]
>
>Lorsque des ressources sont chargées dans un dossier, Experience Manager recherche un profil de traitement dans les propriétés du dossier conteneur. Si aucun profil de traitement n’est appliqué, la recherche se poursuit vers le haut de l’arborescence de dossiers jusqu’à ce qu’un profil appliqué soit trouvé. Celui-ci est alors utilisé pour la ressource. Cela signifie qu’un profil de traitement appliqué à un dossier fonctionne pour l’ensemble de l’arborescence, mais qu’il peut être remplacé par un autre qui est appliqué à un sous-dossier.

Les utilisateurs peuvent vérifier que le traitement a bien eu lieu en ouvrant une ressource récemment chargée dont le traitement est terminé, en ouvrant l’aperçu de la ressource et en cliquant sur la vue **[!UICONTROL Rendus]** du rail de gauche. Les rendus spécifiques situés dans le profil de traitement, pour lesquels le type de la ressource correspond aux règles d’inclusion du type MIME, doivent être visibles et accessibles.

![rendus-supplémentaires](assets/renditions-additional-renditions.png)*Figure : Exemple de deux rendus supplémentaires générés par un profil de traitement appliqué au dossier parent*

## Workflows de post-traitement {#post-processing-workflows}

S’il s’avère qu’un traitement supplémentaire des ressources est nécessaire, mais qu’il ne peut pas être effectué à l’aide des profils de traitement, des workflows de post-traitement peuvent être ajoutés à la configuration. Cela permet d’ajouter un traitement entièrement personnalisé en plus du traitement configurable à l’aide des microservices de ressources.

Les workflows de post-traitement, s’ils sont configurés, sont automatiquement exécutés par AEM une fois le traitement des microservices terminé. Il n’est pas nécessaire d’ajouter manuellement de lanceurs de workflows pour les déclencher.

Voici quelques exemples :

* Étapes de workflow personnalisées pour le traitement des ressources ; il s’agit, par exemple, du code Java à utiliser pour générer des rendus à partir de formats de fichiers propriétaires.
* Intégrations pour ajouter des métadonnées ou des propriétés à des ressources provenant de systèmes externes, des informations sur des produits ou des processus, par exemple.
* Traitement supplémentaire effectué par des services externes.

L’ajout d’une configuration de workflow de post-traitement à Experience Manager comprend les étapes suivantes :

* Création d’un ou de plusieurs modèles de workflow. Nous les appellerons « modèles de workflow de post-traitement », mais il s’agit en fait de modèles de workflow AEM standard.
* Ajout d’étapes de workflow spécifiques à ces modèles. Ces étapes seront exécutées sur les ressources en fonction de la configuration du modèle de workflow.
* La dernière étape d’un tel modèle doit être `DAM Update Asset Workflow Completed Process`. Elle est nécessaire pour s’assurer qu’AEM sait que le traitement a pris fin et que la ressource peut désormais être marquée comme traitée (« Nouveau »).
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
> Contrairement aux déploiements des Managed Services et On-Premise Services d’AEM, la console Web OSGi n’est pas directement disponible dans les déploiements de Cloud Service.

Pour plus d’informations sur les étapes de workflow standard pouvant être utilisées dans le workflow de post-traitement, voir [Étapes du workflow de post-traitement](developer-reference-material-apis.md#post-processing-workflows-steps) (en anglais) dans la documentation de référence du développeur.

## Best practices and limitations {#best-practices-limitations-tips}

* Tenez compte de vos besoins pour tous les types de rendus lors de la conception de workflows. Si vous ne prévoyez pas la nécessité d’un rendu à l’avenir, supprimez l’étape de création du flux de travail. Les rendus ne peuvent pas être supprimés en bloc par la suite. Les rendus non désirés peuvent prendre beaucoup d’espace d’enregistrement après une utilisation prolongée de [!DNL Experience Manager]. Pour les fichiers individuels, vous pouvez supprimer des rendus manuellement de l’interface utilisateur. Pour plusieurs fichiers, vous pouvez soit personnaliser [!DNL Experience Manager] la suppression de rendus spécifiques, soit supprimer les fichiers et les télécharger à nouveau.
