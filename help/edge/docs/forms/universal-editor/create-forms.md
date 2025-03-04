---
title: Comment créer un Forms adaptatif autonome à l’aide de l’éditeur universel ?
description: Cet article explique comment créer un Forms adaptatif à l’aide de l’assistant de création de formulaire dans l’instance d’auteur AEM et publier des formulaires dans AEM Edge Delivery Services.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
source-git-commit: d7e59c16e90e3632140eae08dc2c25b2dd1df5a7
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 45%

---


# Créer des formulaires autonomes à l’aide de l’éditeur universel (WYSIWYG)

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

Cet article vous guide tout au long du processus de création de formulaires autonomes avec l’éditeur universel en sélectionnant un modèle basé sur Edge Delivery Services dans l’assistant de création de formulaire. Vous pouvez également publier les formulaires créés avec l’éditeur universel dans AEM Edge Delivery Services.

<!--To publish forms to Edge Delivery Services, you must first establish a connection between your AEM environment and your GitHub repository. Once connected, you can author the forms using the Universal Editor, which follows a WYSIWYG (What You See Is What You Get) approach for a seamless and consistent user experience with Sites.-->

Avant de commencer, découvrez les types de composants de formulaires disponibles :

* [Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) est un ensemble de services composables qui permet un environnement de développement rapide dans lequel les auteurs et autrices peuvent mettre à jour, publier et lancer rapidement de nouveaux formulaires à l’aide de l’éditeur universel. L’éditeur universel simplifie la création de formulaires pour les services de diffusion Adobe Edge grâce à une interface WYSIWYG visuelle et conviviale.

* [Composants principaux de formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) : il s’agit de composants de capture de données normalisés. Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique. Un développeur ou une développeuse peut facilement personnaliser et mettre en forme ces composants. Vous pouvez consulter [https://aemcomponents.dev/](https://aemcomponents.dev/) pour afficher les composants principaux disponibles en action **Adobe recommande d’utiliser ces composants modernes et extensibles pour développer un Forms adaptatif**.

* [Composants de base des formulaires adaptatifs](/help/forms/creating-adaptive-form.md) : il s’agit de composants de capture de données classiques (anciens). Vous pouvez continuer à les utiliser pour modifier votre formulaire adaptatif existant basé sur les composants de base. Si vous créez des formulaires, Adobe recommande d’utiliser [Composants principaux de Forms adaptatif](#create-an-adaptive-form-core-components) pour créer un Forms adaptatif.

AEM Forms fournit un bloc, appelé bloc de formulaires adaptatifs, qui vous permet de créer facilement des formulaires Edge Delivery Services pour capturer et stocker les données. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de Forms adaptatif](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc de Forms adaptatif à un projet de site AEM existant](#add-adaptive-forms-block-to-your-existing-aem-project).

![Workflow du référentiel Github](/help/edge/assets/repo-workflow.png)

## Conditions préalables

* [Configurez votre référentiel GitHub](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) pour établir une connexion entre votre environnement AEM et le référentiel GitHub.
* Si vous utilisez déjà des Edge Delivery Services, ajoutez la dernière version du [bloc de formulaires adaptatifs](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) à votre référentiel GitHub.
* L’instance de création AEM Forms comprend un modèle basé sur des Edge Delivery Services. Assurez-vous que la [dernière version des composants principaux](https://github.com/adobe/aem-core-forms-components) est installée dans votre environnement.
* Conservez à portée de main l’URL de votre instance de création AEM Forms as a Cloud Service et de votre référentiel GitHub.

## Créer un formulaire adaptatif à l’aide de l’éditeur universel

L’éditeur universel vous permet de créer facilement des formulaires autonomes réactifs et interactifs à l’aide de composants prêts à l’emploi tels que des champs de texte, des cases à cocher et des boutons radio. Il offre des fonctionnalités puissantes telles que des règles dynamiques, une intégration de données fluide et des options de personnalisation, ce qui vous permet de créer des formulaires en fonction de vos besoins exacts.

>[!NOTE]
>
> Vous pouvez également [créer un formulaire dans AEM Sites à l’aide du modèle de site Edge Delivery Services dans l’éditeur universel et le publier dans Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project).

Pour créer un formulaire adaptatif autonome à l’aide de l’éditeur universel, procédez comme suit :

1. **Création d’un formulaire adaptatif sur une instance d’auteur AEM Forms**

   1. Accédez à votre instance de création AEM Forms as a Cloud Service.
   1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et Documents]**.1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant.
   1. Dans l&#39;onglet **Source**, sélectionnez un modèle de formulaire basé sur Edge Delivery Services :

      ![Créer un Forms EDS](/help/edge/assets/create-eds-forms.png)

   1. Cliquez sur **[!UICONTROL Créer]**. L’assistant **Créer un formulaire** s’affiche.
   1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est :
      `https://github.com/wkndforms/edsforms`
   1. Cliquez sur **[!UICONTROL Créer]**.

      ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png)

      Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

      ![créer le formulaire](/help/edge/assets/author-form.png)

      <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

      Lorsque vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

1. **Créez le formulaire dans l’éditeur universel**

   1. Ouvrez l’explorateur de contenu et accédez au composant **[!UICONTROL Formulaire adaptatif]** dans l’**arborescence Contenu**.

      ![arborescence de contenu](/help/edge/assets/content-tree.png)

   1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

      ![ajouter un composant](/help/edge/assets/add-component.png)

   1. Sélectionnez le composant Formulaire adaptatif ajouté et mettez à jour ses propriétés à l’aide des **[!UICONTROL Propriétés]**.

      ![ouvrir les propriétés](/help/edge/assets/component-properties.png)

      La capture d’écran ci-dessous affiche le formulaire `Registration Form` simple créé dans l’éditeur universel :

      ![formulaire de contact](/help/edge/assets/contact-us.png)

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

## Publication du formulaire

Publiez maintenant le formulaire autonome dans Edge Delivery Services en cliquant sur le bouton **[!UICONTROL Publier]** dans le coin supérieur droit de l’éditeur universel.

![publier le formulaire](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Reportez-vous à l’article [Publier et déployer](/help/edge/docs/forms/universal-editor/publish-forms.md) pour savoir comment publier un formulaire dans Edge Delivery Services.

Voici comment accéder au formulaire dans Edge Delivery Services :

* **Version intermédiaire (pour les tests)** : la version intermédiaire affiche la version de travail dépubliée du formulaire à des fins de test. Utilisez le format d’URL suivant pour prévisualiser le formulaire avant sa mise en ligne :

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet s’appelle « esforms », qu’il se trouve sous le compte « windowforms » et que vous utilisez la branche « principale » et le formulaire comme « Formulaire d’enregistrement », l’URL de la version intermédiaire ressemble à ce qui suit :
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **Version en direct (formulaire publié)** : la version active affiche la dernière version publiée du formulaire, accessible aux utilisateurs finaux. Utilisez le format d’URL suivant pour accéder à la version active publiée du formulaire :

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet s’appelle « esforms », qu’il se trouve sous le compte « windowforms » et que vous utilisez la branche « principale » et le formulaire comme « Formulaire d’enregistrement », l’URL de la version intermédiaire ressemble à ce qui suit :
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

La structure de l’URL reste la même pour les versions intermédiaires et actives. Cependant, le contenu affiché diffère en fonction du contexte :

![Afficher le formulaire publié](/help/edge/assets/eds-view-publish-form.png)

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


