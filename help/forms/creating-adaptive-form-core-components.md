---
title: Comment créer un formulaire adaptatif ?
description: Découvrez comment créer un formulaire adaptatif à l’aide de [!DNL Experience Manager Forms]. Les formulaires adaptatifs sont des formulaires HTML5 réactifs qui rationalisent la collecte et le traitement des informations. Découvrez comment créer un formulaire adaptatif basé sur un modèle de données de formulaire et un schéma XML ou JSON.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: a4fd268cb143c1356de3db9d55b16ccb58b67d4b
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 94%

---


# Créer un formulaire adaptatif (composants principaux) {#creating-an-adaptive-form-core-components}

Les formulaires adaptatifs vous permettent de créer des formulaires attrayants, réactifs, dynamiques et adaptatifs. AEM Forms fournit un assistant convivial pour les utilisateurs et utilisatrices professionnels, qui permet de créer rapidement des formulaires adaptatifs. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif.

Avant de commencer, découvrez les types de composants de formulaires disponibles :

* [Composants principaux de formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) : il s’agit de composants de capture de données normalisés. Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique. Un développeur ou une développeuse peut facilement personnaliser et mettre en forme ces composants. Adobe recommande d’utiliser ces composants modernes et extensibles pour développer des formulaires adaptatifs.

* [Composants de base des formulaires adaptatifs](creating-adaptive-form.md) : il s’agit de composants de capture de données classiques (anciens). Vous pouvez continuer à les utiliser pour modifier votre formulaire adaptatif existant basé sur les composants de base. Si vous créez des formulaires, Adobe recommande d’utiliser les [composants principaux de formulaires adaptatifs](creating-adaptive-form-core-components.md).

![Assistant de création d’un formulaire adaptatif](/help/release-notes/assets/wizard.png)


## Conditions préalables

Pour créer un formulaire adaptatif, vous devez disposer des éléments suivants :

* **Activer des composants principaux de formulaires adaptatifs pour votre environnement** : lorsque vous créez un programme, les composants principaux des formulaires adaptatifs sont déjà activés pour votre environnement. Si vous disposez d’un environnement Forms as a Cloud Service basé sur Archetype 39 ou une version antérieure, vous devez [activer les composants principaux des formulaires adaptatifs pour votre environnement](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Lors de l’activation des composants principaux pour votre environnement, le modèle **Formulaires adaptatifs (composant principal)** et le thème de la zone de travail sont ajoutés à votre environnement. Si votre SDK AEM version antérieure à la version 2023.02.0, [assurez-vous que vous avez `prerelease` indicateur activé dans votre environnement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) car les composants principaux de Forms adaptatif faisaient partie de la version préliminaire avant la version 2023.02.0.

* **Un modèle de formulaire adaptatif** : un modèle fournit une structure de base et définit l’aspect, c’est-à-dire la mise en page et les styles, d’un formulaire adaptatif. Il comporte des composants pré-formatés contenant certaines propriétés et une certaine structure de contenu. Il fournit également les options permettant de définir un thème et une action d’envoi. Le thème définit l’aspect et l’action d’envoi définit l’action à entreprendre lors de l’envoi d’un formulaire adaptatif. Par exemple, l’envoi des données collectées à une source de données. Le service cloud fournit un modèle prêt à l’emploi, sans nom :

   * Le modèle `blank` est inclus dans chaque nouveau programme AEM Forms as a Cloud Service.
   * Vous pouvez installer le package de référence, via le gestionnaire de modules, pour ajouter le modèle `blank` à votre programme AEM Forms as a Cloud Service.
   * Vous pouvez également [créer un modèle de formulaire adaptatif (composants principaux)](template-editor.md) à partir de zéro.

* **Un thème de formulaire adaptatif** : un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants.  Le modèle `Canvas` est inclus dans chaque nouveau programme AEM Forms as a Cloud Service.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Autorisations** : ajoutez vos utilisateurs et utilisatrices au groupe [!DNL forms-users]. Les membres du groupe [!DNL forms-users] ont les autorisations de créer un formulaire adaptatif. Pour obtenir la liste détaillée des groupes d’utilisateurs et d’utilisatrices spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).


## Créer un formulaire adaptatif (composants principaux) {#create-an-adaptive-form-core-components}

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms] Il peut s’agir d’une instance cloud ou d’une instance de développement local.

1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, appuyez sur **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.

1. Appuyez sur **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant. Dans l’onglet Source, sélectionnez un modèle :

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

   * **Modèle de données de formulaire** : un [modèle de données de formulaire](data-integration.md) vous permet d’intégrer des entités et des services provenant de sources de données disparates à un formulaire adaptatif. Choisissez le modèle de données de formulaire si le formulaire adaptatif que vous créez implique l’extraction et l’écriture de données depuis et vers plusieurs sources de données.

   * **Schéma JSON** : [schéma JSON](adaptive-form-json-schema-form-model.md), notre formulaire adaptatif basé sur les composants principaux, permet une intégration transparente au système back-end de votre entreprise en vous permettant d’associer un schéma JSON, qui représente la structure des données générées ou consommées. Cette association permet aux créateurs et créatrices d’ajouter dynamiquement du contenu au formulaire adaptatif à l’aide des éléments du schéma. Les éléments du schéma sont facilement accessibles dans l’onglet Objets de modèle de données de l’explorateur de contenu au cours du processus de création. Tous les champs sont automatiquement ajoutés à tout nouveau formulaire adaptatif.

   Par défaut, tous les champs du schéma JSON associé sont automatiquement sélectionnés et convertis en composants de formulaire adaptatif correspondants, ce qui simplifie le processus de création. L’assistant vous permet, en outre, de sélectionner les champs à inclure dans le formulaire adaptatif au moyen de cases à cocher.

1. Dans l’onglet **[!UICONTROL Envoi]**, sélectionnez une action d’envoi :

   * Lorsque vous sélectionnez un modèle, l’action d’envoi spécifiée dans le modèle est sélectionnée automatiquement. Vous pouvez sélectionner une autre action d’envoi dans l’onglet Envoi. L’onglet **[!UICONTROL Envoi]** affiche toutes les actions d’envoi disponibles.

   * Lorsque le modèle sélectionné ne spécifie aucune action d’envoi, vous pouvez utiliser l’onglet **[!UICONTROL Envoi]** pour sélectionner une action d’envoi

1. (Facultatif) Dans l’onglet **[!UICONTROL Diffusion]**, vous pouvez spécifier une date de publication ou de d’annulation de publication pour un formulaire adaptatif.

1. Appuyez sur **[!UICONTROL Créer]**. Une boîte de dialogue pour spécifier le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif s’affiche :

   * **[!UICONTROL Titre]** Spécifie le nom d’affichage du formulaire. Le titre vous permet d’identifier le formulaire dans l’interface utilisateur [!DNL Experience Manager Forms] d’AEM Forms.
   * **[!UICONTROL Nom :]** indique le nom du formulaire. Un noeud portant le nom spécifié est créé dans le référentiel. Lorsque vous commencez à saisir un titre, la valeur du champ de nom est automatiquement générée. Vous pouvez modifier la valeur suggérée. Le champ Nom ne peut contenir que des caractères alphanumériques, des tirets et des traits de soulignement. Toutes les entrées non valides sont remplacées par un trait d’union.
   * **[!UICONTROL Chemin d’accès :]** indique l’emplacement d’enregistrement du formulaire adaptatif. Vous pouvez enregistrer le formulaire adaptatif directement sur `/content/dam/formsanddocuments` ou créer un dossier tel que `/content/dam/formsanddocuments/adaptiveforms` pour enregistrer un formulaire adaptatif. Assurez-vous de créer le dossier avant de l’utiliser dans le chemin d’accès. Le champ **[!UICONTROL Chemin d’accès]** ne crée pas de dossier automatiquement.

1. Appuyez sur **[!UICONTROL Créer]**. Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.  En fonction du type de formulaire adaptatif, les éléments de formulaire présents dans le <!--XFA form template, XML schema or --> schéma JSON ou le modèle de données de formulaire associé sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL explorateur de contenu]** dans la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

Désormais, vous pouvez faire glisser les composants principaux des formulaires adaptatifs vers le conteneur de formulaires adaptatifs pour concevoir et créer le formulaire.

## Composants principaux des formulaires adaptatifs disponibles

Les composants principaux des formulaires adaptatifs sont des composants de capture de données normalisés. Ces composants fournissent des fonctionnalités de personnalisation, réduisent le temps de développement et amenuisent les coûts de maintenance pour vos expériences d’inscription numérique. La [documentation sur les composants principaux des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) comporte une liste détaillée des composants disponibles, ainsi que des informations complètes sur les fonctionnalités de chaque composant. Vous pouvez également consulter [https://aemcomponents.dev/](https://aemcomponents.dev/) pour afficher les composants principaux disponibles en action.

## Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif {#edit-form-model}

1. Sélectionnez le formulaire adaptatif et appuyez sur ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Ouvrir les propriétés]**. La page Propriétés du formulaire s’ouvre.

1. Accédez à l’onglet **[!UICONTROL Modèle de formulaire]** et choisissez un modèle de formulaire. Si le formulaire adaptatif est dépourvu de modèle de formulaire, vous avez la possibilité de choisir un schéma JSON ou un modèle de données de formulaire. D’autre part, si le formulaire adaptatif est déjà basé sur un modèle de formulaire, vous avez la possibilité de passer à un autre modèle de formulaire du même type. Par exemple, si le formulaire utilise un schéma JSON, vous pouvez facilement passer à un autre schéma JSON. De même, si le formulaire utilise un modèle de données de formulaire, vous pouvez passer à un autre modèle de données de formulaire.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les propriétés.
