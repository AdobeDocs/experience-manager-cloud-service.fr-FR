---
title: Publication de Forms pour les Edge Delivery Services
description: Découvrez comment fonctionne la publication de formulaires avec des Edge Delivery Services et comment publier des formulaires AEM avec des Edge Delivery Services.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---


# Publication de Forms pour les Edge Delivery Services

Cet article vous guide tout au long du processus de publication de formulaires dans les Edge Delivery Services AEM.
Pour publier des formulaires dans des Edge Delivery Services, vous devez d’abord établir une connexion entre votre environnement AEM et votre référentiel GitHub. Une fois connecté, vous pouvez créer les formulaires à l’aide de l’éditeur universel, qui suit une approche WYSIWYG (What You See Is What You Get) pour une expérience utilisateur fluide et cohérente avec Sites.

## Prérequis

* Vous découvrez le Forms adaptatif ? Configurez votre référentiel GitHub en suivant le [tutoriel](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) fourni.
* Si vous utilisez déjà des Edge Delivery Services, ajoutez la dernière version du [bloc de Forms adaptatif](/help/edge/docs/forms/tutorial.md#) à votre référentiel GitHub.
* L’instance d’auteur AEM Forms comprend un modèle basé sur des Edge Delivery Services. Assurez-vous que la [dernière version des composants principaux](https://github.com/adobe/aem-core-forms-components) est installée dans votre environnement.
* Conservez à portée de main l’URL de votre instance d’auteur AEM Forms as a Cloud Service et de votre référentiel GitHub.

## Publish Forms pour les Edge Delivery Services

Pour publier des formulaires pour les Edge Delivery Services, procédez comme suit :

[1. Liaison du référentiel GitHub à l’instance AEM](#link-github-repository-to-aem-instance)

[2. Liaison de l’instance AEM au référentiel GitHub](#link-aem-instance-to-github-repository)

### Liaison du référentiel GitHub à une instance AEM

Pour lier [votre projet sur le référentiel GitHub](/help/edge/docs/forms/tutorial.md) à l’instance d’auteur AEM Forms, procédez comme suit :

1. Accédez au référentiel GitHub que vous avez créé ou configuré pour vos Edge Delivery Services.
1. Ouvrez le fichier `fstab.yaml` en mode d’édition.
1. Mettez à jour le fichier `fstab.yaml` dans votre référentiel GitHub avec l’URL de votre instance AEM Forms as a Cloud Service.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   Par exemple, si votre référentiel GitHub s’appelle « aemcrosswalk », il se trouve sous le compte « windform » et que vous utilisez la branche « main », l’URL de l’instance de création ressemble à ce qui suit :

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. Validez les modifications dans le fichier `fstab.yaml`.

### Liaison d’une instance AEM au référentiel GitHub

Pour lier l’instance d’auteur AEM Forms à [votre projet sur le référentiel GitHub](/help/edge/docs/forms/tutorial.md), procédez comme suit :

[1. Création d’un formulaire adaptatif basé sur le modèle Edge Delivery Services](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. Recherchez le conteneur de configuration de votre formulaire dans l’instance d’auteur AEM](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. Créez le formulaire dans l’éditeur universel](#3-author-the-form-in-the-universal-editor)

[4. Publish et prévisualisation du formulaire](#4-publish-and-preview-the-form)

#### 1. Création d’un formulaire adaptatif basé sur le modèle Edge Delivery Services

1. Accédez à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms Et Documents]**.1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms Adaptatif]**. Cette action permet d’ouvrir l’assistant. Dans l’onglet Source , sélectionnez un modèle de formulaire basé sur les Edge Delivery Services :

   ![Créer EDS Forms](/help/edge/assets/create-eds-forms.png){width=50%, align-center}

1. Cliquez sur **[!UICONTROL Créer]** et l’assistant **Créer un formulaire** s’affiche.
1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé « aemcrosswalk », il se trouve sous le compte « wknd form », et l’URL est la suivante :
   `https://github.com/wkndform/aemcrosswalk`
1. Cliquez sur **[!UICONTROL Créer]**.

   ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png){width=50%, align-center}

   Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue de sa création.

   ![créer le formulaire](/help/edge/assets/author-form.png){width=50%, align-center}

   >[!NOTE]
   >
   > La configuration des Edge Delivery Services pour les formulaires basés sur le modèle de Edge Delivery Services est créée automatiquement au niveau du conteneur de configuration du formulaire.

#### 2. Recherchez le conteneur de configuration de votre formulaire dans l’instance d’auteur AEM

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Configuration des Cloud Service]** > **[!UICONTROL Configuration des Edge Delivery Services]** sur votre instance AEM Forms as a Cloud Service author.
1. Sélectionnez le dossier correspondant au nom du formulaire. Par exemple, si votre formulaire s’appelle « contact-us », choisissez le dossier `forms/contact-us`, sélectionnez la configuration et publiez la configuration :

   ![Configuration des Edge Delivery Services ](/help/forms/assets/aem-instance-eds-configuration.png){width=50%, align-center}

1. Cliquez sur **[!UICONTROL Propriétés]** pour afficher la configuration.\
   ![Configuration créée automatiquement](/help/edge/assets/aem-forms-create-configuration-github.png){width=50%, align-center}

   Vous pouvez laisser l’option Hôte Edge telle quelle. Le formulaire serait publié dans les environnements de prévisualisation (.page) et de création (.live).

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration est enregistrée.

#### 3. Créez le formulaire dans l’éditeur universel

Lorsque vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue de sa création.

1. Ouvrez l’explorateur de contenu et accédez au composant **[!UICONTROL Formulaire adaptatif]** dans l’arborescence **Contenu**.

   ![arborescence de contenu](/help/edge/assets/content-tree.png){width=50%, align-center}

1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

   ![ajouter un composant](/help/edge/assets/add-component.png){width=50%, align-center}

1. Sélectionnez le composant de formulaire adaptatif ajouté et mettez à jour ses propriétés à l’aide de **[!UICONTROL Propriétés]**.

   ![ouvrir les propriétés](/help/edge/assets/component-properties.png){width=50%, align-center}

   La capture d’écran ci-dessous affiche le simple formulaire « Contactez-nous » créé dans l’éditeur universel :

   ![formulaire de contact](/help/edge/assets/contact-us.png){width=50%, align-center}

#### 4. Publish et prévisualisation du formulaire

Publiez maintenant le formulaire dans les Edge Delivery Services en cliquant sur le bouton **[!UICONTROL Publish]** dans le coin supérieur droit de l’éditeur universel.

![publier le formulaire](/help/edge/assets/publish-form.png){width=50%, align-center}


Voici comment accéder au formulaire dans les Edge Delivery Services :

* **Version intermédiaire (pour les tests)** : la version intermédiaire affiche la version de travail dépubliée du formulaire à des fins de test. Utilisez le format d’URL suivant pour prévisualiser le formulaire avant sa mise en ligne :

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet s’appelle « aemcrosswalk », il se trouve sous le compte « windform » et que vous utilisez la branche « principale » et le formulaire comme « contactez-nous », l’URL de la version intermédiaire ressemble à ce qui suit :
https://main--aemcrosswalk--wkndform.aem.page/content/forms/af/contact-us

* **Version en direct (formulaire publié)** :   La version active affiche la version la plus récemment publiée du formulaire, accessible aux utilisateurs finaux. Utilisez le format d’URL suivant pour accéder à la version active publiée du formulaire :

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Par exemple, si le référentiel de votre projet s’appelle « aemcrosswalk », il se trouve sous le compte « windform » et que vous utilisez la branche « principale » et le formulaire comme « contactez-nous », l’URL de la version intermédiaire ressemble à ce qui suit :
https://main--aemcrosswalk--wkndform.aem.live/content/forms/af/contact-us

La structure de l’URL reste la même pour les versions intermédiaires et actives. Cependant, le contenu affiché diffère en fonction du contexte :

![Afficher le formulaire publié](/help/edge/assets/eds-view-publish-form.png){width=50%, align-center}

## Résolution des problèmes

Vous rencontrez des problèmes pour charger votre formulaire ? Voici quelques problèmes courants et comment les résoudre :

* **URL du formulaire** : vérifiez à nouveau que l’URL de votre formulaire n’inclut pas l’extension « .html » à la fin. Le service de diffusion Edge ne nécessite pas cette extension.

* **URL de création AEM** L : vérifiez que l’URL de création AEM répertoriée dans votre fichier `fstab.yaml` est correctement formatée. Il doit inclure les détails suivants :

   * Propriétaire GitHub correct
   * Nom de référentiel correct
   * Branche spécifique utilisée pour les Edge Delivery Services

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Voir également

{{see-more-forms-eds}}