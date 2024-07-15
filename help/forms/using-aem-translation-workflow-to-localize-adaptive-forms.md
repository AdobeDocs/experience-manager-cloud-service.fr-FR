---
title: Comment pouvons-nous utiliser AEM processus de traduction pour localiser le Forms adaptatif et le document d’enregistrement ?
description: Découvrez comment utiliser les processus de traduction AEM pour localiser les formulaires adaptatifs et le document d’enregistrement.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 90%

---


# Localisation d’Adaptive Forms et d’un document d’enregistrement{#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Les formulaires localisés permettent de servir un public plus large dans plusieurs zones géographiques. Le processus de traduction Adobe Experience Manager vous aide à localiser des formulaires adaptatifs et leurs documents d’enregistrement. Vous pouvez faire appel à la **traduction automatique** ou à des **traducteurs humains** pour localiser un formulaire adaptatif.

Cet article décrit la procédure d’utilisation du processus de traduction AEM avec des formulaires adaptatifs et des documents d’enregistrement.

## Localiser un formulaire adaptatif et un document d’enregistrement à l’aide de la traduction automatique {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Le service de traduction automatique traduit directement le contenu de vos formulaires adaptatifs et documents d’enregistrement. [!DNL AEM Forms] est préconfiguré pour utiliser une version d’évaluation de [!DNL Microsoft Translator] pour la traduction automatique. Procédez comme suit pour activer la traduction automatique pour les formulaires adaptatifs et le document d’enregistrement :

1. Dans l’interface utilisateur de [!DNL AEM Forms], sélectionnez un formulaire, puis l’option **Ajouter un dictionnaire** .
1. Dans l’écran **Ajouter un dictionnaire au projet de traduction**, sélectionnez l’option **Créer un nouveau projet de traduction** ou **Ajouter à un projet de traduction existant**.
1. Dans le champ **Titre du projet**, indiquez le titre, par exemple `Government Reference Site - German locale.`
1. Dans le champ **Langues cibles**, spécifiez un paramètre régional (par exemple `German(de)`), puis cliquez sur **Terminé**. Vous pouvez spécifier plusieurs paramètres régionaux. Le formulaire est traduit dans tous les paramètres régionaux spécifiés dans le champ **Langues cibles**.
1. Dans la boîte de dialogue Dictionnaire ajouté, cliquez sur **Ouvrir des projets**. Dans l’écran Projets , ouvrez le projet créé.
1. Cliquez sur les **points de suspension** en bas de la mosaïque **Résumé de traduction**. L’écran Résumé de traduction s’affiche.
1. Cliquez sur l’icône **Modifier** en haut de l’écran **Résumé de traduction**. Ouvrez l’onglet **Traduction** et sélectionnez Traduction automatique sur l’écran **Méthode de traduction**. Sélectionnez le **fournisseur de traduction** approprié et la **configuration de cloud**. Cliquez sur l’icône **Terminé** en haut de l’écran.
1. Dans le volet **Tâche de traduction**, cliquez sur l’icône ![aem62forms_downarrow](assets/aem62forms_downarrow.png), puis sur **Démarrer**. Le statut de la mosaïque passe à Brouillon. Une fois la traduction terminée, le statut passe à **Prêt pour la révision**. Actualisez la page après quelques minutes et vérifiez le statut.
1. Après le changement d’état en **Prêt pour la révision**, dans la vignette **Tâche de traduction**, ouvrez le formulaire dans une fenêtre de navigateur. Une version localisée du formulaire s’affiche.

   >[!NOTE]
   >
   >* Avant d’ouvrir la version localisée du formulaire dans la fenêtre du navigateur, assurez-vous que les paramètres régionaux du navigateur correspondent à ceux du formulaire. Par exemple, si le formulaire est traduit en Allemand(de), définissez les paramètres régionaux du navigateur sur Allemand(de).
   >* Les composants de formulaire adaptatif ne prennent pas en charge les langues de droite à gauche (RTL) comme l’hébreu.

   Avec le formulaire adaptatif, le document d’enregistrement généré automatiquement est également localisé.

   Pour plus d’informations sur les paramètres et la configuration du document d’enregistrement, voir :

[Configuration du modèle de document d’enregistrement](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Paramètres d’un document d’enregistrement](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Personnalisez les informations de marque du document d’enregistrement](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) et assurez-vous que les paramètres régionaux du navigateur correspondent à la langue dans laquelle vous avez localisé le formulaire adaptatif à l’aide de la langue de la machine. Les paramètres régionaux du navigateur permettent de localiser les informations de marque dans le document d’enregistrement.
1. Pour afficher le document d’enregistrement localisé, sélectionnez Générer l’aperçu. Le document d’enregistrement PDF est généré et ouvert dans un nouvel onglet de votre navigateur.

<!-- ## Localizing an Adaptive Form and its Document of Record using Human Translation {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In Human translation the content is sent to a translation provider and translated by professional translators. When complete, the translated content is returned and imported into AEM. When your translation provider is integrated with AEM, content is automatically sent between AEM and the translation provider.

For translation, a dictionary containing files in XLIFF format is shared with the professional translators. The dictionary includes a separate XLIFF file for each locale. Each XLIFF file contains text that is displayed to the end users and placeholders for the corresponding localized text.

Perform the following steps to localize a form and its Document of Record using Human Translators:

1. [Connect AEM with your translation service provider](/help/sites-administering/tc-tic.md) and [create translation integration framework configurations](/help/sites-administering/tc-tic.md).

1. [Associate the pages of your language master](/help/sites-administering/tc-tic.md) with the translation service and framework configurations.

1. [Identify the type of content](/help/sites-administering/tc-rules.md) to translate.

1. [Prepare the content for translation](/help/sites-administering/tc-prep.md) by authoring the language master and creating the root pages of language copies.

1. [Create translation projects](/help/sites-administering/tc-manage.md) to gather the content to translate and to prepare the translation process.

1. Use the translation projects to [manage the content translation process](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptive Form components do not support right to left (RTL) languages. For example, Hebrew.
> -->

