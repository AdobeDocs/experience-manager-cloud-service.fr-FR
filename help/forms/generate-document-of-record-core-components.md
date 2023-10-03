---
title: Comment générer un document d’enregistrement pour Forms adaptatif ?
description: Découvrez comment générer un modèle pour un document d’enregistrement (DE) pour les composants principaux de Forms adaptatif.
exl-id: 15540644-c0c3-45ce-97d3-3bdaa16fb4b6
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '3107'
ht-degree: 96%

---

# Générer un document d’enregistrement pour le Forms adaptatif (composants principaux)

## Présentation {#overview}

Lorsqu’un formulaire est rempli ou envoyé, vous pouvez en conserver un enregistrement au format imprimé ou document. Ici, il s’agit d’un document d’enregistrement (DOR). Il s’agit d’une copie imprimable du formulaire envoyé. Vous pouvez également vous reporter au document d’enregistrement pour les informations que les clients ont remplies à une date ultérieure ou utiliser le document d’enregistrement pour archiver ensemble les formulaires et le contenu au format PDF.

![Document d’enregistrement](assets/document-of-record.png)

Pour créer un document d’enregistrement, un modèle basé sur XFA ou Acrobat est fusionné avec les données collectées via un formulaire adaptatif. Vous pouvez générer un document d’enregistrement automatiquement ou à la demande. L’option à la demande vous permet de spécifier un modèle XFA ou Acrobat personnalisé pour donner une apparence personnalisée à votre document d’enregistrement.

Vous pouvez :

* [Générer un document d’enregistrement basé sur XFA](#generate-an-XFA-based-document-of-record)
* [générer un document d’enregistrement basé sur Acroform (Acrobat Form PDF) ;](#generate-an-Acroform-based-document-of-record)
* [générer automatiquement un document d’enregistrement.](#auto-generate-a-document-of-record)

## Avant de commencer {#components-to-automatically-generate-a-document-of-record}

Avant de commencer à apprendre et à préparer les ressources requises pour un document d’enregistrement :

**Modèle de base :** un modèle XFA (fichier XDP) créé dans Forms Designer ou un formulaire Acrobat Form (AcroForm). Le [modèle de base](#base-template-of-a-document-of-record), également appelé métamodèle, est utilisé pour spécifier les informations de style et de marque pour un document d’enregistrement. Chargez votre modèle XFA (fichier XDP) sur votre instance AEM Forms au préalable..

**Formulaire adaptatif :** le formulaire adaptatif pour lequel le document d’enregistrement doit être généré.

## Générer un document d’enregistrement basé sur XFA {#generate-an-XFA-based-document-of-record}

Chargez votre modèle XFA (fichier XDP) vers votre instance AEM Forms. Suivez les étapes suivantes pour configurer un formulaire adaptatif afin d’utiliser un modèle XFA (fichier XDP) comme modèle de document d’enregistrement :

1. Dans l’instance d’auteur Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire ou créez un formulaire adaptatif, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, appuyez sur **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Modèle de données de formulaire]**, **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Associer le modèle de formulaire en tant que modèle de document d’enregistrement**. Lorsque vous sélectionnez cette option, tous les modèles XFA (fichiers XDP) disponibles sur votre ordinateur s’affichent. Sélectionnez le fichier approprié. Assurez-vous également que le même schéma (schéma de données) est utilisé pour le formulaire adaptatif et le modèle XFA sélectionné (fichier XDP).
1. Cliquez sur **[!UICONTROL Terminé]**.

Votre formulaire adaptatif est maintenant configuré pour utiliser un fichier XDP comme modèle de document d’enregistrement. Les étapes suivantes consistent à [lier les composants de formulaire adaptatif aux champs de modèle correspondants](#bind-adaptive-form-components-with-template-fields).

## Génération d’un document d’enregistrement basé sur Acroform {#generate-an-Acroform-based-document-of-record}

Chargez votre PDF Adobe Acrobat (Acroform) sur votre instance AEM Forms. Suivez les étapes suivantes pour configurer un formulaire adaptatif afin d’utiliser Adobe Acrobat PDF (acroform) comme modèle de document d’enregistrement :

1. Dans l’instance d’auteur Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire ou **[!UICONTROL Créez un formulaire adaptatif]**, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, appuyez sur **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Modèle de données de formulaire]**, **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Associer le modèle de formulaire en tant que modèle de document d’enregistrement**. Lorsque vous sélectionnez cette option, tous les fichiers Acrobat PDF (Acroform) disponibles sur votre ordinateur s’affichent. Sélectionnez l’Acroform que vous souhaitez utiliser.
1. Cliquez sur **[!UICONTROL Terminé]**.

Votre formulaire adaptatif est maintenant configuré pour utiliser un Acroform comme modèle de document d’enregistrement. Les étapes suivantes consistent à [lier les composants de formulaire adaptatif aux champs de modèle correspondants](#bind-adaptive-form-components-with-template-fields).

## Génération automatique d’un document d’enregistrement {#auto-generate-a-document-of-record}

Lorsqu’un formulaire adaptatif est configuré pour générer automatiquement un document d’enregistrement, chaque fois qu’un formulaire est modifié, son document d’enregistrement est mis à jour immédiatement. Par exemple, si un champ est supprimé d’un formulaire adaptatif existant, le champ correspondant est également supprimé et n’est pas visible dans le document d’enregistrement. La génération automatique d’un document d’enregistrement présente de nombreux autres avantages :

* Les développeurs de formulaires n’ont pas à gérer manuellement les liaisons de données. Le document d’enregistrement généré automatiquement prend en charge les mises à jour des liaisons de données.
* Les développeurs de formulaires n’ont pas à masquer manuellement les champs marqués comme exclus du document d’enregistrement. Les documents d’enregistrement générés automatiquement sont préconfigurés pour exclure ces champs.
* L’option de génération automatique du document d’enregistrement permet de gagner du temps lors de la création d’un modèle de formulaire pour le document d’enregistrement.
* L’option Document d’enregistrement généré automatiquement vous permet d’utiliser des styles et des aspects différents en utilisant différents modèles de base. Il permet de sélectionner le style et l’apparence appropriés pour le document d’enregistrement de votre entreprise. Si vous ne spécifiez pas de style, les styles système sont définis en tant que valeur par défaut.
* La génération automatique du document d’enregistrement permet de s’assurer que toute modification du formulaire se répercute immédiatement dans le document d’enregistrement.

Suivez les étapes suivantes pour configurer un formulaire adaptatif afin de générer automatiquement un document d’enregistrement :

1. Dans l’instance d’auteur Experience Manager, cliquez sur **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents].**
1. Sélectionnez un formulaire ou créez un formulaire adaptatif, puis cliquez sur **[!UICONTROL Propriétés]**.
1. Dans la fenêtre Propriétés, appuyez sur **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**, sélectionnez **[!UICONTROL Modèle de données de formulaire]**, **[!UICONTROL Schéma]** ou **[!UICONTROL Aucun]**. Vous pouvez également sélectionner un modèle de formulaire lorsque vous créez un formulaire.
1. Dans la section Configuration du modèle de document d’enregistrement de l’onglet Modèle de formulaire, sélectionnez **Générer un document d’enregistrement**.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Liaison des composants de formulaire adaptatif aux champs de modèle {#bind-adaptive-form-components-with-template-fields}

Liez les champs de formulaire adaptatif aux champs de modèle pour afficher les données de formulaire capturées dans le champ de document d’enregistrement correspondant. Pour lier les composants de formulaire adaptatif aux champs de modèle de document d’enregistrement correspondants :

1. Ouvrez le formulaire adaptatif, configuré pour utiliser un modèle de formulaire personnalisé, pour le modifier.

1. Sélectionnez un composant de formulaire adaptatif et cliquez sur l’icône Configurer ![Configurer](assets/Smock_Wrench_18_N.svg). Il ouvre le navigateur des propriétés.

1. Dans le navigateur des propriétés, recherchez et sélectionnez un champ.

   * (Pour le modèle AcroForm) la propriété **[!UICONTROL Champ de référence de liaison de document d’enregistrement]**.
   * (Pour le modèle XFA) la propriété **[!UICONTROL Référence de liaison de modèle de données]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

<!-- 
In the following video, Adaptive Form components are bound with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

Vous pouvez utiliser des actions d’envoi telles que « Envoyer par e-mail », « Appeler un workflow d’AEM », « Appeler un flux Power Automate », etc., et d’autres [actions d’envoi](configuring-submit-actions.md) pour recevoir un document d’enregistrement.
![Actions d’envoi d’image](/help/forms/assets/submit-actions-img.png)



## Mises à jour incrémentielles du modèle de document d’enregistrement {#document-of-record-template-incremental-updates}

Les formulaires adaptatifs et les documents correspondants des modèles d’enregistrement peuvent évoluer au fil du temps. Vous pouvez choisir d’ajouter, de supprimer ou de modifier des champs sur un formulaire adaptatif ou un modèle de document d’enregistrement.

Lorsque vous apportez des modifications à un modèle de document d’enregistrement et chargez le modèle de document d’enregistrement modifié vers AEM Forms, l’éditeur de formulaires adaptatifs détecte automatiquement les liaisons modifiées et vous informe sur les composants de formulaire adaptatif qui nécessitent de nouvelles liaisons. Il vous permet d’effectuer des mises à jour incrémentielles sur un modèle de document d’enregistrement.

Par exemple, une organisation, *We.Retail*, possède un modèle de document d’enregistrement basé sur AcroForm, *we-retail-facture.pdf*. Le modèle ressemble à ce qui suit :

![Modèle d’origine](assets/we-retail-invoice.png)

Après avoir utilisé le modèle pendant un certain temps, l’entreprise décide de renommer le champ `invoice-number` en champ `bill-number` et de capturer l’adresse électronique des acheteurs. Un développeur met à jour le nom du champ `invoice-number` et ajoute un champ d’e-mail au modèle. Il crée également une version du modèle appelée *we-retail-invoice-v2.pdf*.

![Modèle mis à jour](assets/we-retail-new-invoice.png)

<!--

The developer uploads and applies to the updated template to the adaptive form. The adaptive form automatically detects and displays list of fields where binding has changed.

![Binding Error](assets/we-retail-binding-error.png)

The form developer binds Adaptive Forms fields with corresponding Document of Record template.

-->

>[!VIDEO](assets/we-retail-binding.mp4)

Désormais, lorsque le formulaire adaptatif est envoyé, un document d’enregistrement mis à jour est créé.

![Mise à jour-](assets/we-retail-new-invoice-sent-to-customer.png)

## Points essentiels à prendre en compte lors de l’utilisation de documents d’enregistrement {#key-considerations-when-working-with-document-of-record}

Gardez à l’esprit les points et restrictions suivants lorsque vous utilisez un document d’enregistrement pour les formulaires adaptatifs.

* Les modèles de document d’enregistrement ne prennent pas en charge le texte enrichi. Par conséquent, tout texte enrichi dans le formulaire adaptatif statique ou dans les informations renseignées par l’utilisateur final est remplacé par du texte brut dans le document d’enregistrement.
* Les fragments de document contenus dans un formulaire adaptatif n’apparaissent pas dans le document d’enregistrement. Les fragments de formulaire adaptatif sont toutefois pris en charge.
* La liaison de contenu dans le document d’enregistrement généré pour le formulaire adaptatif de schéma XML n’est pas prise en charge.
* La version localisée du document d’enregistrement est créée sur demande pour un paramètre régional lorsque l’utilisateur demande le rendu du document d’enregistrement. La localisation du document d’enregistrement est effectuée en même temps que la localisation du formulaire adaptatif. <!-- For more information on localization of Document of Record and Adaptive Forms see Using AEM translation workflow to localize Adaptive Forms and Document of Record.-->

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

Le tableau suivant décrit les composants de formulaire adaptatif et les composants XFA correspondants, et s’ils apparaissent dans un document d’enregistrement.

### Champs {#fields}

<table>
 <tbody>
  <tr>
   <th>Composant de formulaire adaptatif</th>
   <th>Composant XFA correspondant</th>
   <th>Inclus par défaut dans le modèle de document d’enregistrement ?</th>
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
   <td>Zone numérique</td>
   <td>Champ numérique</td>
   <td>true</td>
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
   <td>Pièce jointe</td>
   <td> </td>
   <td>false</td>
   <td>Non disponible dans le modèle de document d’enregistrement. Disponible uniquement dans le document d’enregistrement par pièces jointes.</td>
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
| Image | Image | Qu’ils soient liés ou non, les composants TextDraw et Image s’affichent toujours dans le document d’enregistrement concernant un formulaire adaptatif basé sur XSD, sauf si cela est exclu dans les paramètres de document d’enregistrement. |
| Texte | Texte |

### Tableaux {#tables}

Composants tabulaires des formulaires adaptatifs, comme l’en-tête, le pied de page et les lignes associés aux composants XFA correspondants. Vous pouvez mapper des panneaux répétables aux tableaux dans un document d’enregistrement.

## Modèle de base d’un document d’enregistrement {#base-template-of-a-document-of-record}

Le modèle de base fournit les informations de style et d’aspect du document d’enregistrement. Il vous permet de personnaliser l’aspect par défaut du document d’enregistrement généré automatiquement. Par exemple, vous pouvez utiliser des modèles de base pour ajouter le logo de votre entreprise dans l’en-tête et les informations sur le copyright dans le pied de page du document d’enregistrement.

Le gabarit de page du modèle de base est utilisé comme gabarit de page du document du modèle d’enregistrement. Le gabarit de page peut comporter des informations telles que l’en-tête, le pied de page et le numéro de page, que vous pouvez appliquer au document d’enregistrement. Vous pouvez appliquer ces informations au document d’enregistrement à l’aide d’un modèle de base pour générer automatiquement un document d’enregistrement. L’utilisation d’un modèle de base vous permet de modifier les propriétés par défaut des champs.

Respectez toujours les [conventions relatives aux modèles de base](#base-template-conventions) lorsque vous créez un modèle de base.

## Conventions relatives aux modèles de base {#base-template-conventions}

Un modèle de base sert à définir l’en-tête, le pied de page, le style et l’apparence d’un document d’enregistrement. L’en-tête et le pied de page peuvent comporter des informations, comme le logo de l’entreprise et la mention de copyright. Le premier gabarit de page du modèle de base est copié et utilisé comme gabarit de page du document d’enregistrement. Il contient l’en-tête, le pied de page et le numéro de page, ainsi que toute autre information devant s’afficher sur toutes les pages du document d’enregistrement. Même si vous utilisez un modèle de base non conforme aux conventions, le premier gabarit de page du modèle de base sera utilisé dans le modèle de document d’enregistrement. Il vous est fortement recommandé de créer votre modèle de base en fonction des conventions correspondantes et de l’utiliser pour la génération automatique du document d’enregistrement.

**Conventions en matière de gabarits de page**

* Dans le modèle de base, vous devriez nommer le sous-formulaire racine `AF_METATEMPLATE` et le gabarit de page `AF_MASTERPAGE`.

* Le gabarit de page « `AF_MASTERPAGE` » et situé sous le sous-formulaire racine `AF_METATEMPLATE` est privilégié pour extraire les informations sur l’en-tête, le pied de page et le style.

* En l’absence de gabarit de page `AF_MASTERPAGE`, le premier gabarit de page présent dans le modèle de base est utilisé.

**Conventions an matière de style des champs**

* Pour appliquer un style aux champs du document d’enregistrement, le modèle de base fournit les champs situés dans le sous-formulaire `AF_FIELDSSUBFORM` sous le sous-formulaire racine `AF_METATEMPLATE`.

* Les propriétés de ces champs sont appliquées aux champs du document d’enregistrement. Ces champs doivent respecter la convention d’affectation des noms de `AF_<name of field in all caps>_XFO`. Par exemple, le champ contenant une case à cocher doit être nommé `AF_CHECKBOX_XFO`.

Pour créer un modèle de base, procédez comme suit dans Forms Designer.

1. Cliquez sur **[!UICONTROL Fichier]** > **[!UICONTROL Nouveau]**.
1. Sélectionnez l’option **[!UICONTROL Basé sur un modèle]**.

1. Sélectionnez la catégorie **[!UICONTROL Forms - Document d’enregistrement]**.
1. Sélectionnez **[!UICONTROL Modèle de base de DE]**.
1. Cliquez sur **[!UICONTROL Suivant]** et renseignez les informations nécessaires.

1. (Facultatif) Modifiez le style et l’aspect à appliquer aux champs du document d’enregistrement.
1. Enregistrez le formulaire.
   ![Propriétés de base](/help/forms/assets/form-designer-dor-img.png)

Vous pouvez désormais utiliser le formulaire enregistré comme modèle de base d’un document d’enregistrement. Ne modifiez ou ne supprimez aucun des scripts du modèle de base.

**Modification du modèle de base**

* Si vous n’appliquez aucun style aux champs du modèle de base, il est recommandé de les supprimer afin que toutes les mises à niveau du modèle de base soient automatiquement sélectionnées.
* Lors de la modification du modèle de base, ne supprimez, n’ajoutez ou ne modifiez pas les scripts.

Respectez rigoureusement les conventions et instructions mentionnées ci-dessus pour concevoir un modèle de base.

## Personnaliser les informations d’identité graphique d’un document d’enregistrement {#customize-the-branding-information-in-document-of-record}

Lors de la génération d’un document d’enregistrement, vous pouvez modifier les informations d’identité graphique pour le document d’enregistrement sous l’onglet Document d’enregistrement. L’onglet Document d’enregistrement inclut des options telles que le logo, l’apparence, la mise en page, l’en-tête et le pied de page, la clause de non-responsabilité et si vous souhaitez inclure des options de case à cocher et de bouton radio désélectionnées.

Pour localiser les informations de branding que vous saisissez dans l’onglet Document d’enregistrement, assurez-vous que le paramètre régional du navigateur est défini correctement. Pour personnaliser les informations d’identité graphique du document d’enregistrement, suivez les étapes suivantes :

1. Sélectionnez un panneau (panneau racine) dans le document d’enregistrement, puis appuyez sur ![configurer](assets/configure.png).
1. Appuyez sur ![dortab](assets/dortab.png). L’onglet Document d’enregistrement s’affiche.
1. Sélectionnez le modèle par défaut ou un modèle personnalisé pour le rendu du document d’enregistrement. Si vous sélectionnez le modèle par défaut, une vignette d’aperçu du document d’enregistrement s’affiche sous la liste déroulante Modèle.
1. Si vous sélectionnez un modèle par défaut ou un modèle personnalisé, une partie ou la totalité des propriétés suivantes s’affichent sous l’onglet Document d’enregistrement. Spécifiez les propriétés mentionnées ci-dessous pour définir l’apparence du document d’enregistrement :

   1. **Propriétés de base** :
      * **Modèle** : si vous choisissez de sélectionner un modèle personnalisé, recherchez et sélectionnez un fichier XDP sur votre serveur [!DNL AEM Forms]. Si vous souhaitez utiliser un modèle qui n’est pas sur votre serveur [!DNL AEM Forms], vous devez au préalable charger le fichier XDP sur votre serveur [!DNL AEM Forms].
      * **Couleur d’accentuation** : la couleur dans laquelle le texte de l’en-tête et les lignes de séparation sont affichés dans le document ou l’enregistrement PDF.
      * **Famille de polices** : famille de polices du texte dans le document d’enregistrement au format PDF.

      * **Inclure les objets de formulaire qui ne sont pas associés à un modèle de données** : la définition de la propriété inclut des champs non liés du formulaire adaptatif basé sur un schéma dans le document d’enregistrement.

      <!-- **Exclude hidden fields from the Document of Record**: Setting the property identifies the hidden fields for exclusion from Document of Record.-->

      * **Masquer la description des panneaux** : la définition de la propriété exclut la description du panneau/tableau du document d’enregistrement. Applicable au panneau et au tableau.



   1. **Propriétés des champs de formulaire** :
      * **Pour les composants Case à cocher et Bouton radio, afficher uniquement les valeurs sélectionnées** : la définition de la propriété affiche uniquement les valeurs sélectionnées de la case à cocher et du bouton radio dans [!UICONTROL document d’enregistrement].
      * **Séparateur pour plusieurs valeurs** : vous pouvez choisir n’importe quel séparateur, tel qu’une virgule ou un saut de ligne, pour afficher plusieurs valeurs.
      * **Alignement des options** : vous pouvez sélectionner l’alignement de votre choix (horizontal, vertical, identique au formulaire adaptatif) pour définir l’alignement des champs (case à cocher ou bouton radio, par exemple) à afficher sur le [!UICONTROL document d’enregistrement]. Par défaut, l’alignement vertical est défini pour les champs du [!UICONTROL document d’enregistrement]. La définition des propriétés à partir des [!UICONTROL Propriétés des champs de formulaire] du document d’enregistrement remplace les propriétés définies dans la variable [!UICONTROL Alignement des éléments] pour les champs d’un formulaire adaptatif. Si vous sélectionnez l’option [!UICONTROL Identique au formulaire adaptatif], l’alignement tel que configuré dans une instance d’auteur de formulaire adaptatif est utilisé pour les champs du [!UICONTROL document d’enregistrement].
      * **Nombre d’options d’alignement horizontal** : vous pouvez définir le nombre d’options à afficher sur le document d’enregistrement pour l’alignement horizontal.



   1. **Propriétés du gabarit de page** :
      * **Image du logo** : vous pouvez choisir d’utiliser l’image du logo à partir du formulaire adaptatif, sélectionner une image dans le gestionnaire des ressources numériques (DAM) ou en charger une à partir de votre ordinateur.
      * **Titre du formulaire** : titre du document d’enregistrement.
      * **Texte d’en-tête** : texte qui apparaît dans la section d’en-tête du document d’enregistrement.
      * **Libellé clause de non-responsabilité** : libellé de la clause de non-responsabilité.
      * **Clause de non-responsabilité** : texte spécifiant la portée des droits et des obligations sur le document d’enregistrement.
      * **Texte de clause de non-responsabilité** : texte de la clause de non-responsabilité.

      ![Propriétés du gabarit de page](/help/forms/assets/dorpropertiesimg.png)

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

1. Pour enregistrer les modifications d’identité graphique, appuyez sur **[!UICONTROL Terminé]**.



## Mises en page de tableau et de colonne pour les panneaux d’un document d’enregistrement {#table-and-column-layouts-for-panels-in-document-of-record}

Votre formulaire adaptatif peut être étendu, avec plusieurs champs de formulaire. Vous ne pouvez pas enregistrer un document d’enregistrement comme copie exacte du formulaire adaptatif. Vous pouvez maintenant choisir une mise en page de tableau ou de colonne pour enregistrer un ou plusieurs panneaux de formulaires adaptatifs dans le document d’enregistrement PDF.

Avant de générer un document d’enregistrement, dans les paramètres d’un panneau, sélectionnez Tableau ou Colonne pour Mise en page du document d’enregistrement pour ce panneau. Les champs du panneau sont organisés en conséquence dans le document d’enregistrement.

![Champs dans un panneau rendu dans une mise en page Tableau dans le document d’enregistrement](assets/dortablelayout.png)

Champs dans un panneau rendu dans une mise en page Tableau dans le document d’enregistrement

![Champs dans un panneau rendu dans une mise en page Colonne dans le document d’enregistrement](assets/dorcolumnlayout.png)

Champs dans un panneau rendu dans une mise en page Colonne dans le document d’enregistrement

## Paramètres d’un document d’enregistrement {#document-of-record-settings}

Les paramètres d’un document d’enregistrement permettent de sélectionner les options à inclure dans le document d’enregistrement. Par exemple, une banque accepte le nom, l’âge, le numéro de sécurité sociale et le numéro de téléphone dans un formulaire. Le formulaire génère un numéro de compte bancaire et les détails de la banque. Vous pouvez choisir de n’afficher que le nom, le numéro de sécurité sociale, le compte bancaire et les informations bancaires dans le document d’enregistrement.

Les paramètres du composant Document d’enregistrement sont disponible sous ses propriétés. Pour accéder aux propriétés d’un composant, sélectionnez le composant et cliquez sur ![cmppr](assets/cmppr.png) dans le recouvrement. Les propriétés sont répertoriées dans la barre latérale. Vous y trouvez les paramètres suivants.

**Paramètres sur le terrain**

* **Exclure du document d’enregistrement** : la définition de cette propriété sur true exclut le champ du document d’enregistrement. Il s’agit d’une propriété pouvant faire l’objet d’un script appelée « `excludeFromDoR` ». Son comportement dépend de la propriété au niveau du formulaire **Exclure des champs du document d’enregistrement (DE) s’il est masqué**.

* **Afficher le panneau sous forme de tableau** : la définition de cette propriété affiche le panneau sous forme de tableau dans le document d’enregistrement s’il comporte moins de 6 champs. Applicable au panneau uniquement.
* **Exclure le titre du document d’enregistrement** : la définition de la propriété exclut le titre du panneau/tableau du document d’enregistrement. Applicable au panneau et à la table uniquement.
* **Exclure la description du document d’enregistrement** : la définition de la propriété exclut la description du panneau/tableau du document d’enregistrement. Applicable au panneau et à la table uniquement.

**Paramètres des niveaux de formulaires**

* **Inclure les champs non liés dans le document d’enregistrement** : la définition de la propriété comprend les champs non liés du schéma basé sur le formulaire adaptatif du document d’enregistrement. Par défaut, le paramètre est true.
<!-- **Exclude fields from DoR if hidden:** Set the property to exclude the hidden fields from Document of Record at form submission. When you enable [Revalidate on server](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), the server recomputes the hidden fields before excluding those fields from the Document of Record.->>