---
title: Comment pouvons-nous traduire un formulaire adaptatif basé sur les composants principaux ?
description: Découvrez comment créer un modèle de données de formulaire dans AEM Forms, tester le modèle avec des exemples de données et de services et configurer diverses options pour un modèle.
feature: Adaptive Forms
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 17%

---

# Utilisation de la traduction automatique ou humaine pour traduire un formulaire adaptatif basé sur des composants principaux {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Les formulaires localisés permettent de servir un public plus large dans plusieurs zones géographiques. Le processus de traduction Adobe Experience Manager vous aide à localiser des formulaires adaptatifs et leurs documents d’enregistrement. Vous pouvez faire appel à la **traduction automatique** ou à des **traducteurs humains** pour localiser un formulaire adaptatif.

## Traduire un formulaire adaptatif et un document d’enregistrement à l’aide de la traduction automatique {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Le service de traduction automatique traduit immédiatement votre contenu dans le formulaire adaptatif et [Document d’enregistrement](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service est préconfiguré pour utiliser une version d’évaluation de Microsoft Translator pour la traduction automatique. Procédez comme suit pour activer la traduction automatique pour les formulaires adaptatifs et le document d’enregistrement :

1. Dans l’interface utilisateur AEM Forms, sélectionnez un formulaire, puis appuyez sur l’option **[!UICONTROL Ajouter un dictionnaire]**.
1. Dans l’écran Ajouter un dictionnaire au projet de traduction , pour le **[!UICONTROL Projet]** option

   * Pour créer un projet de traduction, sélectionnez la **[!UICONTROL Création d’un projet de traduction]** et dans la variable **Titre du projet** , indiquez le titre. Par exemple, `Government Reference Site - German locale.`.
   * Pour ajouter un nouveau dictionnaire à un projet de traduction existant, sélectionnez le **[!UICONTROL Ajouter à un projet de traduction existant]** et sélectionnez une **[!UICONTROL Projet de traduction existant]**.
1. Dans le **Langues cibles** , spécifiez un paramètre régional (par exemple, `German(de)`). Vous pouvez spécifier plusieurs paramètres régionaux. Le formulaire est traduit dans tous les paramètres régionaux spécifiés dans la variable **Langues cibles** champ . Cliquez sur **Terminé**.
1. Dans la boîte de dialogue Dictionnaire ajouté, cliquez sur **Ouvrir des projets**.
1. Dans l’écran Projets , cliquez sur le projet nouvellement créé. Par exemple, cliquez sur le bouton **Site de référence du gouvernement - langue allemande** mosaïque.
1. Dans le volet **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Démarrer**. L’état de la mosaïque passe à Brouillon. Une fois la traduction terminée, l’état passe à **Approuvé**. Actualisez la page après quelques minutes et vérifiez l’état.

   ![Commencer la traduction](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Une fois que l’état est défini sur **Approuvé** sur le **Tâche de traduction** , cliquez sur la mosaïque ![aem62forms_downflèche](assets/aem62forms_downarrow.png) puis cliquez sur **Terminer**.

1. Pour prévisualiser le formulaire localisé, sélectionnez le formulaire localisé dans l’interface utilisateur d’AEM Forms. Cliquez sur **[!UICONTROL Aperçu]** >**[!UICONTROL Aperçu comme HTML]**. rouvrez le formulaire après avoir ajouté la variable `afAcceptLang=<locale code>` à l’URL du formulaire. Par exemple, ajoutez `afAcceptLang=de`pour ouvrir la version allemande du formulaire.


   >[!NOTE]
   >
   >* Avant d’ouvrir la version localisée du formulaire dans la fenêtre du navigateur, assurez-vous que les paramètres régionaux du navigateur correspondent à ceux du formulaire. Par exemple, si le formulaire est traduit en allemand(de), définissez les paramètres régionaux du navigateur sur Allemand(de).
   >* Les composants de formulaire adaptatif ne prennent pas en charge les langues de droite à gauche (RTL). comme l’hébreu.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, tap Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## Localiser un formulaire adaptatif et son document d’enregistrement à l’aide de la traduction humaine {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

En traduction humaine, le contenu est envoyé à un prestataire de traduction et traduit par des traducteurs professionnels. Une fois la traduction terminée, le contenu traduit est renvoyé et importé dans AEM. Lorsque votre fournisseur de traduction est intégré à AEM, le contenu est automatiquement transféré entre AEM et le fournisseur de traduction.

Pour la traduction, un dictionnaire contenant des fichiers au format XLIFF est partagé avec les traducteurs professionnels. Le dictionnaire contient un fichier XLIFF distinct pour chaque paramètre régional. Chaque fichier XLIFF contient du texte qui s’affiche pour les utilisateurs finaux et des espaces réservés pour le texte localisé correspondant.

Effectuez les étapes suivantes pour localiser un formulaire et son document d’enregistrement à l’aide de traducteurs humains :

1. Dans l’interface utilisateur AEM Forms, sélectionnez un formulaire, puis appuyez sur l’option **[!UICONTROL Ajouter un dictionnaire]**.
1. Dans l’écran Ajouter un dictionnaire au projet de traduction , pour le **[!UICONTROL Projet]** option

   * Pour créer un projet de traduction, sélectionnez la **[!UICONTROL Création d’un projet de traduction]** et dans la variable **Titre du projet** , indiquez le titre. Par exemple, `Government Reference Site - German locale.`.
   * Pour ajouter un nouveau dictionnaire à un projet de traduction existant, sélectionnez le **[!UICONTROL Ajouter à un projet de traduction existant]** et sélectionnez une **[!UICONTROL Projet de traduction existant]**.
1. Dans le **Langues cibles** , spécifiez un paramètre régional (par exemple, `German(de)`). Vous pouvez spécifier plusieurs paramètres régionaux. Le formulaire est traduit dans tous les paramètres régionaux spécifiés dans la variable **Langues cibles** champ . Cliquez sur **Terminé**.
1. Dans la boîte de dialogue Dictionnaire ajouté, cliquez sur **Ouvrir des projets**.
1. Dans l’écran Projets , cliquez sur le projet nouvellement créé. Par exemple, cliquez sur le bouton **Site de référence du gouvernement - langue allemande** mosaïque.
1. Au bas de la **Résumé** , cliquez sur la mosaïque **ellipses**. L’écran Propriétés du projet de traduction s’affiche.
1. Ouvrez le **[!UICONTROL Avancé]** dans la partie supérieure de la **Propriétés du projet de traduction** écran. Pour le **[!UICONTROL Champ de traduction]**, sélectionnez **[!UICONTROL Traduction humaine]**. Cliquez sur **Enregistrer et fermer** en haut de l’écran.
1. Sur le **Tâche de traduction** , cliquez sur la mosaïque ![aem62forms_downflèche](assets/aem62forms_downarrow.png) puis cliquez sur **Exporter**. Dans la boîte de dialogue Exporter, cliquez sur l’option Télécharger le fichier exporté . Il télécharge un fichier .zip.
   ![Exporter le fichier de traduction](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Extrayez le fichier .zip téléchargé. Le dossier extrait comporte deux fichiers :
   * translation_export_summary.xml
   * [form-fields-file].xml.
1. Ouvrez le [form-fields-file].xml pour modification. Ajoutez les chaînes et les messages localisés pour les champs de formulaire. Enregistrez et fermez le fichier.
1. Zip des fichiers dans translation_export_summary.xml et [form-fields-file].xml.
1. Sur le **Tâche de traduction** , cliquez sur la mosaïque ![aem62forms_downflèche](assets/aem62forms_downarrow.png) puis cliquez sur **Importer**. Sélectionnez l’archive contenant [form-fields-file].xml. avec des chaînes et des messages localisés pour les champs de formulaire.

   ![Importer un fichier de traduction](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Pour prévisualiser le formulaire localisé, sélectionnez le formulaire localisé dans l’interface utilisateur d’AEM Forms. Cliquez sur **[!UICONTROL Aperçu]** >**[!UICONTROL Aperçu comme HTML]**. rouvrez le formulaire après avoir ajouté la variable `afAcceptLang=<locale code>` à l’URL du formulaire. Par exemple, ajoutez `afAcceptLang=de`pour ouvrir la version allemande du formulaire.
