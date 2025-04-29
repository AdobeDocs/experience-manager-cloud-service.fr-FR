---
title: Comment créer des formulaires autonomes basés sur des modèles de composants principaux ou de Edge Delivery Services et les publier sur Edge Delivery Services
description: Cet article explique comment créer un Forms adaptatif en sélectionnant un modèle basé sur les composants principaux ou un modèle basé sur Edge Delivery Services dans l’assistant de création de formulaire. Vous pouvez également publier les formulaires dans AEM Edge Delivery Services.
feature: Edge Delivery Services
role: User
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: c68e98cfe442d0b5a928fde596e193073d5cac21
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 29%

---


# De la création à la publication : AEM Forms sur Edge Delivery Services

<span class="preview"> Cette fonctionnalité est disponible par le biais du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail avec le nom de votre organisation et le nom de votre référentiel GitHub à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

Adobe Experience Manager (AEM) vous permet de créer des formulaires attrayants, réactifs et dynamiques. Il propose plusieurs méthodes de création, chacune adaptée à différents besoins et niveaux d’expertise des utilisateurs et utilisatrices&#x200B;

Cet article se concentre sur l’approche selon laquelle les formulaires sont créés dans l’environnement AEM et publiés via Edge Delivery Services. Forms créé à l’aide de modèles basés sur les composants principaux peut être publié sur AEM et Edge Delivery Services, offrant ainsi une certaine flexibilité de déploiement. En revanche, les formulaires créés à l’aide de modèles basés sur Edge Delivery Services ne peuvent être publiés que sur Edge Delivery Services&#x200B;

![Créer et publier un formulaire adaptatif](/help/edge/docs/forms/universal-editor/assets/author-publish-af.png){width=50% align=center}

## Avantages de la création de formulaires dans AEM et de la publication avec Edge Delivery Services :

* **Préservation des workflows AEM existants** : les entreprises peuvent continuer à utiliser les workflows AEM et les structures de gouvernance qu’elles ont établis, en veillant à la cohérence et au contrôle de la création de contenu&#x200B;

* **Performances améliorées** : la publication via Edge Delivery Services accélère les temps de rendu, améliore l’expérience utilisateur et réduit les temps de chargement des pages&#x200B;

* **SEO amélioré** : Edge Delivery Services est conçu pour diffuser du contenu avec des scores Google Lighthouse élevés, ce qui peut conduire à une meilleure optimisation du moteur de recherche et à une visibilité accrue. &#x200B;

* **Options de déploiement flexibles** : Forms créé avec les composants principaux peut être publié sur AEM et Edge Delivery Services, offrant ainsi une certaine flexibilité au niveau des stratégies de déploiement&#x200B;

## Avant de commencer

Avant de commencer à créer des formulaires dans AEM et à les publier via Edge Delivery Services, assurez-vous que les conditions préalables suivantes sont remplies :

* Assurez-vous qu’un référentiel Github est configuré pour Edge Delivery Services.
   * Si vous ne disposez pas d’un référentiel, [nouveau projet AEM préconfiguré avec le bloc de Forms adaptatif](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block).
   * Si vous disposez d’un référentiel, ajoutez le bloc de Forms adaptatif à votre référentiel existant. Vous trouverez des instructions détaillées dans la [Prise en main de Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project).
* Établir une connexion entre votre environnement AEM et le référentiel GitHub. [Comment faire ? ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)

Diagramme de flux de décision destiné à guider la configuration et la publication de Forms adaptatif :

![Workflow du référentiel Github](/help/forms/assets/repo-workflow.png){width=auto}

## Créer des formulaires dans AEM et les publier dans Edge Delivery Services

Pour créer des formulaires dans AEM et les publier sur Edge Delivery Services, procédez comme suit :

[1. Choisissez un modèle et créez le formulaire](#choose-a-template-and-create-the-form)

[2. Créer le formulaire](#author-the-form)

[3. Publication d’un formulaire](#publish-a-form)

### Choisir un modèle et créer le formulaire

Vous pouvez créer des formulaires sur une instance AEM pour les publier dans Edge Delivery Services à l’aide des méthodes suivantes :

>[!BEGINTABS]

>[!TAB modèle basé sur Edge Delivery Services]

Pour choisir le modèle et créer le formulaire, procédez comme suit :

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant.
1. Dans l’onglet **Source**, sélectionnez un modèle basé sur **Edge Delivery Services** :

   ![Créer des formulaires EDS](/help/edge/assets/create-eds-forms.png)

   Lorsque vous sélectionnez un modèle basé sur **Edge Delivery Services**, le bouton **[!UICONTROL Créer]** est activé.
1. (Facultatif) Dans les onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]**, vous pouvez sélectionner une source de données ou une action d’envoi.
1. (Facultatif) Dans l’onglet **[!UICONTROL Diffusion]**, vous pouvez spécifier une date de publication ou d’annulation de publication pour un formulaire.
1. Cliquez sur **[!UICONTROL Créer]** et l’assistant **Créer un formulaire** s’affiche :

   1. Spécifiez le **Nom** et le **Titre**.
   1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est la suivante :
      `https://github.com/wkndforms/edsforms`

   ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png)

   Lorsque vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

   ![créer le formulaire](/help/edge/assets/author-form.png)
1. Cliquez sur **[!UICONTROL Créer]** pour créer le formulaire. Vous pouvez désormais [créer le formulaire à l’aide de l’éditeur universel](#author-the-form).

>[!TAB  Modèle basé sur les composants principaux ]

Pour choisir le modèle et créer le formulaire, procédez comme suit :

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant.
1. Dans l’onglet **Source**, sélectionnez un modèle **basé sur les composants principaux** et un **thème**, le bouton **[!UICONTROL Créer]** est activé. :

![ Modèle basé sur les composants principaux ](/help/forms/assets/core-component-based-template.png)

1. (Facultatif) Dans les onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]**, vous pouvez sélectionner une source de données ou une action d’envoi.
1. (Facultatif) Dans l’onglet **[!UICONTROL Diffusion]**, vous pouvez spécifier une date de publication ou d’annulation de publication pour un formulaire.
1. Cliquez sur **[!UICONTROL Créer]** et l’assistant **Créer un formulaire** s’affiche pour :
   1. Spécifiez le **Nom** et le **Titre**.
   2. Indiquez l’emplacement dans le champ **Chemin** où le formulaire adaptatif doit être enregistré.

   ![Assistant Créer un formulaire](/help/forms/assets/create-cc-form.png)

   Lorsque vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur de formulaires adaptatifs à des fins de création.

   ![ Éditeur de formulaire adaptatif ](/help/forms/assets/af-editor-form.png)

1. Cliquez sur **[!UICONTROL Créer]** pour créer le formulaire. Vous pouvez désormais [créer le formulaire à l’aide de l’éditeur de formulaire adaptatif](#author-the-form).

>[!ENDTABS]

### Créer le formulaire

Les formulaires créés à l’aide du modèle basé sur Edge Delivery Services s’ouvrent dans l’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) en vue de leur création. Toutefois, les formulaires créés à l’aide du modèle basé sur les composants principaux s’ouvrent dans l’éditeur de formulaires adaptatifs à des fins de création.

Effectuez les étapes suivantes pour créer des formulaires à l’aide de l’éditeur universel pour le modèle basé sur Edge Delivery Services ou à l’aide de l’éditeur de formulaire adaptatif pour le modèle basé sur les composants principaux :

>[!BEGINTABS]

>[!TAB modèle basé sur Edge Delivery Services]


1. Ouvrez l’explorateur de contenu et accédez au composant **[!UICONTROL Formulaire adaptatif]** dans l’**arborescence de contenu**.

   ![arborescence de contenu](/help/edge/assets/content-tree.png)

1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.
   ![ajouter un composant](/help/edge/assets/add-component.png)

   La capture d’écran ci-dessous affiche le `Registration Form` créé dans l’éditeur universel :

   ![Formulaire de contact](/help/edge/assets/contact-us.png)

>[!NOTE]
>
> Pour obtenir des instructions détaillées sur la création d’un formulaire adaptatif à l’aide de l’éditeur universel, [cliquez ici](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

Vous pouvez maintenant [configurer et personnaliser des actions d’envoi de formulaire](/help/edge/docs/forms/universal-editor/submit-action.md).

>[!TAB  Modèle basé sur les composants principaux ]

1. Cliquez sur **[!UICONTROL Insérer le composant]** dans la section **Faire glisser les composants ici**.

   ![Faites glisser les composants ici](/help/forms/assets/drag-components-af-editor.png)

1. Ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

   ![Ajouter des composants](/help/forms/assets/add-component-af.png)

La capture d’écran ci-dessous affiche le `Enrollment Form` créé dans l’éditeur de formulaire adaptatif :

![ Éditeur de formulaire adaptatif ](/help/forms/assets/af-editor-form.png)

>[!NOTE]
>
> Pour obtenir des conseils détaillés sur la création d’un formulaire adaptatif basé sur le modèle de composant principal, [cliquez ici](/help/forms/creating-adaptive-form-core-components.md).

Vous pouvez maintenant [configurer les actions d’envoi de formulaires](/help/forms/configure-submit-actions-core-components.md).

>[!ENDTABS]

### Publier le formulaire

Pour publier un formulaire adaptatif sur Edge Delivery Services, vous devez [créer une configuration Edge Delivery Services sur une instance AEM](#create-an-edge-delivery-services-configuration).

#### Création d’une configuration Edge Delivery Services

Pour créer la configuration Edge Delivery Services, procédez comme suit :

>[!BEGINTABS]
>[!TAB Pour les formulaires créés à l’aide du modèle basé sur Edge Delivery Services ]


La configuration Edge Delivery Services des formulaires basés sur le modèle Edge Delivery Services est créée automatiquement dans le conteneur de configurations du formulaire.

![Configuration Edge Delivery Services](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB Pour les formulaires créés à l’aide du modèle basé sur les composants principaux]

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Configuration de Edge Delivery Services]** sur votre instance de création AEM Forms as a Cloud Service.

   ![Sélectionner la configuration Edge Delivery Services](/help/edge/assets/select-eds-conf.png)

1. Sélectionnez le dossier correspondant au nom du formulaire. Par exemple, si votre formulaire est appelé `enrollment-form`, choisissez le dossier `forms/enrollment-form` et cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Configuration]** :

   ![Configuration Edge Delivery Services](/help/forms/assets/create-eds-conf.png)

1. Cliquez sur la configuration **[!UICONTROL Edge Delivery Services]** puis sur **[!UICONTROL Propriétés]** pour afficher les propriétés :

   ![Configuration créée automatiquement](/help/forms/assets/eds-conf.png)

   La configuration de Edge Delivery Services s’affiche.

1. Spécifiez les éléments suivants dans la Configuration Edge Delivery Services :

   * **Organisation** : indiquez le nom de votre organisation GitHub.

   * **Nom du site** : spécifiez le nom de votre référentiel GitHub.
   * **Branche** : indiquez le nom de la branche. Laissez la zone de texte vide si vous utilisez la branche principale.
   * **(Facultatif) Hôte Edge** : laissez l’option Hôte Edge telle quelle. Le formulaire est publié dans les environnements de prévisualisation (.page) et d’activation (.live).
   * **(Facultatif) Jeton d’authentification du site** : utilisez le jeton d’authentification du site pour authentifier en toute sécurité les requêtes entre votre instance AEM et Edge Delivery Services.

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration est créée.

>[!ENDTABS]

#### Accès au formulaire sous Edge Delivery Services

Pour accéder au formulaire sous Edge Delivery Services, il est obligatoire de le publier. Effectuez les étapes suivantes pour publier le formulaire :

>[!BEGINTABS]
>[!TAB Dans l’éditeur universel]

1. Publiez le formulaire en cliquant sur le bouton **[!UICONTROL Publier]** dans le coin supérieur droit de l’éditeur universel.

![publier le formulaire](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Reportez-vous à l’article [Publier et déployer](/help/edge/docs/forms/universal-editor/publish-forms.md) pour savoir comment publier un formulaire dans Edge Delivery Services.

>[!TAB Dans l’éditeur de formulaire adaptatif]

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire que vous souhaitez publier.

1. Cliquez sur l’option **[!UICONTROL Publier]** dans la barre d’outils, consultez toutes les ressources de référence qui seraient publiées avec le formulaire.

![Publication d’un formulaire dans l’éditeur de formulaire adaptatif](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Reportez-vous à l’article [Gérer la publication dans Experience Manager Forms](/help/forms/manage-publication.md) pour savoir comment publier un formulaire dans l’éditeur de formulaires adaptatifs.

>[!ENDTABS]

* **Version intermédiaire (pour les tests)** : la version intermédiaire affiche la version de travail dépubliée du formulaire à des fins de test. Utilisez le format d’URL suivant pour prévisualiser le formulaire avant sa mise en ligne :

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`



* **Version en direct (formulaire publié)** : la version active affiche la dernière version publiée du formulaire, accessible aux utilisateurs finaux. Utilisez le format d’URL suivant pour accéder à la version active publiée du formulaire :

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  La structure de l’URL reste la même pour les versions intermédiaires et actives. Cependant, le contenu affiché diffère en fonction du contexte.

Les captures d’écran ci-dessous comparent les URL de formulaires intermédiaires et dynamiques et les aperçus visuels pour les formulaires créés à l’aide de modèles basés sur Edge Delivery Services et sur les composants principaux :

>[!BEGINTABS]
>[!TAB Accès aux formulaires créés à l’aide d’un modèle Edge Delivery Services]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
    <thead>
    <tr>
      <th style="width: 20%;"><strong>Version</strong></th>
      <th style="width: 80%;"><strong>Image</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <td>Version intermédiaire</td>
      <td><img src="/help/forms/assets/registration-form-staged-version.png" alt="Version intermédiaire du formulaire d’enregistrement" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Version en direct</td>
      <td><img src="/help/forms/assets/registration-form-live-version.png" alt="Version active du formulaire d’enregistrement" style="width: 100%; height: auto;" /></td>
    </tr>
    </tbody>
  </table>

>[!TAB Accès aux formulaires créés à l’aide d’un modèle basé sur les composants principaux]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr>
      <th style="width: 20%;"><strong>Version</strong></th>
      <th style="width: 80%;"><strong>Image</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Version intermédiaire</td>
      <td><img src="/help/forms/assets/enrollment-form-staged-version.png" alt="Version intermédiaire du formulaire d’inscription" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Version en direct</td>
      <td><img src="/help/forms/assets/enrollment-form-live-version.png" alt="Version active du formulaire d’inscription" style="width: 100%; height: auto;" /></td>
    </tr>
  </tbody>
  </table>

>[!ENDTABS]

## Résolution des problèmes

Vous rencontrez des problèmes pour charger votre formulaire ? Voici quelques problèmes courants et comment les résoudre :

* **URL du formulaire** : vérifiez à nouveau que l’URL de votre formulaire n’inclut pas l’extension « .html » à la fin. Edge Delivery Services ne nécessite pas cette extension.

* **URL de création AEM** : vérifiez que l’URL de création AEM répertoriée dans votre fichier `fstab.yaml` est correctement formatée. Elle doit inclure les détails suivants :

   * Propriétaire GitHub
   * Nom de référentiel
   * Branche spécifique utilisée pour Edge Delivery Services

## Commencer à créer des formulaires

{{universal-editor-see-also}}

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.

### Managing a form

You can perform several operations on form using the AEM Forms user interface.

1. Login into your AEM Forms as a Cloud Service author instance.
1. Select **[!UICONTROL Adobe Experience Manager]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Forms & Documents]**.

1. Select a form and the toolbar displays the following operations you can perform on the selected form.

<table>
 <tbody>
  <tr>
   <td><p><strong>Operation</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Edit</p> </td>
   <td><p>Opens the form in edit mode.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Properties</p> </td>
   <td><p>Provides options to modify the properties of the form.<br /> <br /> </p> </td>
  </tr>
  <td><p>Copy</p> </td>
   <td><p> Provides options to copy the form  and paste it at the desired location. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Preview</p> </td>
   <td><p>Provides options to preview the form as HTML or perform a custom preview by merging data from an XML file with the form. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Downloads the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Start Review/Manage Review</p> </td>
   <td><p>Allows initiating and managing a review of the selected form.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publish / Unpublish</p> </td>
   <td><p>Publishes / unpublishes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Delete</p> </td>
   <td><p>Deletes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Compare</p> </td>
   <td><p>Compares two different form for previewing purposes.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table> 


## How Edge Delivery Services Forms Work?

Users can author Edge Delivery Services Forms using document-based authoring tools such as Google Drive, SharePoint, or the Universal Editor (WYSIWYG authoring), while leveraging the basic styling, behaviour and components available in the GitHub repository. Once authored, Edge Delivery Services Forms can send data to any platform using the Forms Submission Service.

![How Edge Delivery Services Forms works](/help/edge/docs/forms/assets/eds-forms-working.png)

### Key components of Edge Delivery Services Forms

The key components of Edge Delivery Servies Forms are:

* **GitHub Repository**: The GitHub repository serves as a boilerplate for creating Edge Delivery Services Forms. The forms leverage basic styling and functionality from the repository and allow users to add customizations and custom components to the Edge Delivery Services Forms.

* **Form Authoring**: Edge Delivery Services Forms support two types of authoring: WYSIWYG and document-based authoring. Document-based authoring enables users to create forms using familiar tools like Google Docs and Microsoft Office. WYSIWYG authoring allows users to design forms visually using the Universal Editor, making it easy for non-technical users to create and manage forms. Universal Editor offers an intuitive form creation experience and provides access to numerous form capabilities.

* **Forms Submission Service**: The Forms Submission Service allows you to store data from forms submissions on any platform, such as OneDrive, SharePoint, or Google Sheets, making it easy to access and manage form data within your preferred system.-->
