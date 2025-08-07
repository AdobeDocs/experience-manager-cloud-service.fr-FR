---
title: Comment créer un formulaire adaptatif basé sur les composants principaux à l’aide de modèles de formulaire XFA ?
description: Découvrez comment créer un formulaire adaptatif à l’aide  [!DNL Experience Manager Forms]  modèles de formulaire XFA ou de fichiers XDP.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: f3c9b798-8b20-4674-9b96-a3a0b143d947
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 20%

---

# Créer un formulaire adaptatif (composants principaux) basé sur des modèles de formulaire XFA

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

AEM as a Cloud Service permet aux utilisateurs de créer des Forms adaptatifs basés sur des composants principaux à l’aide de modèles de formulaire XFA (XML Forms Architecture) ou de fichiers `*.XDP` (XML Data Package). Cette fonctionnalité permet aux utilisateurs de gagner du temps en migrant des champs du modèle de formulaire XFA ou des fichiers XDP directement vers le Forms adaptatif.

Vous pouvez réutiliser votre modèle de formulaire XFA ou vos fichiers XDP à partir de modèles de formulaire pour créer un Forms adaptatif basé sur les composants principaux. Pour réutiliser, chargez et associez un modèle de formulaire XFA ou des fichiers XDP à un formulaire adaptatif. Les éléments du modèle de formulaire XFA ou des fichiers XDP peuvent être utilisés dans l’outil de recherche de contenu lors de la création de formulaires adaptatifs. À partir de l’outil de recherche de contenu, vous pouvez faire glisser et déposer les éléments du modèle de formulaire dans le formulaire.

## Avantages de la création de formulaires basés sur des modèles de formulaire XFA ou des fichiers XDP

Voici quelques-uns des avantages de la création de formulaires basés sur des modèles de formulaire XFA ou des fichiers XDP :

* **Gains de temps** : vous pouvez réutiliser rapidement des modèles de formulaire XFA existants (fichiers XDP) sans avoir à recréer la structure du formulaire, ce qui vous permet de gagner du temps et vous évite des tâches pendant le processus de création.
* **Migration sans effort** : si vous utilisez déjà des modèles de formulaire XFA, cette option permet d’effectuer facilement la migration vers le Forms adaptatif, ce qui vous permet de tirer parti des avantages des composants principaux AEM modernes sans perdre les données de formulaire et la logique existantes.
* **Expérience utilisateur améliorée** : les Forms adaptatives sont plus réactives et personnalisables que les formulaires XFA. En passant à un Forms adaptatif, vous pouvez améliorer la convivialité de l’expérience sur différents appareils et tailles d’écran.
* **Intégration améliorée** : les Forms adaptatives s’intègrent mieux à d’autres fonctionnalités, telles que les workflows, la liaison de données et les envois de formulaires, ce qui permet des workflows plus fluides et une meilleure gestion globale des formulaires.

## Conditions préalables

Vous avez besoin des éléments suivants pour créer un formulaire adaptatif basé sur les composants principaux à l’aide de modèles de formulaire XFA ou de fichiers XDP :

* [Activation des composants principaux des formulaires adaptatifs pour votre environnement](enable-adaptive-forms-core-components.md).
* Il est recommandé de connaître les domaines suivants :
   * Création d’un formulaire adaptatif
   * XFA (XML Forms Architecture)

## Comment créer un formulaire adaptatif à l’aide d’un modèle de formulaire XFA ou de fichiers XDP ?

Pour créer un formulaire adaptatif à l’aide de modèles de formulaire XFA ou XDP, procédez comme suit :

1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms].
1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.

   ![Forms et documents](/help/forms/assets/create-fdm.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**.

   ![Créer un formulaire adaptatif](/help/forms/assets/create-af.png)

   L’assistant de création de formulaire s’ouvre.
1. Dans l’onglet **Source**, sélectionnez un modèle basé sur les composants principaux.

   ![Sélection d’un modèle](/help/forms/assets/select-template.png)

   Lorsque vous sélectionnez un modèle, un thème et l’action d’envoi spécifiée dans le modèle sont sélectionnés automatiquement. Le bouton **[!UICONTROL Créer]** est activé.

   ![Sélectionner le thème](/help/forms/assets/select-form-theme.png)

1. Sélectionnez **[!UICONTROL Créer]**. Une boîte de dialogue pour spécifier le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif s’affiche.
1. Indiquez son titre, son nom et son emplacement.
1. Sélectionnez **[!UICONTROL Créer]**.
   ![Indiquez le nom et le titre](/help/forms/assets/create-form.png)

   Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.
1. Sélectionnez ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Ouvrir les propriétés]**.

   ![Ouvrir les propriétés](/help/forms/assets/form-properties.png)

   La page Propriétés du formulaire s’ouvre.
1. Accédez à l’onglet **[!UICONTROL Modèle de formulaire]** et choisissez **Modèles de formulaire**.
1. Sélectionnez le fichier .xdp dans la liste déroulante.

   ![Sélectionner un fichier XDP](/help/forms/assets/select-xdp-file.png)

   Une boîte de dialogue d’avertissement s’affiche à l’écran. Cliquez sur **OK** pour continuer.

   ![Boîte de dialogue d’avertissement](/help/forms/assets/fdm-warning.png)

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer les propriétés.

   >[!NOTE]
   >
   > Après avoir sélectionné **Modèles de formulaire** dans l’onglet **Modèle** de formulaire, il ne peut pas être modifié.


Un formulaire adaptatif est créé et s’ouvre dans l’éditeur de formulaires adaptatifs. L’éditeur affiche le contenu disponible dans le modèle.  En fonction du type de formulaire adaptatif, les éléments de formulaire présents dans le modèle de formulaire XFA associé sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

>[!NOTE]
>
> Vous pouvez désactiver les scripts pour les champs de formulaire XDP à l’aide de la barre d’outils du panneau du champ ajouté. Créez des logiques pour les champs ajoutés à l’aide de l’[éditeur visuel de règles](/help/forms/rule-editor-core-components.md).

