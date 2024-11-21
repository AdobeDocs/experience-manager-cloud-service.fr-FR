---
title: Comment créer un formulaire adaptatif basé sur des composants principaux à l’aide de modèles de formulaire XFA ?
description: Découvrez comment créer un formulaire adaptatif à l’aide de  [!DNL Experience Manager Forms]  avec des modèles de formulaire XFA ou des fichiers XDP.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 18%

---


# Créer un formulaire adaptatif (composants principaux) basé sur des modèles de formulaire XFA

<span class="preview"> La fonctionnalité est disponible dans le cadre du programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

AEM as a Cloud Service offre aux utilisateurs la possibilité de créer une Forms adaptative basée sur des composants principaux à l’aide de modèles de formulaire XFA (XML Forms Architecture) ou de fichiers `*.XDP` (package de données XML). Cette fonctionnalité permet aux utilisateurs de gagner du temps en migrant les champs du modèle de formulaire XFA ou des fichiers XDP directement vers le Forms adaptatif.

Vous pouvez réutiliser votre modèle de formulaire XFA ou vos fichiers XDP pour créer un Forms adaptatif basé sur les composants principaux. Pour le réutiliser, téléchargez et associez un modèle de formulaire XFA ou des fichiers XDP à un formulaire adaptatif. Les éléments du modèle de formulaire XFA ou des fichiers XDP peuvent être utilisés dans l’outil de recherche de contenu lors de la création de formulaires adaptatifs. Dans l’outil de recherche de contenu, vous pouvez faire glisser les éléments de modèle de formulaire sur le formulaire.

## Avantages de la création de formulaires basés sur des modèles de formulaire XFA ou des fichiers XDP

La création de formulaires basés sur des modèles de formulaire XFA ou des fichiers XDP offre peu d’avantages :

* **Économie de temps** : vous pouvez rapidement réutiliser des modèles de formulaire XFA (fichiers XDP) existants sans avoir à recréer la structure du formulaire, ce qui vous permet de gagner du temps et de gagner du temps au cours du processus de création.
* **Migration sans effort** : si vous utilisez déjà des modèles de formulaire XFA, cette option permet de migrer facilement vers Forms adaptatif, ce qui vous permet de tirer parti des avantages des composants principaux d’AEM modernes sans perdre les données de formulaire et la logique existantes.
* **Expérience utilisateur améliorée** : les Forms adaptatives sont plus réactives et personnalisables que les formulaires XFA. En passant à Adaptive Forms, vous pouvez garantir une expérience plus conviviale sur différents appareils et tailles d’écran.
* **Intégration améliorée** : les Forms adaptatives s’intègrent mieux à d’autres fonctionnalités, telles que les workflows, la liaison de données et les envois de formulaire, ce qui permet de fluidifier les workflows et d’améliorer la gestion globale des formulaires.

## Prérequis

Vous avez besoin des éléments suivants pour créer un formulaire adaptatif basé sur des composants principaux à l’aide de modèles de formulaire XFA ou de fichiers XDP :

* [Activation des composants principaux des formulaires adaptatifs pour votre environnement](enable-adaptive-forms-core-components.md).
* Il est recommandé de se familiariser avec les domaines suivants :
   * Création d’un formulaire adaptatif
   * XFA (XML Forms Architecture)

## Comment créer un formulaire adaptatif à l’aide de modèles de formulaire XFA ou de fichiers XDP ?

Effectuez les étapes suivantes pour créer un formulaire adaptatif à l’aide de modèles de formulaire XFA ou XDP :

1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms].
1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.

   ![Forms et documents](/help/forms/assets/create-fdm.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**.

   ![Créer un formulaire adaptatif](/help/forms/assets/create-af.png)

   L’assistant de création de formulaire s’ouvre.
1. Dans l’onglet **Source** , sélectionnez un modèle basé sur les composants principaux.

   ![Sélection d’un modèle](/help/forms/assets/select-template.png)

   Lorsque vous sélectionnez un modèle, un thème et une action d’envoi spécifiés dans le modèle sont automatiquement sélectionnés et le bouton **[!UICONTROL Créer]** est activé.

   ![Sélectionner un thème](/help/forms/assets/select-form-theme.png)

1. Sélectionnez **[!UICONTROL Créer]**. Une boîte de dialogue pour spécifier le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif s’affiche.
1. Indiquez son titre, son nom et son emplacement.
1. Sélectionnez **[!UICONTROL Créer]**.
   ![Fournir le nom et le titre](/help/forms/assets/create-form.png)

   Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.
1. Sélectionnez ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Ouvrir les propriétés]**.

   ![Ouvrir les propriétés](/help/forms/assets/form-properties.png)

   La page Propriétés du formulaire s’ouvre.
1. Accédez à l’onglet **[!UICONTROL Modèle de formulaire]** et sélectionnez **Modèles de formulaire**.
1. Sélectionnez le fichier .xdp dans la liste déroulante.

   ![Sélectionner un fichier XDP](/help/forms/assets/select-xdp-file.png)

   Une boîte de dialogue d’avertissement s’affiche à l’écran. Cliquez sur **OK** pour continuer.

   ![Boîte de dialogue d’avertissement](/help/forms/assets/fdm-warning.png)

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer les propriétés.

   >[!NOTE]
   >
   > Après avoir sélectionné **Modèles de formulaire** dans l’onglet **Modèle** de formulaire, il ne peut pas être modifié.


Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.  En fonction du type de formulaire adaptatif, les éléments de formulaire présents dans le modèle de formulaire XFA associé sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL explorateur de contenu]** de la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

>[!NOTE]
>
> Vous pouvez désactiver les scripts pour les champs de formulaire XDP à l’aide de la barre d’outils du panneau du champ ajouté. Créez des logiques pour les champs ajoutés à l’aide de l’ [ éditeur de règles visuel](/help/forms/rule-editor-core-components.md).

## Voir également

{{see-also}}
* [Ajouter un comportement dynamique aux formulaires à l’aide de l’éditeur de règles](/help/forms/rule-editor-core-components.md)