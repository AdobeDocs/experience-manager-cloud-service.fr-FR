---
title: Générer un PDF d’envoi (anciennement Document d’enregistrement) pour AEM Forms
description: Découvrez comment générer un PDF d’envoi à partir des envois de formulaire pour le Forms adaptatif. Créez un PDF du formulaire envoyé à des fins d’archivage ou de référence.
feature: Adaptive Forms, Foundation Components
exl-id: 16d07932-3308-4b62-8fa4-88c4e42ca7b6
role: User, Developer
source-git-commit: 0b112a5a1830fac9d0170771e052bbb2ef3cadbf
workflow-type: tm+mt
source-wordcount: '4117'
ht-degree: 53%

---

# Générer un PDF d’envoi (anciennement Document d’enregistrement) pour le Forms adaptatif

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

## Vue d’ensemble {#overview}

Lorsqu’un formulaire est rempli ou envoyé, vous pouvez conserver un enregistrement du formulaire, au format imprimé ou au format de document. Cet enregistrement est appelé PDF d’envoi (anciennement Document d’enregistrement, ou DoR). Il s’agit d’un PDF du formulaire envoyé qui peut être imprimé. Vous pouvez également vous reporter au PDF d’envoi pour les informations que les clients ont remplies à une date ultérieure ou utiliser le PDF d’envoi pour archiver ensemble les formulaires et le contenu au format PDF.

![Submission PDF (anciennement Document d’enregistrement)](assets/document-of-record.png)

Pour créer un PDF d’envoi, un modèle basé sur XFA ou Acrobat est fusionné avec les données collectées via un formulaire adaptatif. Vous pouvez générer un PDF d’envoi automatiquement ou à la demande.
L’option à la demande vous permet de spécifier un modèle XFA ou Acrobat personnalisé pour donner une apparence personnalisée à votre PDF d’envoi.

Vous pouvez :

* [Générer une PDF d’envoi basée sur XFA](#generate-an-XFA-based-document-of-record)
* [Générer un PDF d’envoi basé sur Acroform (Acrobat Form PDF)](#generate-an-Acroform-based-document-of-record)
* [Générer automatiquement un PDF d’envoi](#auto-generate-a-document-of-record)

## Avant de commencer {#components-to-automatically-generate-a-document-of-record}

Avant de commencer à apprendre et à préparer les ressources requises pour une PDF d’envoi :

**Modèle de base :** un modèle XFA (fichier XDP) créé dans Forms Designer ou un formulaire Acrobat Form (AcroForm). Le [modèle de base](#base-template-of-a-document-of-record) est utilisé pour spécifier les informations de style et de marque pour un PDF d’envoi. Chargez votre modèle XFA (fichier XDP) sur votre instance AEM Forms au préalable.

**Formulaire adaptatif :** formulaire adaptatif pour lequel le PDF d’envoi doit être généré.

## Générer une PDF d’envoi basée sur XFA {#generate-an-XFA-based-document-of-record}

Chargez votre modèle XFA (fichier XDP) vers votre instance AEM Forms. Pour configurer un formulaire adaptatif afin d’utiliser un modèle XFA (fichier XDP) comme modèle pour Submission PDF, procédez comme suit :

1. Dans l’instance de création Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, sélectionnez **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Associer le modèle de formulaire en tant que modèle de document d’enregistrement**. Lorsque vous sélectionnez cette option, tous les modèles XFA (fichiers XDP) disponibles sur votre ordinateur s’affichent. Sélectionnez le fichier approprié. Assurez-vous également que le même schéma (schéma de données) est utilisé pour le formulaire adaptatif et le modèle XFA sélectionné (fichier XDP).
1. Cliquez sur **[!UICONTROL Terminé]**

Votre formulaire adaptatif est maintenant configuré pour utiliser un fichier XDP comme modèle de PDF d’envoi. L’étape suivante consiste à [lier les composants de formulaire adaptatif aux champs de modèle correspondants](#bind-adaptive-form-components-with-template-fields).

## Générer un PDF d’envoi basé sur Acroform {#generate-an-Acroform-based-document-of-record}

Chargez votre PDF Adobe Acrobat (Acroform) sur votre instance AEM Forms. Pour configurer un formulaire adaptatif afin d’utiliser Adobe Acrobat PDF (Acroform) comme modèle pour l’envoi de PDF, procédez comme suit :

1. Dans l’instance de création Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, sélectionnez **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Associer le modèle de formulaire en tant que modèle de document d’enregistrement**. Lorsque vous sélectionnez cette option, tous les fichiers Acrobat PDF (Acroform) disponibles sur votre ordinateur s’affichent. Sélectionnez le fichier approprié.
1. Cliquez sur **[!UICONTROL Terminé]**

Votre formulaire adaptatif est maintenant configuré pour utiliser un Acroform comme modèle pour Submission PDF. L’étape suivante consiste à [lier les composants de formulaire adaptatif aux champs de modèle correspondants](#bind-adaptive-form-components-with-template-fields).

## Générer automatiquement un PDF de soumission {#auto-generate-a-document-of-record}

Lorsqu’un formulaire adaptatif est configuré pour générer automatiquement un PDF d’envoi, chaque fois qu’un formulaire est modifié, son PDF d’envoi est mis à jour immédiatement. Par exemple, si un champ est supprimé d’un formulaire adaptatif existant, le champ correspondant est également supprimé et n’est pas visible dans le PDF d’envoi. La génération automatique d’une PDF d’envoi présente de nombreux autres avantages :

* Les développeurs de formulaires n’ont pas à gérer manuellement les liaisons de données. Le PDF d’envoi généré automatiquement prend en charge les mises à jour liées à la liaison de données.
* Les développeurs de formulaires n’ont pas à masquer manuellement les champs marqués comme exclus de Submission PDF. Les PDF d’envoi générées automatiquement sont préconfigurées pour exclure ces champs.
* L’option PDF d’envoi générée automatiquement permet de gagner du temps lors de la création d’un modèle de formulaire pour le PDF d’envoi.
* L’option PDF d’envoi générée automatiquement vous permet d’utiliser des styles et des aspects différents en utilisant différents modèles de base. Il permet de sélectionner le style et l’apparence appropriés pour Submission PDF pour votre organisation. Si vous ne spécifiez pas de style, les styles système sont définis en tant que valeur par défaut.
* Le PDF d’envoi généré automatiquement garantit que toute modification du formulaire se répercute immédiatement dans le PDF d’envoi.

Pour configurer un formulaire adaptatif afin de générer automatiquement un PDF d’envoi, procédez comme suit :

1. Dans l’instance de création Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, sélectionnez **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Générer un document d’enregistrement**.
1. Cliquez sur **[!UICONTROL Terminé]**

## Liaison des composants de formulaire adaptatif aux champs de modèle {#bind-adaptive-form-components-with-template-fields}

Liez les champs de formulaire adaptatif aux champs de modèle pour afficher les données de formulaire capturées dans le champ PDF d’envoi correspondant. Pour lier les composants de formulaire adaptatif aux champs de modèle PDF d’envoi correspondants :

1. Ouvrez le formulaire adaptatif, configuré pour utiliser un modèle de formulaire personnalisé, pour le modifier.

1. Sélectionnez un composant de formulaire adaptatif et cliquez sur l’icône Configurer ![Configurer](assets/Smock_Wrench_18_N.svg). Il ouvre le navigateur des propriétés.

1. Dans le navigateur des propriétés, recherchez et sélectionnez un champ.

   * (Pour le modèle AcroForm) la propriété **[!UICONTROL Champ de référence de liaison de document d’enregistrement]**.
   * (Pour le modèle XFA) la propriété **[!UICONTROL Référence de liaison de modèle de données]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

<!-- 
In the following video, Adaptive Form components are bound with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

Vous pouvez utiliser l’action de soumission de workflow Experience Manager Envoyer un e-mail conjointement avec l’étape [Document d’enregistrement) et d’autres actions de soumission](configuring-submit-actions.md) pour recevoir une PDF de soumission.

## Mises à jour incrémentielles du modèle de PDF d’envoi {#document-of-record-template-incremental-updates}

Les formulaires adaptatifs et les modèles de PDF d’envoi correspondants peuvent évoluer au fil du temps. Vous pouvez choisir d’ajouter, de supprimer ou de modifier des champs dans un formulaire adaptatif ou un modèle de PDF d’envoi.

Lorsque vous modifiez un modèle PDF d’envoi et chargez le modèle modifié vers AEM Forms, l’éditeur de Forms adaptatif détecte automatiquement les liaisons modifiées et vous informe sur les composants de formulaire adaptatif qui nécessitent de nouvelles liaisons. Il vous permet d’effectuer des mises à jour incrémentielles sur un modèle de PDF d’envoi.

Par exemple, une organisation, *We.Retail*, possède un modèle de PDF d’envoi basé sur AcroForm, *we-retail-facture.pdf*. Le modèle ressemble à ce qui suit :

![Modèle d’origine](assets/we-retail-invoice.png)

Après avoir utilisé le modèle pendant un certain temps, l’entreprise décide de renommer le champ `invoice-number` en champ `bill-number` et de capturer l’adresse électronique des acheteurs. Un développeur met à jour le nom du champ `invoice-number` et ajoute un champ d’e-mail au modèle. Il crée également une version du modèle appelée *we-retail-facture-v2.pdf*.

![Modèle mis à jour](assets/we-retail-new-invoice.png)

Le développeur charge et applique le modèle mis à jour au formulaire adaptatif. Le formulaire adaptatif détecte et affiche automatiquement la liste des champs où la liaison a changé.

![Erreur de liaison](assets/we-retail-binding-error.png)

Le développeur de formulaires associe les champs de Forms adaptatif au modèle de PDF d’envoi correspondant.

>[!VIDEO](assets/we-retail-binding.mp4)

Désormais, lorsque le formulaire adaptatif est envoyé, un PDF d’envoi mis à jour est créé.

![Mise à jour des lots-](assets/we-retail-new-invoice-sent-to-customer.png)

## Considérations essentielles lors de l’utilisation de Submissions PDF {#key-considerations-when-working-with-document-of-record}

Gardez à l’esprit les points et restrictions suivants lorsque vous utilisez Submission PDF pour Adaptive Forms.

* **Prise en charge du texte enrichi** : Submission PDF prend en charge les balises de balisage HTML dans les champs de texte enrichi. Pour plus d’informations sur les balises prises en charge et les considérations relatives à l’accessibilité, consultez [Balises de balisage HTML prises en charge dans Submission PDF](html-markup-tags-support-in-document-of-record.md).
* Les fragments de document d’un formulaire adaptatif n’apparaissent pas dans le PDF d’envoi. Les fragments de formulaire adaptatif sont toutefois pris en charge.
* La liaison de contenu dans Submission PDF générée pour un formulaire adaptatif de schéma XML n’est pas prise en charge.
* La version localisée de Submission PDF est créée à la demande pour un paramètre régional lorsque l’utilisateur demande le rendu de Submission PDF. La localisation de l’envoi PDF se produit avec la localisation du formulaire adaptatif. <!-- For more information on localization of Document of Record and Adaptive Forms see Using AEM translation workflow to localize Adaptive Forms and Document of Record.-->

<!-- ## Configure an adaptive form to generate  Document of Record {#adaptive-form-types-and-their-documents-of-record}

While creating an adaptive form, in the Form Model tab of Adaptive Form properties, select one the following option: 

* **None**
  Select the option to create an Adaptive Form without a form model. When the option is selected, the Document of Record is automatically generated for your Adaptive Form.

* **[Associate form template as a Document of Record template](creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)**
  
  Select the option to use an XFA Form as a template for Document of Record. 

* **[Generate Document of Record](creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)**
  Select the option to use an XFA Form as a template. When the option is selected, the Document of Record is automatically generated for your Adaptive Form. When you use an XML schema as a template for an Adaptive Form, ensure that the adaptive form and associated XFA Form use the same XML schema as your Adaptive Form
  

When you select a form model, configure Document of Record using options available under Document of Record Template Configuration. See [Document of Record Template Configuration](#document-of-record-template-configuration). -->

## Mappage des éléments d’un formulaire adaptatif {#mapping-of-adaptive-form-elements}

Le tableau suivant décrit les composants de formulaire adaptatif et les composants XFA correspondants, et s’ils apparaissent dans un PDF d’envoi.

### Champs {#fields}

<table>
 <tbody>
  <tr>
   <th>Composant de formulaire adaptatif</th>
   <th>Composant XFA correspondant</th>
   <th>Inclus par défaut dans le modèle PDF d’envoi ?</th>
   <th>Remarques</th>
  </tr>
  <tr>
   <td>Bouton</td>
   <td>Bouton</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Case à cocher</td>
   <td>Case à cocher</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Sélecteur de date</td>
   <td>Champ Date/Heure</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Liste déroulante</td>
   <td>Liste déroulante</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Signature tactile</td>
   <td>Signature tactile</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Zone numérique</td>
   <td>Champ numérique</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Zone de mot de passe</td>
   <td>Champ Mot de passe</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Bouton radio</td>
   <td>Bouton radio</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Zone de texte</td>
   <td>Champ de texte</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Bouton de réinitialisation</td>
   <td>Bouton de réinitialisation</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Bouton Envoyer</td>
   <td><p>Bouton Envoyer par e-mail</p> <p>Bouton Envoyer via HTTP</p> </td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Termes et conditions</td>
   <td> </td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Pièce jointe</td>
   <td> </td>
   <td>false</td>
   <td>Non disponible dans le modèle PDF d’envoi. Disponible uniquement dans Submission PDF par le biais de pièces jointes.</td>
  </tr>
 </tbody>
</table>

### Conteneurs {#containers}

<table>
 <tbody>
  <tr>
   <th>Composant de formulaire adaptatif</th>
   <th>Composant XFA correspondant</th>
   <th>Remarques</th>
  </tr>
  <tr>
   <td>Panneau<br /> </td>
   <td>Sous-formulaire<br /> </td>
   <td>Le panneau répétable est mappé à un sous-formulaire répétable.</td>
  </tr>
 </tbody>
</table>

### Composants statiques {#static-components}

| Composant de formulaire adaptatif | Composant XFA correspondant | Remarques |
|---|---|---|
| Image | Image | Qu’ils soient liés ou non, les composants TextDraw et Image apparaissent toujours dans le PDF d’envoi pour un formulaire adaptatif basé sur XSD, sauf si cela est exclu dans les paramètres de PDF d’envoi. |

### Tableaux {#tables}

Composants tabulaires des formulaires adaptatifs, comme l’en-tête, le pied de page et les lignes associés aux composants XFA correspondants. Vous pouvez mapper des panneaux répétables aux tableaux dans Submission PDF.

## Modèle de base d’un PDF d’envoi {#base-template-of-a-document-of-record}

Le modèle de base fournit des informations de style et d’aspect à Submission PDF. Il vous permet de personnaliser l’aspect par défaut du PDF d’envoi généré automatiquement. Par exemple, vous pouvez utiliser un modèle de base pour ajouter le logo de votre société dans l’en-tête et les informations sur le droit d’auteur dans le pied de page du PDF de soumission.

Le gabarit de page du modèle de base est utilisé comme gabarit de page pour le modèle PDF d’envoi. Le gabarit de page peut comporter des informations telles que l’en-tête, le pied et le numéro de page, que vous pouvez appliquer à Submission PDF. Vous pouvez appliquer ces informations à Submission PDF à l’aide d’un modèle de base pour la génération automatique de Submission PDF. L’utilisation d’un modèle de base permet de modifier les propriétés par défaut des champs.

Respectez toujours les [conventions relatives aux modèles de base](#base-template-conventions) lorsque vous créez un modèle de base.

## Conventions relatives aux modèles de base {#base-template-conventions}

Un modèle de base est utilisé pour définir l’en-tête, le pied de page, le style et l’aspect d’un PDF d’envoi. L’en-tête et le pied de page peuvent comporter des informations, comme le logo de l’entreprise et la mention de droit d’auteur. Le gabarit de page du modèle de base est copié et utilisé comme gabarit de page du PDF d’envoi. Il contient l’en-tête, le pied de page et le numéro de page, ainsi que toute autre information devant apparaître sur toutes les pages du PDF d’envoi. Si vous utilisez un modèle de base non conforme aux conventions en matière de modèles de base, le premier gabarit de page du modèle de base est toujours utilisé dans le modèle PDF d’envoi. Il est vivement recommandé de concevoir votre modèle de base en fonction de ses conventions et de l’utiliser pour la génération automatique du code PDF d’envoi.

**Conventions en matière de gabarits de page**

* Dans le modèle de base, vous devriez nommer le sous-formulaire racine `AF_METATEMPLATE` et le gabarit de page `AF_MASTERPAGE`.

* Le gabarit de page « `AF_MASTERPAGE` » et situé sous le sous-formulaire racine `AF_METATEMPLATE` est privilégié pour extraire les informations sur l’en-tête, le pied de page et le style.

* En l’absence de gabarit de page `AF_MASTERPAGE`, le premier gabarit de page présent dans le modèle de base est utilisé.

**Conventions an matière de style des champs**

* Pour appliquer un style aux champs du PDF d’envoi, le modèle de base fournit les champs situés dans le sous-formulaire `AF_FIELDSSUBFORM` sous le sous-formulaire racine `AF_METATEMPLATE`.

* Les propriétés de ces champs sont appliquées aux champs dans le PDF d’envoi. Ces champs doivent respecter la convention d’affectation des noms de `AF_<name of field in all caps>_XFO`. Par exemple, le champ contenant une case à cocher doit être nommé `AF_CHECKBOX_XFO`.

Pour créer un modèle de base, procédez comme suit dans Forms Designer.

1. Cliquez sur **[!UICONTROL Fichier]** > **[!UICONTROL Nouveau]**.
1. Sélectionnez l’option **[!UICONTROL Basé sur un modèle]**.

1. Sélectionnez la catégorie **[!UICONTROL Forms - Document d’enregistrement]**.
1. Sélectionnez **[!UICONTROL Modèle de base de DE]**.
1. Cliquez sur **[!UICONTROL Suivant]** et renseignez les informations nécessaires.

1. (Facultatif) Modifiez le style et l’aspect à appliquer aux champs du PDF d’envoi.
1. Enregistrez le formulaire.

Vous pouvez désormais utiliser le formulaire enregistré comme modèle de base pour Submission PDF. Ne modifiez ou ne supprimez aucun des scripts du modèle de base.

**Modification du modèle de base**

* Si vous n’appliquez aucun style aux champs du modèle de base, il est recommandé de les supprimer afin que toutes les mises à niveau du modèle de base soient automatiquement reportées.
* Lors de la modification du modèle de base, ne supprimez, n’ajoutez ou ne modifiez pas les scripts.

Respectez rigoureusement les conventions et instructions mentionnées ci-dessus pour concevoir un modèle de base.

## Personnaliser les informations d’identité graphique dans Submission PDF {#customize-the-branding-information-in-document-of-record}

Lors de la génération d’une PDF de soumission, vous pouvez modifier les informations de branding de la PDF de soumission dans l’onglet Document d’enregistrement. L’onglet Document d’enregistrement inclut des options telles que le logo, l’apparence, la mise en page, l’en-tête et le pied de page, la clause de non-responsabilité et si vous souhaitez inclure des options de case à cocher et de bouton radio désélectionnées.

Pour localiser les informations de branding que vous saisissez dans l’onglet Document d’enregistrement, assurez-vous que les paramètres régionaux du navigateur sont définis correctement. Pour personnaliser les informations d’identité graphique de Submission PDF, procédez comme suit :

1. Sélectionnez un panneau (panneau racine) dans le PDF d’envoi, puis sélectionnez ![configurer](assets/configure.png).
1. Sélectionnez ![dortab](assets/dortab.png). L’onglet Document d’enregistrement s’affiche.
1. Sélectionnez le modèle par défaut ou un modèle personnalisé pour le rendu du PDF d’envoi. Si vous sélectionnez le modèle par défaut, une vignette d’aperçu du PDF d’envoi s’affiche sous la liste déroulante Modèle.
1. Selon que vous sélectionnez un modèle par défaut ou un modèle personnalisé, certaines des propriétés suivantes, ou toutes les propriétés, apparaissent dans l’onglet Document d’enregistrement. Spécifiez les propriétés mentionnées ci-dessous pour définir l’apparence du PDF d’envoi :

   1. **Propriétés de base** :
      * **Modèle** : si vous choisissez de sélectionner un modèle personnalisé, recherchez et sélectionnez un fichier XDP sur votre serveur [!DNL AEM Forms]. Si vous souhaitez utiliser un modèle qui n’est pas sur votre serveur [!DNL AEM Forms], vous devriez au préalable charger le fichier XDP sur votre serveur [!DNL AEM Forms].
      * **Couleur d’accentuation** : la couleur dans laquelle le texte de l’en-tête et les lignes de séparation sont affichés dans le PDF d’envoi.
      * **Famille de polices** : famille de polices du texte dans la PDF d’envoi.

        >[!NOTE]
        >
        > AEM Forms propose toute une gamme de polices intégrées qui s’intègrent de manière transparente aux fichiers PDF. Pour afficher la liste des polices prises en charge, [cliquez ici](/help/forms/supported-out-of-the-box-fonts.md).

      * **Inclure les objets de formulaire qui ne sont pas liés au modèle de données** : la définition de la propriété inclut des champs non liés du formulaire adaptatif basé sur un schéma dans le PDF d’envoi.
      * **Exclure les champs masqués du document d’enregistrement** : la définition de la propriété identifie les champs masqués à exclure du PDF d’envoi.
      * **Masquer la description des panneaux** : la définition de la propriété exclut la description du panneau/tableau de Submission PDF. Applicable au panneau et au tableau.

      ![Propriétés de base](/help/forms/assets/basicpropertiesdor.png)

   2. **Propriétés des champs de formulaire** :
      * **Pour les composants Case à cocher et Bouton radio, afficher uniquement les valeurs sélectionnées** : la définition de la propriété affiche uniquement les valeurs sélectionnées de la case à cocher et du bouton radio dans [!UICONTROL document d’enregistrement].
      * **Séparateur pour plusieurs valeurs** : vous pouvez choisir n’importe quel séparateur, tel qu’une virgule ou un saut de ligne, pour afficher plusieurs valeurs.
      * **Alignement des options** : vous pouvez sélectionner l’alignement de votre choix (horizontal, vertical, identique au formulaire adaptatif) pour définir l’alignement des champs (case à cocher ou bouton radio, par exemple) à afficher sur le [!UICONTROL document d’enregistrement]. Par défaut, l’alignement vertical est défini pour les champs du [!UICONTROL document d’enregistrement]. La définition des propriétés à partir des [!UICONTROL Propriétés des champs de formulaire] du document d’enregistrement remplace les propriétés définies dans la variable [!UICONTROL Alignement des éléments] pour les champs d’un formulaire adaptatif. Si vous sélectionnez l’option [!UICONTROL Identique au formulaire adaptatif], l’alignement tel que configuré dans une instance de création de formulaire adaptatif est utilisé pour les champs du [!UICONTROL document d’enregistrement].
      * **Nombre d’options d’alignement horizontal**:You peut définir le nombre d’options à afficher dans le PDF d’envoi pour l’alignement horizontal.

      ![Propriétés des champs de formulaire](/help/forms/assets/formfieldpropertiesdor.png)

   3. **Propriétés du gabarit de page** :
      * **Image du logo** : vous pouvez choisir d’utiliser l’image du logo à partir du formulaire adaptatif, sélectionner une image dans le gestionnaire des ressources numériques (DAM) ou en charger une à partir de votre ordinateur.
      * **Titre du formulaire** : titre du document d’enregistrement.
      * **Texte d’en-tête** : texte qui apparaît dans la section d’en-tête du PDF d’envoi.
      * **Libellé clause de non-responsabilité** : libellé de la clause de non-responsabilité.
      * **Clause de non-responsabilité** : texte spécifiant la portée des droits et des obligations sur le PDF de soumission.
      * **Texte de clause de non-responsabilité** : texte de la clause de non-responsabilité.

      ![Propriétés du gabarit de page](/help/forms/assets/masterpagepropertiesdor.png)

   >[!NOTE]
   >
   >Si vous utilisez un modèle de formulaire adaptatif créé avec une version de Designer antérieure à la version 6.3, pour que les propriétés Couleur d’accentuation et Famille de polices fonctionnent, assurez-vous de la présence des éléments suivants dans votre modèle de formulaire adaptatif sous le sous-formulaire racine :

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Pour enregistrer les modifications d’identité graphique, sélectionnez **[!UICONTROL Terminé]**.

>[!NOTE]
> 
> Pour afficher un titre de formulaire personnalisé dans votre PDF d’envoi, modifiez le **Titre du formulaire personnalisé** dans **Propriétés du document d’enregistrement** > **Propriétés de page du Principal**. Ce titre personnalisé :
> 
> * Apparaît dans l’en-tête du PDF généré
> * Apparaît comme titre dans les propriétés du document PDF
> * S’affiche en tant que titre d’affichage initial à l’ouverture du PDF

## Prise en charge des documents d’enregistrement dans l’éditeur de formulaire adaptatif {#dor-support-in-adaptiveform}

Vous pouvez configurer le modèle [!UICONTROL Document d’enregistrement] directement à partir de l’éditeur de formulaire adaptatif ou de l’éditeur de modèle de formulaire adaptatif.

Effectuez les étapes suivantes à partir de l’instance de création de l’éditeur de formulaire adaptatif :

1. Sélectionnez le composant **[!UICONTROL Conteneur de formulaires adaptatifs (racine)]**.
1. Cliquez sur l’![Icône Configurer](/help/forms/assets/configure-icon.svg) pour ouvrir les **[!UICONTROL Propriétés]** du conteneur de formulaires adaptatifs.
1. Ouvrez l’onglet **[!UICONTROL Modèle de document d’enregistrement]** et sélectionnez l’une des options suivantes :
   * **[!UICONTROL Aucun]** : lorsque cette option est sélectionnée, aucun modèle de [!UICONTROL document d’enregistrement] n’est créé pour votre formulaire adaptatif.
   * **[!UICONTROL Associer le modèle de formulaire en tant que modèle de document d’enregistrement]**:When si cette option est sélectionnée, le formulaire XFA est utilisé comme modèle pour l’envoi de PDF.
   * **[!UICONTROL Générer un document d’enregistrement]** : lorsque cette option est sélectionnée, le modèle de [!UICONTROL document d’enregistrement] est généré automatiquement pour votre formulaire adaptatif.

1. Sélectionnez ![Enregistrer](/help/forms/assets/check-button.png) pour enregistrer les propriétés.

![Prise en charge des modèles de document d’enregistrement](/help/forms/assets/dor-templatesupport.png)

>[!NOTE]
>
>Lorsque le modèle de [!UICONTROL document d’enregistrement] est créé à l’aide d’un éditeur de modèle de formulaire adaptatif, seules deux options sont disponibles sous l’onglet [!UICONTROL Modèle de document d’enregistrement] : [!UICONTROL Aucun] et [!UICONTROL Générer un document d’enregistrement].

## Dispositions de tableaux et de colonnes pour les panneaux dans Submission PDF {#table-and-column-layouts-for-panels-in-document-of-record}

Votre formulaire adaptatif peut être étendu, avec plusieurs champs de formulaire. Vous ne pouvez pas enregistrer un PDF d’envoi en tant que copie exacte du formulaire adaptatif. Vous pouvez maintenant choisir une disposition de tableau ou de colonne pour enregistrer un ou plusieurs panneaux de formulaires adaptatifs dans le PDF d’envoi.

Avant de générer un PDF d’envoi, dans les paramètres d’un panneau, sélectionnez Tableau ou Colonne pour Mise en page du document d’enregistrement pour ce panneau. Les champs du panneau sont organisés en conséquence dans le PDF d’envoi.

![Champs dans un panneau rendu dans une mise en page de tableau dans le PDF d’envoi](assets/dortablelayout.png)

Champs dans un panneau rendu dans une mise en page de tableau dans le PDF d’envoi

![Champs dans un panneau rendu dans une mise en page Colonne dans le PDF d’envoi](assets/dorcolumnlayout.png)

Champs dans un panneau rendu dans une mise en page Colonne dans le PDF d’envoi

## Paramètres d’envoi de PDF {#document-of-record-settings}

Les paramètres de PDF d’envoi vous permettent de choisir les options que vous souhaitez inclure dans la PDF d’envoi. Par exemple, une banque accepte le nom, l’âge, le numéro de sécurité sociale et le numéro de téléphone dans un formulaire. Le formulaire génère un numéro de compte bancaire et les détails de la banque. Vous pouvez choisir de n’afficher que le nom, le numéro de sécurité sociale, le compte bancaire et les informations bancaires dans Submission PDF.

Les paramètres du composant Document d’enregistrement sont disponible sous ses propriétés. Pour accéder aux propriétés d’un composant, sélectionnez le composant et cliquez sur ![cmppr](assets/cmppr.png) dans le recouvrement. Les propriétés sont répertoriées dans la barre latérale. Vous y trouvez les paramètres suivants.

**Paramètres sur le terrain**

* **Exclure du document d’enregistrement** : la définition de la propriété sur true exclut le champ du PDF d’envoi. Il s’agit d’une propriété pouvant faire l’objet d’un script appelée « `excludeFromDoR` ». Son comportement dépend de la propriété au niveau du formulaire **Exclure des champs du document d’enregistrement (DE) s’il est masqué**.

* **Afficher le panneau sous forme de tableau :** la définition de cette propriété affiche le panneau sous forme de tableau dans le PDF d’envoi s’il contient moins de 6 champs. Applicable au panneau uniquement.
* **Exclure le titre du document d’enregistrement** : la définition de la propriété exclut le titre du panneau/tableau du PDF d’envoi. Applicable au panneau et à la table uniquement.
* **Exclure la description du document d’enregistrement :** la définition de la propriété exclut la description du panneau/tableau de la PDF d’envoi. Applicable au panneau et à la table uniquement.

**Paramètres des niveaux de formulaires**

* **Inclure les champs non liés dans le document d’enregistrement :** la définition de la propriété inclut les champs non liés du schéma basé sur le formulaire adaptatif dans le PDF d’envoi. Par défaut, le paramètre est true.
* **Exclure les champs du document d’enregistrement s’ils sont masqués :** définissez la propriété pour exclure les champs masqués du PDF d’envoi lors de l’envoi du formulaire. Lorsque vous activez [Revalider sur le serveur](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), le serveur recalcule les champs masqués avant d’exclure ces champs du PDF d’envoi.

## Utiliser un fichier XCI personnalisé

Un fichier XCI permet de définir différentes propriétés d’un document. Forms as a Cloud Service comporte un fichier XCI maître. Vous pouvez utiliser un fichier XCI personnalisé pour remplacer une ou plusieurs propriétés par défaut spécifiées dans le fichier XCI maître. Par exemple, vous pouvez choisir d’incorporer une police dans un document ou d’activer la propriété balisée pour tous les documents. Le tableau suivant indique les options XCI :

| Option XCI | Description |
|--- |--- |
| config/present/pdf/creator | Identifie le créateur du document à l’aide de l’entrée Créateur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le [guide de référence PDF](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/pdf/producer | Identifie le producteur du document à l’aide de l’entrée Producteur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le [guide de référence PDF](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/layout | Contrôle si la sortie est un panneau unique ou si elle est paginée. |
| config/present/pdf/compression/level | Indique le degré de compression à utiliser lors de la génération d’un document PDF. |
| config/present/pdf/fontInfo/embed | Contrôle l’incorporation des polices dans le document de sortie. |
| config/present/pdf/scriptModel | Contrôle si des informations spécifiques à XFA sont incluses dans le document PDF de sortie. |
| config/present/common/data/adjustData | Contrôle si l’application XFA ajuste les données après la fusion. |
| config/present/pdf/renderPolicy | Contrôle si la génération du contenu de la page est effectuée sur le serveur ou différée au client. |
| config/present/common/locale | Spécifie les paramètres régionaux par défaut utilisés dans le document de sortie. |
| config/present/destination | Lorsque contenu par un élément présent, indique le format de sortie. Lorsqu’il est contenu par un élément openAction, spécifie l’action à effectuer lors de l’ouverture du document dans un client interactif. |
| config/present/output/type | Spécifie le type de compression à appliquer à un fichier ou le type de sortie à produire. |
| config/present/common/temp/uri | Spécifie l’URI du formulaire. |
| config/present/common/template/base | Fournit un emplacement de base pour les URI dans le design de formulaire. Lorsque cet élément est absent ou vide, l’emplacement du design de formulaire est utilisé comme base. |
| config/present/common/log/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/output/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/script/currentPage | Indique la page initiale à l’ouverture du document. |
| config/present/script/exclude | Informe Forms as a Cloud Service des événements à ignorer. |
| config/present/pdf/linearized | Contrôle si le document PDF de sortie est linéarisé. |
| config/present/script/runScripts | Contrôle l’ensemble de scripts que Forms as a Cloud Service exécute. |
| config/present/pdf/tagged | Contrôle l’inclusion de balises dans le document PDF de sortie. Les balises, dans le contexte d’un PDF, sont des informations supplémentaires incluses dans un document afin d’exposer la structure logique du document. Les balises aident à l’accessibilité et au reformatage. Par exemple, un numéro de page peut être balisé en tant qu’artefact afin qu’un lecteur d’écran ne l’indique pas au milieu du texte. Bien que les balises rendent un document plus utile, elles augmentent également sa taille et le temps de traitement pour le créer. |
| config/present/pdf/fontInfo/alwaysEmbed | Spécifie une police incorporée dans le document de sortie. |
| config/present/pdf/fontInfo/neverEmbed | Spécifie une police qui ne doit jamais être incorporée dans le document de sortie. |
| config/present/pdf/pdfa/part | Spécifie le numéro de version de la spécification PDF/A à laquelle le document est conforme. |
| config/present/pdf/pdfa/amd | Spécifie le niveau de modification de la spécification PDF/A. |
| config/present/pdf/pdfa/conformance | Spécifie le niveau de conformité avec la spécification PDF/A. |
| config/present/pdf/version | Spécifie la version du document PDF à générer |
| config/present/pdf/version/map | Spécifie les polices de secours pour le document. |

>[!NOTE]
>
> AEM Forms propose toute une gamme de polices intégrées qui s’intègrent de manière transparente aux fichiers PDF. Pour afficher la liste des polices prises en charge, [cliquez ici](/help/forms/supported-out-of-the-box-fonts.md).


### Utilisez un fichier XCI personnalisé dans votre environnement Forms as a Cloud Service

1. Ajoutez le fichier XCI personnalisé à votre projet de développement.
1. Spécifiez les [propriété intégrée](/help/implementing/deploying/configuring-osgi.md) suivantes :

   ```JSON
    {
     "xciFilePath": "[path of XCI file]"
    }
   ```

   Par exemple,

   ```JSON
    {
     "xciFilePath": "/content/dam/formsanddocuments/customMinionProBoldAndTagged.xci"
    }
   ```

1. Déployez le projet dans votre environnement Cloud Service.

### Utilisez un fichier XCI personnalisé dans votre environnement de développement Forms as a Cloud Service local

1. Chargez le fichier XCI dans votre environnement de développement local.
1. Ouvrez le gestionnaire de configuration Cloud Service SDK. L’URL par défaut est : <http://localhost:4502/system/console/configMgr>.
1. Recherchez et ouvrez la configuration **[!UICONTROL du canal web pour la communication interactive et les formulaires adaptatifs]**.
1. Spécifiez le chemin d’accès du fichier XCI et cliquez sur **[!UICONTROL Enregistrer]**.


## Voir également {#see-also}

{{see-also}}
