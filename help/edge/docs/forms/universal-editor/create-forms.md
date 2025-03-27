---
title: Comment créer des formulaires autonomes basés sur un modèle Edge Delivery Services à l’aide de l’éditeur universel ?
description: Cet article explique comment utiliser l’éditeur universel pour créer des formulaires en sélectionnant un modèle basé sur Edge Delivery Services dans l’assistant de création de formulaires. Vous pouvez également publier les formulaires dans AEM Edge Delivery Services.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: c81698c2d424d39688d1c9fad6c085223f5854a5
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 67%

---

# Guide détaillé sur la création de formulaires autonomes dans l’éditeur universel

<span class="preview"> Cette fonctionnalité est disponible par le biais du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail avec le nom de votre organisation et le nom de votre référentiel GitHub à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

Cet article vous guide tout au long du processus de création de formulaires autonomes à l’aide de l’éditeur universel en sélectionnant un modèle basé sur Edge Delivery Services dans l’assistant de création de formulaire. Vous pouvez également publier les formulaires créés avec l’éditeur universel dans AEM Edge Delivery Services.

AEM Forms fournit un bloc, appelé bloc de formulaires adaptatifs, qui vous permet de créer facilement des formulaires Edge Delivery Services pour capturer et stocker les données. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc de formulaires adaptatifs à un projet AEM existant](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project).

![Workflow du référentiel Github](/help/edge/assets/repo-workflow.png){width=50%}

## Conditions préalables

* [Configurez votre référentiel GitHub](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) pour établir une connexion entre votre environnement AEM et le référentiel GitHub.
* Si vous utilisez déjà des Edge Delivery Services, ajoutez la dernière version du [bloc de formulaires adaptatifs](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) à votre référentiel GitHub.
* L’instance de création AEM Forms comprend un modèle basé sur des Edge Delivery Services. Assurez-vous que la [dernière version des composants principaux](https://github.com/adobe/aem-core-forms-components) est installée dans votre environnement.
* Conservez à portée de main l’URL de votre instance de création AEM Forms as a Cloud Service et de votre référentiel GitHub.

## Utilisation des formulaires dans l’éditeur universel

L’éditeur universel vous permet de créer facilement des formulaires réactifs et interactifs autonomes à l’aide de composants préconfigurés tels que des champs de texte, des cases à cocher et des boutons radio. Il offre des fonctionnalités puissantes telles que des règles dynamiques, une intégration de données fluide et des options de personnalisation, ce qui vous permet de créer des formulaires en fonction de vos besoins exacts. Vous pouvez également publier les formulaires dans AEM Edge Delivery Services. Vous pouvez effectuer les actions suivantes sur les formulaires dans l’éditeur universel :
* [Créer un formulaire](#create-a-form)
* [Créer un formulaire](#author-a-form)
* [Publication d’un formulaire](#publish-a-form)
* [Gestion d’un formulaire](#manage-a-form)

>[!NOTE]
>
> Vous pouvez également [créer un formulaire dans AEM Sites à l’aide du modèle de site Edge Delivery Services dans l’éditeur universel et le publier dans Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project).


### Créer un formulaire

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**. Cette action permet d’ouvrir l’assistant.
1. Dans l’onglet **Source**, sélectionnez un modèle de formulaire basé sur Edge Delivery Services :

   ![Créer des formulaires EDS](/help/edge/assets/create-eds-forms.png)


   Lorsque vous sélectionnez un modèle basé sur Edge Delivery Services, le bouton **[!UICONTROL Créer]** est activé.
1. (Facultatif) Dans les onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]**, vous pouvez sélectionner une source de données ou une action d’envoi.
1. (Facultatif) Dans l’onglet **[!UICONTROL Diffusion]**, vous pouvez spécifier une date de publication ou de dépublication pour un formulaire.

1. Cliquez sur **[!UICONTROL Créer]**. L’assistant **Créer un formulaire** s’affiche.
1. Spécifiez les **Nom** et **Titre**.
1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est la suivante :
   `https://github.com/wkndforms/edsforms`
1. Cliquez sur **[!UICONTROL Créer]**.

   ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png)

   Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

   ![créer le formulaire](/help/edge/assets/author-form.png)

   <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

   Lorsque vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

### Créer un formulaire

1. Ouvrez l’explorateur de contenu et accédez au composant **[!UICONTROL Formulaire adaptatif]** dans l’**arborescence de contenu**.

   ![arborescence de contenu](/help/edge/assets/content-tree.png)

1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

   ![ajouter un composant](/help/edge/assets/add-component.png)

1. Sélectionnez le composant Formulaire adaptatif ajouté et mettez à jour ses propriétés à l’aide des **[!UICONTROL Propriétés]**.

   ![ouvrir les propriétés](/help/edge/assets/component-properties.png)

   La copie d’écran ci-dessous affiche le simple formulaire `Registration Form` créé dans l’éditeur universel :

   ![Formulaire de contact](/help/edge/assets/contact-us.png)

   Vous pouvez maintenant [configurer et personnaliser des actions d’envoi de formulaire](/help/edge/docs/forms/universal-editor/submit-action.md).


<!--
## **Edge Delivery Services configuration of form**



   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Edge Delivery Services Configuration]** on your AEM Forms as a Cloud Service author instance.

        ![Select Edge Delivery Services Configuration](/help/edge/assets/select-eds-conf.png)
   1. Select the folder that matches the form's name. For example, if your form is called 'registration-form' choose the folder `forms/registration-form` and selct the configuration and publish the configuration:

        ![Edge Delivery Services Configuration](/help/edge/assets/aem-instance-eds-configuration.png)

   1. Click **[!UICONTROL Properties]** to see the configuration.   
        ![Automatically created configuration](/help/edge/assets/aem-forms-create-configuration-github.png)

        You can leave the Edge Host option as it is. The form would be published to both preview (.page) and live (.live) environments. 

   1. Click **[!UICONTROL Save and Close]**. The configuration is saved. -->

### Publication d’un formulaire

Publiez maintenant le formulaire autonome dans Edge Delivery Services en cliquant sur le bouton **[!UICONTROL Publier]** dans le coin supérieur droit de l’éditeur universel.

![publier le formulaire](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Reportez-vous à l’article [Publier et déployer](/help/edge/docs/forms/universal-editor/publish-forms.md) pour savoir comment publier un formulaire dans Edge Delivery Services.

Voici comment accéder au formulaire dans Edge Delivery Services :

* **Version intermédiaire (pour les tests)** : la version intermédiaire affiche la version de travail dépubliée du formulaire à des fins de test. Utilisez le format d’URL suivant pour prévisualiser le formulaire avant sa mise en ligne :

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet est nommé « edsforms », qu’il se trouve dans le compte « wkndform » et que vous utilisez la branche « main » et le formulaire « Formulaire d’rengistrement », l’URL intermédiaire ressemble à celle-ci :
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **Version en direct (formulaire publié)** : la version active affiche la dernière version publiée du formulaire, accessible aux utilisateurs finaux. Utilisez le format d’URL suivant pour accéder à la version active publiée du formulaire :

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet est nommé « edsforms », qu’il se trouve dans le compte « wkndform » et que vous utilisez la branche « main » et le formulaire « Formulaire d’rengistrement », l’URL intermédiaire ressemble à celle-ci :
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

La structure de l’URL reste la même pour les versions intermédiaires et actives. Cependant, le contenu affiché diffère en fonction du contexte :

![Afficher le formulaire publié](/help/edge/assets/eds-view-publish-form.png)

### Gestion d’un formulaire

Vous pouvez effectuer plusieurs opérations sur le formulaire à l’aide de l’interface utilisateur d’AEM Forms.

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

1. Sélectionnez un formulaire et la barre d’outils affiche les opérations suivantes que vous pouvez effectuer sur le formulaire sélectionné.

<table>
 <tbody>
  <tr>
   <td><p><strong>Opération</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Modifier</p> </td>
   <td><p>Ouvre le formulaire en mode d'édition.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Propriétés</p> </td>
   <td><p>Fournit des options pour modifier les propriétés du formulaire.<br /> <br /> </p> </td>
  </tr>
  <td><p>Copier</p> </td>
   <td><p> Fournit des options pour copier le formulaire et le coller à l’emplacement souhaité. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Prévisualisation</p> </td>
   <td><p>Fournit des options pour prévisualiser le formulaire sous HTML ou effectuer un aperçu personnalisé en fusionnant les données d’un fichier XML avec le formulaire. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Téléchargement</p> </td>
   <td><p>Télécharge le formulaire sélectionné.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Démarrage de la révision/Gestion de la révision</p> </td>
   <td><p>Permet de lancer et de gérer la révision du formulaire sélectionné.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>-->
  <tr>
   <td><p>Publier/Dépublier</p> </td>
   <td><p>Publie/dépublie le formulaire sélectionné.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Supprimer</p> </td>
   <td><p>Supprime le formulaire sélectionné.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Comparer</p> </td>
   <td><p>Compare deux formulaires différents à des fins de prévisualisation.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Résolution des problèmes

Vous rencontrez des problèmes pour charger votre formulaire ? Voici quelques problèmes courants et comment les résoudre :

* **URL du formulaire** : vérifiez à nouveau que l’URL de votre formulaire n’inclut pas l’extension « .html » à la fin. Edge Delivery Services ne nécessite pas cette extension.

* **URL de création AEM** : vérifiez que l’URL de création AEM répertoriée dans votre fichier `fstab.yaml` est correctement formatée. Elle doit inclure les détails suivants :

   * Propriétaire GitHub
   * Nom de référentiel
   * Branche spécifique utilisée pour Edge Delivery Services

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Commencer à créer des formulaires

{{universal-editor-see-also}}
