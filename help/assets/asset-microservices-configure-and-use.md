---
title: Configuration et utilisation des microservices de ressources pour le traitement des ressources
description: Découvrez comment configurer et utiliser les microservices de ressources natifs du cloud pour traiter les ressources à l’échelle.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 68b2214a4c8941365120bdef670e89b4c9058966

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

Le traitement des ressources dépend de la configuration du **[!UICONTROL de]** traitement, qui fournit une configuration par défaut et permet à un administrateur d’ajouter une configuration de traitement des ressources plus spécifique. Les administrateurs peuvent créer et gérer les configurations des  de post-traitement, y compris la personnalisation facultative. La personnalisation des  de permet l’extensibilité et la personnalisation complète.

Un flux de haut niveau pour le traitement des ressources est en dessous.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![asset-microservices-flow](assets/asset-microservices-flow.png)

>[!NOTE]
>
> Le traitement des ressources décrit ici remplace le modèle de `DAM Update Asset` flux de travail existant dans les versions précédentes d’Experience Manager. La plupart des étapes standard de génération de rendu et liées aux métadonnées sont remplacées par le traitement des microservices de ressources, et les étapes restantes, le cas échéant, peuvent être remplacées par la configuration du processus de post-traitement.

## Prise en main du traitement des ressources {#get-started}

Le traitement des ressources avec les microservices de ressources est préconfiguré avec une configuration par défaut, garantissant que les rendus par défaut requis par le système sont disponibles. Il s’assure également que les métadonnées   et le texte  les opérations de  sont disponibles. Les utilisateurs peuvent immédiatement  télécharger ou mettre à jour des ressources et le traitement de base est disponible par défaut.

Pour des besoins spécifiques de génération de rendu ou de traitement des ressources, un administrateur AEM peut créer des de [!UICONTROL traitement supplémentaires]. Les utilisateurs peuvent affecter un ou plusieurs des  de disponibles à des dossiers spécifiques afin d’effectuer un traitement supplémentaire. Par exemple, pour générer des rendus spécifiques au Web, aux mobiles et aux tablettes. La vidéo suivante explique comment créer et appliquer des [!UICONTROL de] traitement et comment accéder aux rendus créés.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

Pour modifier les  existantes, voir [les configurations des microservices](#configure-asset-microservices)de ressources.
Pour créer un de traitement personnalisé  spécifique à vos besoins personnalisés, par exemple pour l’intégrer à d’autres systèmes, reportez-vous à la page [](#post-processing-workflows)de post-traitement.

## Configurations des microservices de ressources {#configure-asset-microservices}

Pour configurer les microservices de ressources, les administrateurs peuvent utiliser l’interface utilisateur de configuration sous **[!UICONTROL Outils > Ressources >]** de traitement.

### Configuration par défaut {#default-config}

Avec la configuration par défaut, seul le de traitement standard est configuré. Le  de traitement standard n’est pas visible dans l’interface utilisateur et vous ne pouvez pas le modifier. Il s’exécute toujours pour traiter les fichiers téléchargés. Un de traitement standard permet de s’assurer que tout le traitement de base requis par Experience Manager est terminé sur toutes les ressources.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png) -->

Le de traitement standard fournit la configuration de traitement suivante :

* Miniatures standard utilisées par l’interface utilisateur d’Asset (48, 140 et 319 px)
* Grand (rendu Web - 1 280 px)
* Extraction de métadonnées
* Extraction de texte

### Formats de fichiers pris en charge {#supported-file-formats}

Les microservices de ressources prennent en charge une grande variété de formats de fichier en termes de capacité à générer des rendus ou à extraire des métadonnées. Voir Formats [de fichier](file-format-support.md) pris en charge pour le  de complet.

### Ajouter de traitement supplémentaire {#processing-profiles}

Des  de traitement supplémentaires peuvent être ajoutées à l’aide de l’action **[!UICONTROL Créer]** .

Chaque configuration de  de traitement inclut un de rendus. Pour chaque rendu, vous pouvez spécifier les éléments suivants :

* Nom du rendu.
* Format de rendu pris en charge, tel que JPEG, PNG ou GIF.
* Largeur et hauteur du rendu en pixels. S’il n’est pas spécifié, la taille totale en pixels de l’image d’origine est utilisée.
* Qualité du rendu JPEG en pourcentage.
* Types MIME inclus et exclus pour définir l’applicabilité d’un  de.

![traitement--ajout](assets/processing-profiles-adding.png)

Lorsque vous créez et enregistrez un nouveau de traitement  il est ajouté au de l’ de traitement configuré. Vous pouvez appliquer ces  de traitement aux dossiers dans la hiérarchie de dossiers afin de les rendre efficaces pour le transfert de fichiers et le traitement de fichiers.

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) -->

#### Largeur et hauteur du rendu {#rendition-width-height}

La spécification de hauteur et de largeur du rendu fournit des tailles maximales de l’image de sortie générée. Le microservice d’actifs tente de générer le rendu le plus grand possible, dont la largeur et la hauteur ne sont pas supérieures à la largeur et à la hauteur spécifiées, respectivement. Les proportions sont conservées, c&#39;est-à-dire identiques à l&#39;original.

Une valeur vide signifie que le traitement des fichiers prend la dimension de pixel de l’original.

#### Règles d’inclusion de type MIME {#mime-type-inclusion-rules}

Lorsqu’un fichier avec un type MIME spécifique est traité, le type MIME est d’abord vérifié par rapport à la valeur des types MIME exclus pour la spécification de rendu. S’il correspond à ce , ce rendu spécifique n’est pas généré pour la ressource (&quot;liste noire&quot;).

Dans le cas contraire, le type MIME est vérifié par rapport au type MIME inclus. S’il correspond au  du, le rendu est généré (&quot;liste blanche&quot;).

#### Rendu FPO spécial {#special-fpo-rendition}

Lorsque vous importez des fichiers de grande taille d’AEM dans le Adobe InDesign, un professionnel de la création doit attendre longtemps avant de [placer un fichier](https://helpx.adobe.com/indesign/using/placing-graphics.html). En attendant, l’utilisateur ne peut pas utiliser InDesign. Cela interrompt le flux créatif et a un impact négatif sur l’expérience utilisateur. Adobe permet de commencer par le placement temporaire de rendus de petite taille dans le InDesign, qui peut être remplacé ultérieurement par des ressources à la demande en pleine résolution. Experience Manager fournit des rendus utilisés uniquement pour les emplacements (FPO). Ces rendus FPO ont une taille de fichier réduite, mais ont les mêmes proportions.

Le de traitement peut inclure un rendu FPO (pour placement uniquement). Consultez la [documentation](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) d’Adobe Asset Link pour savoir si vous devez l’activer pour vos  de traitement. Pour plus d’informations, voir la documentation [complète d’](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)Adobe Asset Link.

## Utiliser des microservices de ressources pour traiter des ressources {#use-asset-microservices}

Créez et appliquez le de traitement personnalisé supplémentaire aux dossiers spécifiques pour Experience Manager afin de traiter les fichiers téléchargés ou mis à jour dans ces dossiers. Le de traitement standard intégré par défaut est toujours exécuté, mais il n’est pas visible dans l’interface utilisateur. Si vous ajoutez un  de personnalisé, les deux  de sont utilisées pour traiter les ressources téléchargées.

Il existe deux façons d’appliquer des  de traitement aux dossiers :

* Les administrateurs peuvent sélectionner une définition de de traitement dans **[!UICONTROL Outils > Ressources >]** de traitement, puis utiliser l’action **[!UICONTROL Appliquer l’]** à un ou plusieurs dossiers. Il ouvre un navigateur de contenu qui vous permet de naviguer jusqu’à des dossiers spécifiques, de les sélectionner et de confirmer l’application du .
* Les utilisateurs peuvent sélectionner un dossier dans l’interface utilisateur Ressources, utiliser l’action **[!UICONTROL Propriétés]** pour ouvrir l’écran des propriétés du dossier, cliquer sur l’onglet **[!UICONTROL Profils de traitement]** et, dans la liste déroulante, sélectionner le profil de traitement approprié pour ce dossier. Le choix sera enregistré lors de l’action **[!UICONTROL Enregistrer et fermer]**.

>[!NOTE]
>
>Un seul  de traitement peut être appliqué à un dossier spécifique. Si vous avez besoin d’un plus grand nombre de rendus générés, vous pouvez ajouter d’autres définitions de rendus au  de traitement.

Une fois qu’un de traitement est appliqué à un dossier, toutes les nouvelles ressources transférées (ou mises à jour) dans ce dossier ou dans l’un de ses sous-dossiers sont traitées à l’aide du de traitement supplémentaire  configuré. Ce traitement supplémentaire s’ajoute au  de par défaut standard. Si vous appliquez plusieurs  à un dossier, les ressources téléchargées ou mises à jour sont traitées à l’aide de chacun de ces  de.

>[!NOTE]
>
>Lorsque des fichiers sont téléchargés dans un dossier, Experience Manager recherche dans les propriétés du dossier contenant une  de traitement. Si aucune n’est appliquée, elle remonte dans l’arborescence de dossiers jusqu’à ce qu’elle trouve un de traitement appliqué et l’utilise pour la ressource. Cela signifie qu’un de traitement appliqué à un dossier fonctionne pour l’arborescence entière, mais peut être surchargé avec un autre  appliqué à un sous-dossier.

Les utilisateurs peuvent vérifier que le traitement a eu lieu en ouvrant une ressource nouvellement chargée pour laquelle le traitement est terminé, en ouvrant le  de ressources et en cliquant sur le **[!UICONTROL Rendus]** du rail de gauche. Les rendus spécifiques dans le de traitement, pour lesquels le type de ressource spécifique correspond aux règles d’inclusion de type MIME, doivent être visibles et accessibles.

![additional-renditions](assets/renditions-additional-renditions.png)*Figure : Exemple de deux rendus supplémentaires générés par une  de traitement appliquée au dossier parent*

##  de post-traitement {#post-processing-workflows}

Dans le cas où un traitement supplémentaire des ressources est nécessaire et ne peut pas être effectué à l’aide du de traitement, un de post-traitement supplémentaire peut être ajouté à la configuration. Cela permet d’ajouter un traitement entièrement personnalisé en plus du traitement configurable à l’aide des microservices de ressources.

Les  de post-traitement, s’ils sont configurés, sont automatiquement exécutés par AEM une fois le traitement des microservices terminé. Il n’est pas nécessaire d’ajouter manuellement des lanceurs de processus pour les déclencher.

Voici quelques exemples :

* étapes de processus personnalisées pour le traitement des ressources, par exemple le code Java pour générer des rendus à partir de formats de fichier propriétaires.
* intégrations permettant d’ajouter des métadonnées ou des propriétés à des ressources provenant de systèmes externes, par exemple des informations sur les produits ou les processus.
* traitement supplémentaire effectué par des services externes

L’ajout d’une configuration de processus de post-traitement à Experience Manager comprend les étapes suivantes :

* Création d’un ou de plusieurs modèles de processus. Nous les appellerons &quot;modèles de processus de post-traitement&quot;, mais il s’agit de modèles de processus AEM standard.
* Ajout d’étapes de processus spécifiques à ces modèles. Ces étapes seront exécutées sur les ressources en fonction de la configuration du modèle de processus.
* La dernière étape d&#39;un tel modèle doit être l&#39; `DAM Update Asset Workflow Completed Process` étape. Ceci est nécessaire pour s’assurer qu’AEM sait que le traitement est terminé et que la ressource peut être marquée comme traitée (&quot;Nouveau&quot;).
* Création d’une configuration pour le service d’exécution de flux de travail personnalisé, qui permet de configurer l’exécution d’un modèle de processus de post-traitement par chemin d’accès (emplacement du dossier) ou par  régulier 

### Création de modèles de processus de post-traitement {#create-post-processing-workflow-models}

Les modèles de processus de post-traitement sont des modèles de processus AEM standard. Créez différents modèles si vous avez besoin d’un traitement différent pour différents emplacements de référentiel ou types de ressources.

Les étapes de traitement doivent être ajoutées en fonction des besoins. Vous pouvez utiliser toutes les étapes prises en charge disponibles, ainsi que toutes les étapes de processus implémentées sur mesure.

Assurez-vous que la dernière étape de chaque  de post-traitement est `DAM Update Asset Workflow Completed Process`. La dernière étape permet de s’assurer qu’Experience Manager sait quand le traitement des ressources est terminé.

### Configuration de l’exécution du processus de post-traitement {#configure-post-processing-workflow-execution}

Pour configurer les modèles de processus de post-traitement à exécuter pour les ressources téléchargées ou mises à jour dans le système une fois le traitement des microservices de ressources terminé, le service Runner de processus personnalisé doit être configuré.

Le service d’exécution de flux de travail personnalisé (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) est un service OSGi et propose deux options de configuration :

* de post-traitement par chemin (`postProcWorkflowsByPath`) : Plusieurs modèles de processus peuvent être répertoriés, en fonction de différents chemins d’accès au référentiel. Les chemins et les modèles doivent être séparés par un deux-points. Les chemins d’accès simples au référentiel sont pris en charge et doivent être mappés à un modèle de flux de travail dans le `/var` chemin d’accès. Par exemple : `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* de post-traitement  par  (`postProcWorkflowsByExpression`) : Plusieurs modèles de flux de travail peuvent être répertoriés, en fonction de différents   réguliers.   et les modèles doivent être séparés par un deux-points. Le  normal doit pointer directement vers le noeud Asset et non vers l’un des rendus ou des fichiers. Par exemple : `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Configuration de l’exécution de flux de travail personnalisé est une configuration d’un service OSGi. Voir [Déploiement sur Experience Manager](/help/implementing/deploying/overview.md) pour en savoir plus sur la manière de déployer une configuration OSGi.
> Contrairement aux déploiements sur site et aux services gérés d’AEM, la console Web OSGi n’est pas directement disponible dans les déploiements de services cloud.

Pour plus d’informations sur l’étape standard du flux de travail pouvant être utilisée dans le flux de post-traitement, voir les étapes du flux de [travail dans le flux](developer-reference-material-apis.md#post-processing-workflows-steps) de post-traitement dans la référence du développeur.
