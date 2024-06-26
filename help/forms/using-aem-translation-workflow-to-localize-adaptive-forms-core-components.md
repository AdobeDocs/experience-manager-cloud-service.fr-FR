---
title: Comment pouvons-nous traduire un formulaire adaptatif basé sur les composants principaux ?
description: Découvrez comment créer un modèle de données de formulaire (FDM) dans AEM Forms, tester le modèle avec des exemples de données et de services et configurer diverses options pour un modèle.
feature: Adaptive Forms, Core Components
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 93%

---

# Utiliser la traduction automatique ou humaine pour traduire un formulaire adaptatif basé sur des composants principaux {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Les formulaires localisés permettent de servir un public plus large dans plusieurs zones géographiques. Le processus de traduction Adobe Experience Manager vous aide à localiser des formulaires adaptatifs et leurs documents d’enregistrement. Vous pouvez faire appel à la **traduction automatique** ou à des **traducteurs humains** pour localiser un formulaire adaptatif.

## Traduire un formulaire adaptatif et un document d’enregistrement à l’aide de la traduction automatique {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Le service de traduction automatique traduit directement le contenu de vos formulaires adaptatifs et [documents d’enregistrement](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service est préconfiguré pour utiliser une version d’évaluation de Microsoft Translator pour la traduction automatique. Procédez comme suit pour activer la traduction automatique pour les formulaires adaptatifs et le document d’enregistrement :

1. Dans l’interface utilisateur AEM Forms, sélectionnez un formulaire, puis l’option **[!UICONTROL Ajouter un dictionnaire]**.
1. Dans l’écran Ajouter un dictionnaire au projet de traduction, pour l’option **[!UICONTROL Projet]** :

   * Pour créer un projet de traduction, sélectionnez l’option **[!UICONTROL Créer un projet de traduction]**. Dans le champ **Titre du projet**, indiquez le titre. Par exemple, `Government Reference Site - German locale.`.
   * Pour ajouter un nouveau dictionnaire à un projet de traduction existant, sélectionnez l’option **[!UICONTROL Ajouter à un projet de traduction existant]** et sélectionnez un **[!UICONTROL Projet de traduction existant]**.
1. Dans le champ **Langues cibles**, spécifiez un paramètre régional (par exemple `German(de)`). Vous pouvez spécifier plusieurs paramètres régionaux. Le formulaire est traduit dans tous les paramètres régionaux spécifiés dans le champ **Langues cibles**. Cliquez sur **Terminé**.
1. Dans la boîte de dialogue Dictionnaire ajouté, cliquez sur **Ouvrir des projets**.
1. Dans l’écran Projets , cliquez sur le projet créé. Par exemple, cliquez sur la mosaïque **Site de référence du gouvernement - langue allemande**.
1. Dans le volet **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Démarrer**. Le statut de la mosaïque passe à Brouillon. Une fois la traduction terminée, le statut passe à **Approuvé**. Actualisez la page après quelques minutes et vérifiez le statut.

   ![Début de la traduction](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Une fois que le statut est défini sur **Approuvé** sur la mosaïque **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Terminer**.

1. Pour prévisualiser le formulaire localisé, sélectionnez le formulaire localisé dans l’UI d’AEM Forms. Cliquez sur **[!UICONTROL Aperçu]** > **[!UICONTROL Aperçu au format HTML]**. Rouvrez le formulaire après avoir ajouté `afAcceptLang=<locale code>` à l’URL du formulaire. Par exemple, ajoutez `afAcceptLang=de` pour ouvrir la version allemande du formulaire.


   >[!NOTE]
   >
   >* Avant d’ouvrir la version localisée du formulaire dans la fenêtre du navigateur, assurez-vous que les paramètres régionaux du navigateur correspondent à ceux du formulaire. Par exemple, si le formulaire est traduit en Allemand(de), définissez les paramètres régionaux du navigateur sur Allemand(de).
   >* Les composants de formulaire adaptatif ne prennent pas en charge les langues de droite à gauche (RTL). comme l’hébreu.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, select Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## Localiser un formulaire adaptatif et son document d’enregistrement à l’aide de la traduction humaine {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

Avec la traduction humaine, le contenu est envoyé à un prestataire de traduction et traduit par des traducteurs et des traductrices professionnels. Une fois la traduction terminée, le contenu traduit est renvoyé et importé dans AEM. Lorsque votre fournisseur de traduction est intégré à AEM, le contenu est automatiquement transféré entre AEM et le fournisseur de traduction.

Pour la traduction, un dictionnaire contenant les fichiers au format XLIFF est partagé avec les traducteurs et les traductrices professionnels. Le dictionnaire contient un fichier XLIFF distinct pour chaque langue. Chaque fichier XLIFF contient du texte visible par les personnes utilisatrices finales, ainsi que des espaces réservés pour le texte localisé correspondant.

Effectuez les étapes suivantes pour localiser un formulaire et son document d’enregistrement à l’aide de traducteurs et traductrices humains :

1. Dans l’interface utilisateur AEM Forms, sélectionnez un formulaire, puis l’option **[!UICONTROL Ajouter un dictionnaire]**.
1. Dans l’écran Ajouter un dictionnaire au projet de traduction, pour l’option **[!UICONTROL Projet]** :

   * Pour créer un projet de traduction, sélectionnez l’option **[!UICONTROL Créer un projet de traduction]**. Dans le champ **Titre du projet**, indiquez le titre. Par exemple, `Government Reference Site - German locale.`.
   * Pour ajouter un nouveau dictionnaire à un projet de traduction existant, sélectionnez l’option **[!UICONTROL Ajouter à un projet de traduction existant]** et sélectionnez un **[!UICONTROL Projet de traduction existant]**.
1. Dans le champ **Langues cibles**, spécifiez un paramètre régional (par exemple `German(de)`). Vous pouvez spécifier plusieurs paramètres régionaux. Le formulaire est traduit dans tous les paramètres régionaux spécifiés dans le champ **Langues cibles**. Cliquez sur **Terminé**.
1. Dans la boîte de dialogue Dictionnaire ajouté, cliquez sur **Ouvrir des projets**.
1. Dans l’écran Projets , cliquez sur le projet créé. Par exemple, cliquez sur la mosaïque **Site de référence du gouvernement - langue allemande**.
1. Au bas de la mosaïque **Résumé**, cliquez sur les **points de suspension**. L’écran Propriétés du projet de traduction s’affiche.
1. Ouvrez l’onglet **[!UICONTROL Avancé]** dans la partie supérieure de l’écran **Propriétés du projet de traduction**. Pour le **[!UICONTROL champ Traduction]**, sélectionnez **[!UICONTROL Traduction humaine]**. Cliquez sur **Enregistrer et fermer** en haut de l’écran.
1. Dans la mosaïque **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Exporter**. Dans la boîte de dialogue Exporter, cliquez sur l’option Télécharger le fichier exporté. Un fichier ZIP est téléchargé.
   ![Exporter le fichier de traduction](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Extrayez le fichier ZIP téléchargé. Le dossier extrait comporte deux fichiers :
   * translation_export_summary.xml
   * [form-fields-file].xml.
1. Ouvrez le fichier [form-fields-file].xml pour modification. Ajoutez les chaînes et les messages localisés pour les champs de formulaire. Enregistrez et fermez le fichier.
1. Compressez les fichiers translation_export_summary.xml et [form-fields-file].xml.
1. Dans la mosaïque **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Importer**. Sélectionnez l’archive contenant [form-fields-file].xml avec des chaînes et des messages localisés pour les champs de formulaire.

   ![Importer un fichier de traduction](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Pour prévisualiser le formulaire localisé, sélectionnez le formulaire localisé dans l’UI d’AEM Forms. Cliquez sur **[!UICONTROL Aperçu]** > **[!UICONTROL Aperçu au format HTML]**. Rouvrez le formulaire après avoir ajouté `afAcceptLang=<locale code>` à l’URL du formulaire. Par exemple, ajoutez `afAcceptLang=de` pour ouvrir la version allemande du formulaire.

## Voir également {#see-also}

{{see-also}}