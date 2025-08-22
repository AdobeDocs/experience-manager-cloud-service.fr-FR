---
title: Comment créer un formulaire adaptatif basé sur les composants principaux ?
description: Découvrez comment créer un formulaire adaptatif à l’aide de [!DNL Experience Manager Forms]. Les formulaires adaptatifs sont des formulaires HTML5 réactifs qui rationalisent la collecte et le traitement des informations. Découvrez comment créer un formulaire adaptatif basé sur un modèle de données de formulaire (FDM) et un schéma XML ou JSON.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: 8d43f28e62a865b6b990678544e0d9589f17722a
workflow-type: tm+mt
source-wordcount: '2340'
ht-degree: 77%

---

# Créer un formulaire adaptatif (composants principaux) {#creating-an-adaptive-form-core-components}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-an-adaptive-form-core-components.html) |
| AEM as a Cloud Service | Cet article |


Les formulaires adaptatifs vous permettent de créer des formulaires attrayants, réactifs, dynamiques et adaptatifs. AEM Forms fournit un assistant convivial destiné aux utilisateurs professionnels pour créer rapidement un Forms adaptatif. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif.

Avant de commencer, découvrez les types de composants de formulaires disponibles :

* [Composants principaux de formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) : il s’agit de composants de capture de données normalisés. Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique. Un développeur ou une développeuse peut facilement personnaliser et mettre en forme ces composants. Adobe recommande d’utiliser ces composants modernes et extensibles pour développer des formulaires adaptatifs.

* [Composants de base des formulaires adaptatifs](creating-adaptive-form.md) : il s’agit de composants de capture de données classiques (anciens). Vous pouvez continuer à les utiliser pour modifier votre formulaire adaptatif existant basé sur les composants de base. Si vous créez des formulaires, Adobe recommande d’utiliser les [composants principaux de formulaires adaptatifs](creating-adaptive-form-core-components.md).

![Assistant de création d’un formulaire adaptatif](/help/release-notes/assets/wizard.png)


## Conditions préalables

Pour créer un formulaire adaptatif, vous devez disposer des éléments suivants :


* **Activer les composants principaux de Forms adaptative pour votre environnement** : lorsque vous créez un programme, les composants principaux de Forms adaptative sont déjà activés pour votre environnement.  Installez la dernière version de pour activer les composants principaux de Forms adaptatif pour votre environnement AEM Cloud Service. Lors de l’activation des composants principaux pour votre environnement, les modèles et thèmes **Forms adaptative (composant principal)** sont ajoutés à votre environnement. Si votre version du SDK AEM est antérieure à 2023.02.0, [assurez-vous que l’indicateur `prerelease` est activé dans votre environnement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features), car les composants principaux des formulaires adaptatifs faisaient partie de la version préliminaire avant la version 2023.02.0.

* **Modèle de formulaire adaptatif** : un modèle fournit une structure de base et définit l’aspect, c’est-à-dire la mise en page et les styles, d’un formulaire adaptatif. Il comporte des composants pré-formatés contenant certaines propriétés et une certaine structure de contenu. Il fournit également les options permettant de définir un thème et une action d’envoi. Le thème définit l’aspect et l’action d’envoi définit l’action à entreprendre lors de l’envoi d’un formulaire adaptatif. Par exemple, l’envoi des données collectées à une source de données. Le service cloud fournit un modèle prêt à l’emploi, sans nom :

   * Le modèle `blank` est inclus dans chaque nouveau programme AEM Forms as a Cloud Service.
   * Vous pouvez installer le package de référence, via le gestionnaire de modules, pour ajouter le modèle `blank` à votre programme AEM Forms as a Cloud Service.
   * Vous pouvez également [créer un modèle de Forms adaptatif (composants principaux)](/help/forms/template-editor-core-components.md) à partir de zéro.
   * Vous pouvez également déployer des [exemples de modèles](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=fr) dans votre environnement. Vous pouvez ainsi créer rapidement des formulaires.

* **Un thème de formulaire adaptatif** : un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants.  Le modèle `Canvas` est inclus dans chaque nouveau programme AEM Forms as a Cloud Service. Vous pouvez également déployer des [exemples de thèmes](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=fr) dans votre environnement. Cela permet de commencer la mise en forme de vos formulaires et fournit une structure de base pour créer ou personnaliser un thème en fonction des besoins de votre entreprise.

  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Autorisations** : ajoutez vos utilisateurs et utilisatrices au groupe [!DNL forms-users]. Les membres du groupe [!DNL forms-users] ont les autorisations de créer un formulaire adaptatif. Pour obtenir une liste détaillée des groupes d’utilisateurs et d’utilisatrices spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Créer un formulaire adaptatif  {#create-an-adaptive-form-core-components}

1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms]. Il peut s’agir d’une instance cloud ou d’une instance de développement local.

1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant. Dans l’onglet Source, sélectionnez un modèle :

   ![Modèle de composants principaux](/help/forms/assets/core-components-template.png)

   Lorsque vous sélectionnez un modèle, un thème et l’action d’envoi spécifiée dans le modèle sont sélectionnés automatiquement. Le bouton **[!UICONTROL Créer]** est activé. Vous pouvez accéder aux onglets **[!UICONTROL Style]** ou **[!UICONTROL Envoi]** pour sélectionner un autre thème ou une autre action d’envoi. Si le modèle sélectionné ne spécifie pas de thème, le bouton de création reste désactivé. Vous pouvez accéder à l’onglet **[!UICONTROL Styles]** pour sélectionner manuellement un thème.

   >[!NOTE]
   >
   >
   > Si vous n’avez pas le modèle **Formulaires adaptatifs (composant principal)** sur votre environnement, vous devez [activer les composants principaux des formulaires adaptatifs pour votre environnement](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Quand vous activez des composants principaux pour votre environnement, le modèle **Formulaires adaptatifs (composant principal)** est ajouté à votre environnement.

1. Dans l’onglet **[!UICONTROL Style]**, sélectionnez un thème :

   * Lorsque le modèle sélectionné spécifie un thème, celui-ci est automatiquement sélectionné dans l’assistant. Vous pouvez également choisir un thème différent dans l’onglet Style.

   * Si le modèle sélectionné ne spécifie aucun thème, vous pouvez utiliser l’onglet Style pour en choisir un. Le bouton **[!UICONTROL Créer]** n’est activé qu’après la sélection d’un thème.

1. (Facultatif) Dans l’onglet Données, sélectionnez un modèle de données :

   * **Modèle de données de formulaire (FDM)** : un [modèle de données de formulaire](data-integration.md) vous permet d’intégrer des entités et des services provenant de sources de données disparates à un formulaire adaptatif. Choisissez le modèle de données de formulaire (FDM) si le formulaire adaptatif que vous créez implique l’extraction et l’écriture de données depuis et vers plusieurs sources de données.

   * **Schéma JSON** : [schéma JSON](adaptive-form-json-schema-form-model.md), notre formulaire adaptatif basé sur les composants principaux, permet une intégration transparente au système back-end de votre entreprise en vous permettant d’associer un schéma JSON, qui représente la structure des données générées ou consommées. Cette association permet aux créateurs et créatrices d’ajouter dynamiquement du contenu au formulaire adaptatif à l’aide des éléments du schéma. Les éléments du schéma sont facilement accessibles dans l’onglet Objets de modèle de données de l’explorateur de contenu au cours du processus de création. Tous les champs sont automatiquement ajoutés à tout formulaire adaptatif créé.

   Par défaut, tous les champs du schéma JSON associé sont automatiquement sélectionnés et convertis en composants de formulaire adaptatif correspondants, ce qui simplifie le processus de création. L’assistant vous permet, en outre, de sélectionner les champs à inclure dans le formulaire adaptatif au moyen de cases à cocher.

1. Dans l’onglet **[!UICONTROL Envoi]**, sélectionnez une action d’envoi :

   * Lorsque vous sélectionnez un modèle, l’action d’envoi spécifiée dans le modèle est sélectionnée automatiquement. Vous pouvez sélectionner une autre action d’envoi dans l’onglet Envoi. L’onglet **[!UICONTROL Envoi]** affiche toutes les actions d’envoi disponibles.

   * Lorsque le modèle sélectionné ne spécifie aucune action d’envoi, vous pouvez utiliser l’onglet **[!UICONTROL Envoi]** pour sélectionner une action d’envoi

1. (Facultatif) Dans l’onglet **[!UICONTROL Diffusion]**, vous pouvez spécifier une date de publication ou de d’annulation de publication pour un formulaire adaptatif.

1. Sélectionnez **[!UICONTROL Créer]**. Une boîte de dialogue pour spécifier le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif s’affiche :

   * **[!UICONTROL Titre]** Spécifie le nom d’affichage du formulaire. Le titre vous permet d’identifier le formulaire dans l’interface utilisateur [!DNL Experience Manager Forms] d’AEM Forms.
   * **[!UICONTROL Nom :]** indique le nom du formulaire. Un nœud portant le nom spécifié est créé dans le référentiel. Lorsque vous commencez à saisir un titre, la valeur du champ Nom est automatiquement générée. Vous pouvez modifier la valeur suggérée. Le champ Nom ne peut contenir que des caractères alphanumériques, des traits d’union et des traits de soulignement. Toutes les entrées non valides sont remplacées par un trait d’union.
   * **[!UICONTROL Chemin d’accès :]** indique l’emplacement d’enregistrement du formulaire adaptatif. Vous pouvez enregistrer le formulaire adaptatif directement sur `/content/dam/formsanddocuments` ou créer un dossier tel que `/content/dam/formsanddocuments/adaptiveforms` pour enregistrer un formulaire adaptatif. Assurez-vous de créer le dossier avant de l’utiliser dans le chemin d’accès. Le champ **[!UICONTROL Chemin d’accès]** ne crée pas de dossier automatiquement.

1. Sélectionnez **[!UICONTROL Créer]**. Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.  En fonction du type de formulaire adaptatif, les éléments de formulaire présents dans le schéma JSON <!--XFA form template, XML schema or --> ou le modèle de données de formulaire (FDM) associé sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

Vous pouvez maintenant faire glisser et déposer le [Composants principaux de Forms adaptatif](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) dans le conteneur de Forms adaptatif pour concevoir et créer le formulaire. Vous pouvez également consulter [https://aemcomponents.dev/](https://aemcomponents.dev/) pour afficher les composants principaux disponibles en action.

>[!NOTE]
>
> Vous pouvez également [créer un Forms adaptatif à l’aide de modèles de formulaire XFA (*.XDP)](/help/forms/create-adaptive-form-using-xfa-templates.md). Il permet de gagner du temps en réutilisant les champs des fichiers XDP directement dans le Forms adaptatif.

## Configurer l’action Envoyer pour un formulaire adaptatif {#configure-submit-action-for-form}

Une action Soumettre vous permet de choisir la destination des données capturées via un formulaire adaptatif. Elle est déclenchée lorsqu’un utilisateur ou une utilisatrice clique sur le bouton Soumettre d’un formulaire adaptatif. Les formulaires adaptatifs incluent certaines actions de soumission prêtes à l’emploi. Vous pouvez également étendre les actions de soumission par défaut pour créer votre propre action de soumission. Pour configurer une action de soumission pour votre formulaire :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.

1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.

   ![Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer une action d’envoi.](/help/forms/assets/adaptive-forms-submit-message.png)

1. Sélectionnez et configurez une **[!UICONTROL action d’envoi]** en fonction de vos besoins. Pour plus d’informations sur les actions d’envoi, voir [Action d’envoi de formulaire adaptatif](/help/forms/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Rediriger l’utilisateur ou l’utilisatrice vers une page ou afficher un message de remerciement lors de l’envoi du formulaire

Lors de la soumission d’un formulaire, vous pouvez rediriger la personne utilisatrice vers une autre page web ou un message. Pour rediriger la personne utilisatrice ou configurer le message de remerciement :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Envoi]**.

   ![Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer une page de redirection ou un message de remerciement.](/help/forms/assets/adaptive-forms-redirect-message.png)

   * Pour configurer une URL de redirection, pour l’option Lors de l’envoi, sélectionnez l’option **[!UICONTROL Rediriger vers l’URL]**, puis parcourez et sélectionnez une page AEM Sites, ou fournissez l’URL d’une page externe.

   * Pour configurer un message de remerciement ou personnalisé, sélectionnez l’option **[!UICONTROL Afficher le message]** et écrivez un message dans la zone **[!UICONTROL Contenu du message]** pour l’option Lors de l’envoi. Il s’agit d’une zone de texte enrichi. Vous pouvez utiliser l’option Plein écran pour afficher tous les éléments de texte enrichi disponibles.

## Configurer un schéma ou un modèle de données de formulaire (FDM) pour un formulaire adaptatif{#configure-schema-or-data-model-for-form}

Vous pouvez utiliser le modèle de données de formulaire (FDM) pour connecter un formulaire à une Source de données afin d’envoyer et de recevoir des données en fonction des actions de l’utilisateur. Vous pouvez également connecter un formulaire à un schéma JSON pour recevoir les données envoyées dans un format prédéfini. Selon les besoins, connectez votre formulaire à un schéma JSON ou à un modèle de données de formulaire (FDM) :

* [Créer un schéma JSON et le charger dans votre environnement](/help/forms/adaptive-form-json-schema-form-model.md)
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md)

### Configurer un schéma JSON ou un modèle de données de formulaire (FDM) pour votre formulaire

Pour configurer un schéma JSON ou un modèle de données de formulaire (FDM) pour votre formulaire :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Modèle de données]**.

   ![Cliquez sur l’icône Clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer un schéma JSON ou un modèle de données de formulaire (FDM)](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Sélectionnez et configurez un schéma JSON ou un modèle de données de formulaire (FDM) en fonction de vos besoins :

   * Lorsque vous sélectionnez l’option **[!UICONTROL Modèle de formulaire]**, utilisez l’option **[!UICONTROL Sélectionner le modèle de données de formulaire]** pour sélectionner un modèle de données de formulaire (FDM) préconfiguré.
   * Lorsque vous sélectionnez l’option **[!UICONTROL Schéma]**, utilisez l’option **[!UICONTROL Schéma]** pour sélectionner un schéma JSON pour votre formulaire.

1. Cliquez sur **[!UICONTROL Terminé]**.

## Configurer un service de préremplissage  {#configure-prefill-service-for-form}

Vous pouvez utiliser le service de préremplissage pour remplir automatiquement les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ou une utilisatrice ouvre un formulaire, les valeurs de ces champs sont préremplies. Vous pouvez effectuer les actions suivantes :

* [Créer un service de préremplissage personnalisé](/help/forms/prepopulate-adaptive-form-fields.md)
* [Utiliser le service de préremplissage de modèle de données de formulaire](#fdm-prefill-service)

### Utiliser le service de préremplissage de modèle de données de formulaire pour préremplir les champs d’un formulaire adaptatif {#fdm-prefill-service}

Vous pouvez utiliser le service de préremplissage de modèle de données de formulaire pour préremplir les champs d’un formulaire adaptatif à l’aide d’un modèle de données de formulaire ou d’un service de préremplissage personnalisé. Le service de préremplissage de modèle de données de formulaire utilise la méthode [Obtenir le service du modèle de données de formulaire configuré](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) pour récupérer des données. Pour utiliser le service de préremplissage de modèle de données de formulaire pour un formulaire adaptatif :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** du formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’icône de propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
   ![Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer une page de redirection ou un message de remerciement.](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. Sélectionnez un modèle de données de formulaire (FDM). Ouvrez l’onglet **[!UICONTROL De base]**. Dans le service de préremplissage, sélectionnez **[!UICONTROL Service de préremplissage de modèle de données de formulaire]**.
1. Cliquez sur **[!UICONTROL Terminé]**. Votre formulaire adaptatif est maintenant configuré pour utiliser le préremplissage du modèle de données de formulaire. Vous pouvez désormais utiliser l’[éditeur de règles](rule-editor.md) pour créer des règles afin de préremplir les champs du formulaire.

## Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif {#edit-form-model}

1. Sélectionnez le formulaire adaptatif et sélectionnez ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Ouvrir les propriétés]**. La page Propriétés du formulaire s’ouvre.

1. Accédez à l’onglet **[!UICONTROL Modèle de formulaire]** et choisissez un modèle de formulaire. Si le formulaire adaptatif ne dispose pas de modèle de formulaire, vous avez la possibilité de choisir un schéma JSON ou un modèle de données de formulaire (FDM). D’autre part, si le formulaire adaptatif est déjà basé sur un modèle de formulaire, vous avez la possibilité de passer à un autre modèle de formulaire du même type. Par exemple, si le formulaire utilise un schéma JSON, vous pouvez facilement passer à un autre schéma JSON. De même, si le formulaire utilise un modèle de données de formulaire (FDM), vous pouvez passer à un autre modèle de données de formulaire (FDM).

1. Sélectionnez **[!UICONTROL Enregistrer]** pour enregistrer les propriétés.


## Comment renommer un formulaire adaptatif AEM ? {#rename-an-AEM-Adaptive-Form}

Pour renommer un formulaire adaptatif, procédez comme suit :

1. Sélectionnez un formulaire adaptatif dans l’interface d’utilisation d’AEM Forms.
1. Cliquez sur le bouton **Propriétés** situé sur le rail supérieur.
1. Modifiez le nom du formulaire dans l’onglet **Titre**, comme illustré ci-dessous.
1. Cliquez sur **Enregistrer et fermer**.

![Renommer un formulaire adaptatif AEM](/help/forms/assets/change-af-name.png)



