---
title: Ajout d’un formulaire adaptatif (composants principaux) dans la page AEM Sites
seo-title: How to add an Adaptive Form (Core Components) to an AEM Sites page?
description: Vous pouvez utiliser le formulaire adaptatif (composants principaux) dans une page AEM Sites pour remplir et envoyer un formulaire sans quitter les pages AEM Sites.
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 1046231f-787c-4e49-9ba0-e7dd59e41bce
source-git-commit: 0d21b4ba2e7ce7592e3f2c57e4d320adc0af1008
workflow-type: tm+mt
source-wordcount: '2207'
ht-degree: 19%

---

# Ajout d’un Forms adaptatif à une page AEM Sites {#add-an-adaptive-form-to-aem-sites-page}

## Présentation {#overview}

Vous pouvez facilement créer ou incorporer un Forms adaptatif dans une page AEM Sites pour permettre à vos utilisateurs de remplir et d’envoyer un formulaire sans quitter la page Sites. Il permet à l’utilisateur de rester dans le contexte d’autres éléments de la page web et d’interagir simultanément avec le formulaire.

Vous pouvez choisir l’une des méthodes suivantes pour créer ou incorporer un formulaire adaptatif dans une page AEM Sites :

* **Créez un formulaire adaptatif en faisant glisser les composants de formulaire vers le composant de conteneur de Forms adaptatif**: Utilisez la variable [Conteneur Forms adaptatif](#af-container-component) pour créer un espace dans votre page web qui hébergerait le formulaire adaptatif. Vous pouvez faire glisser et déposer le composant Formulaire adaptatif dans cet espace pour créer un formulaire. Par exemple, visionnez la vidéo ci-dessous pour savoir comment créer un formulaire adaptatif à l’aide de [!UICONTROL Conteneur Forms adaptatif] component :

Le [Conteneur de formulaires adaptatifs](#af-container-component) vous permet de créer des expériences d’inscription numérique en utilisant des composants Forms adaptatifs directement dans l’éditeur AEM Sites. Cette intégration offre une expérience transparente aux auteurs AEM Sites qui souhaitent créer et gérer des formulaires dans leurs pages AEM Sites.

* **Incorporation d’un formulaire adaptatif existant**: Le [Forms adaptatif - Incorporer (V2)](#embed-existing-af) vous permet d’incorporer facilement un formulaire adaptatif préexistant dans une page dans AEM Sites. Par exemple, incorporez un formulaire adaptatif à l’aide de la fonction [!UICONTROL Forms adaptatif - Incorporer] dans la page du site, comme illustré dans la vidéo suivante :

Cette fonctionnalité améliore l’adaptabilité et la réutilisation d’Adaptive Forms. Cette intégration permet aux clients de réutiliser le Forms adaptatif qu’ils ont déjà créé.

* **Utilisation de l’assistant de Forms adaptatif pour créer un formulaire**:

   Utilisez la variable [Forms adaptatif - Incorporer (v2)](#embed-new-af) pour créer un formulaire adaptatif à partir de l’éditeur AEM Sites à l’aide de l’assistant de création de formulaire. Le formulaire est enregistré en tant qu’entité externe. Vous pouvez également réutiliser ce formulaire dans d’autres pages Sites et dans des formulaires autonomes.
Par exemple, visionnez la vidéo ci-dessous pour savoir comment créer et incorporer un formulaire adaptatif nouvellement créé à l’aide de la fonction [!UICONTROL Forms adaptatif - Incorporer] dans la page du site.

### Considération {#considerations}

Vous pouvez utiliser l’éditeur de règles pour ajouter ou contrôler le comportement dynamique des composants de formulaire adaptatif. Par exemple, masquez ou affichez un composant. L’éditeur de règles n’est pas disponible pour les composants de formulaire non adaptatif. Par conséquent, faites preuve de diligence lors de l’utilisation de composants de formulaire non adaptatif dans le composant de conteneur AEM Forms.

## Création d’un formulaire adaptatif à l’aide du composant de conteneur de Forms adaptatif {#af-container-component}

Le [!UICONTROL Conteneur de formulaires adaptatifs] permet de créer des expériences d’inscription numérique à l’aide des composants Forms adaptatif dans l’éditeur AEM Sites. Vous pouvez créer un formulaire adaptatif en faisant glisser les composants de formulaire.

### Prérequis {#prerequisites-af-container}

+++ Activer **[!UICONTROL Conteneur Forms adaptatif]** dans la stratégie du modèle associé.

Pour activer [!UICONTROL Conteneur Forms adaptatif] dans la stratégie du modèle, procédez comme suit :

1. Accédez au [!UICONTROL Informations sur la page] > [!UICONTROL Modifier le modèle]
1. Cliquez sur le bouton [!UICONTROL Stratégie] et sélectionnez la variable **[!UICONTROL Conteneur Forms adaptatif]**  sous la case **[Nom du projet AEM Archetype] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Inclure les clientlibs sur la page du site

Pour utiliser les composants Forms adaptatifs dans une page AEM Sites, incluez les bibliothèques clientes Customheaderlibs et Customfooterlibs dans la page AEM Sites à l’aide du référentiel d’AEM et du pipeline de déploiement.

1. Ouvrez votre [Archétype AEM Forms ou référentiel Git cloné](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) dans un éditeur de texte. Par exemple, Visual Studio Code.
1. Accédez à `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Copiez la valeur de `sling:resourceSuperType`. Par exemple, la valeur est `core/wcm/components/page/v3/page`.

   ![ressource sling](/help/forms/assets/slingresource.png)

1. Créer la structure similaire à l’emplacement `ui.apps/src/main/content/jcr_root/apps` identique à `core/wcm/components/page/v3/page`.

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png)

1. Ajouter `customheaderlibs.html` et `customfooterlibs.html` fichiers .

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly> 
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly> 
   ```

   Le fichier customfooterlibs.html est utilisé pour JavaScript et le fichier customheaderlibs.html pour le CSS.

1. [Exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) pour déployer les modifications.

+++

### Création d’un formulaire adaptatif à l’aide du composant de conteneur de Forms adaptatif {#create-af-using-af-container}


Pour créer un formulaire adaptatif à l’aide de [!UICONTROL Conteneur Forms adaptatif] component :

1. Ouvrez la page AEM Sites en mode d’édition.
1. Dans le panneau Explorateur de composants, faites glisser et déposez le **[!UICONTROL Conteneur Forms adaptatif]** sur la page.
1. Créez un formulaire adaptatif à l’aide des composants de Forms adaptatif.
1. Enregistrez les paramètres.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Votre formulaire est prêt. Lorsque vous publiez la page AEM Sites, elle publie automatiquement un formulaire adaptatif et les ressources référencées qui lui sont associées.

#### Configuration des propriétés du conteneur de formulaires adaptatifs {#configure-additional-settings-container}

Vous pouvez personnaliser les paramètres avancés de la variable [!UICONTROL Conteneur de formulaires adaptatifs] composant. Par exemple, vous pouvez configurer le service de préremplissage pour charger un formulaire adaptatif avec des valeurs préremplies sur la page d’un site. Vous configurez les paramètres du modèle de données pour associer le formulaire adaptatif à un modèle de données. Si vous souhaitez enregistrer les données sur OneDrive ou SharePoint lors de l’envoi d’un formulaire adaptatif, configurez les paramètres de l’action d’envoi. Vous pouvez également ajouter une action Envoyer personnalisée pour votre Forms adaptatif.

Pour définir les propriétés de la variable **[!UICONTROL Conteneur Forms adaptatif]** , cliquez sur le composant ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) dans la barre d’actions. Le **[!UICONTROL Modifier le conteneur Forms adaptatif]** s’ouvre.

![Boîte de dialogue de modification](/help/forms/assets/adaptiveformcontainer-editdialog.png)

Dans le [!UICONTROL Modifier le conteneur Forms adaptatif] , vous pouvez spécifier ce qui suit.
* **Onglet De base**
   * **Service de préremplissage**: Vous pouvez utiliser le service de préremplissage pour remplir automatiquement les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ouvre un formulaire, les valeurs de ces champs sont préremplies. Pour plus d’informations sur le service de préremplissage, voir [Préremplir les champs de formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)
   * **Catégorie de bibliothèque cliente**: Spécifiez la variable [Fonctions JavaScript](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions) qui sont utilisés dans les expressions et pris en charge par Adaptive Forms.
* **Modèle de données**: Un modèle de données vous permet d’intégrer des entités et des services provenant de sources de données disparates à un formulaire adaptatif. Choisir **[!UICONTROL Modèle de données de formulaire]** si le formulaire adaptatif que vous créez implique la récupération et l’écriture de données à partir de et vers plusieurs sources de données.
   * **Modèle de données de formulaire**: Un modèle de données de formulaire permet à un formulaire adaptatif de communiquer avec des sources de données disparates. Pour plus d’informations sur la configuration d’une source de données, voir [Configurez les sources de données.](/help/forms/configure-data-sources.md)
   * **Schéma**: Le schéma représente la structure dans laquelle les données sont générées ou utilisées par le système principal de votre entreprise. Vous pouvez [associer le schéma à un formulaire adaptatif ;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html) et utiliser ses éléments pour ajouter du contenu dynamique à un formulaire adaptatif.

      >[!NOTE]
      >
      > Après avoir configuré le modèle de données de formulaire, vous ne pouvez pas modifier le modèle de formulaire associé. Il est toutefois possible de modifier le schéma associé au modèle de données de formulaire.

* **Onglet Envoi**

   * **Rediriger vers l’URL**

      **URL/chemin de redirection**: Indique l’URL ou le chemin vers lequel un formulaire adaptatif est redirigé après l’action d’envoi.

      **Action Envoyer**: Une action d’envoi est déclenchée lorsqu’un utilisateur clique sur le bouton Envoyer d’un formulaire adaptatif. Vous pouvez [configurer l’action d’envoi sur le formulaire adaptatif](/help/forms/configuring-submit-actions.md). Les formulaires adaptatifs fournissent quelques actions d’envoi prêtes à l’emploi :
      * Envoyer vers le point d’entrée REST
      * Envoyer un e-mail
      * Envoyer à l’aide du modèle de données de formulaire
      * Appeler un processus AEM
      * Envoyer à SharePoint
      * Envoyer à OneDrive
      * Envoyer au stockage Blob Azure

   Vous pouvez également [étendre les actions d’envoi par défaut ;](custom-submit-action-form.md) pour créer votre propre action Envoyer personnalisée.

* **Afficher le message**
   * **Contenu du message**: Rédigez un message à l’aide de l’éditeur de texte enrichi à afficher lors de l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.

## Incorporation d’un formulaire adaptatif  {#aem-container-component}

Utilisation **[!UICONTROL Forms adaptatif - Incorporer (V2)]** vous pouvez incorporer un nouveau formulaire adaptatif ou un formulaire adaptatif existant dans la page du site. Le [!UICONTROL Forms adaptatif - Incorporer] vous permet d’effectuer les opérations suivantes :

* [Incorporation d’un formulaire adaptatif existant](#embed-new-af)

* [Création et incorporation d’un nouveau formulaire adaptatif](#embed-existing-af)

### Prérequis {#prerequisites}

+++ Activez la variable **Forms adaptatif - Incorporer** dans la stratégie du modèle associé.

Pour activer [!UICONTROL Forms adaptatif - Incorporer (v2)] dans la stratégie du modèle, procédez comme suit :

1. Accédez au [!UICONTROL Informations sur la page] > [!UICONTROL Modifier le modèle]

1. Cliquez sur le bouton [!UICONTROL Stratégie] et sélectionnez la variable **[!UICONTROL Formulaire adaptatif - Incorporer (v2)]** sous la case **[!UICONTROL [Nom du projet AEM Archetype] - Forms]** groupe .
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Inclure les clientlibs sur la page du site

Lorsque la variable **[!UICONTROL Lorsque le formulaire couvre toute la largeur d’une page]** est sélectionnée dans la variable **[!UICONTROL Conteneurs de formulaires]** configurer la boîte de dialogue et **Forms adaptatif à l’aide des composants principaux** sont utilisées ; il est nécessaire d’inclure les bibliothèques client sur la page de votre site correspondant.

![Gif de recouvrement](/help/forms/assets/overlaycorecomponent.gif)

Pour utiliser les composants Forms adaptatifs dans une page AEM Sites, incluez les bibliothèques clientes Customheaderlibs et Customfooterlibs dans la page AEM Sites à l’aide du référentiel d’AEM et du pipeline de déploiement.

1. Ouvrez votre [Archétype AEM Forms ou référentiel Git cloné](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) dans un éditeur de texte. Par exemple, Visual Studio Code.
1. Accédez à `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Copiez la valeur de `sling:resourceSuperType`. Par exemple, la valeur est `core/wcm/components/page/v3/page`.

   ![ressource sling](/help/forms/assets/slingresource.png)

1. Créer la structure similaire à l’emplacement `ui.apps/src/main/content/jcr_root/apps` identique à `core/wcm/components/page/v3/page`.

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png)

1. Ajouter `customheaderlibs.html` et `customfooterlibs.html` fichiers .

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
       data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
       <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly>
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
     data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
     <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly>
   ```

   Le fichier customfooterlibs.html est utilisé pour JavaScript et le fichier customheaderlibs.html pour le fichier CSS.

1. [Exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) pour déployer les modifications.

+++

### Incorporer un nouveau formulaire adaptatif {#embed-new-af}

1. Ouvrez la page AEM Sites en mode d’édition.
1. Dans le panneau Explorateur de composants, faites glisser et déposez le [!UICONTROL Forms adaptatif - Incorporer (v2)] sur la page.
1. Cliquez sur le bouton **Plus** et vous êtes redirigé vers l’assistant de création de formulaire.

   ![Forms adaptatif - Composant Incorporer](/help/forms/assets/aemformcontainer.png)

1. Créez un formulaire adaptatif à partir du [!UICONTROL Création de formulaire] assistant.
1. Le [!UICONTROL Chemin de la ressource] inclut déjà le chemin d’un formulaire adaptatif créé.
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

### Incorporer un formulaire adaptatif existant {#embed-existing-af}

1. Ouvrez la page AEM Sites en mode d’édition.
1. Dans le panneau Explorateur de composants, faites glisser et déposez le [!UICONTROL Forms adaptatif - Incorporer] sur la page.
1. Appuyez sur le bouton [!UICONTROL Forms adaptatif - Incorporer] dans la page sites, puis appuyez sur ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) dans la barre d’actions. Le **[!UICONTROL Modifier le Forms adaptatif - Incorporer]** s’ouvre.
1. Recherchez et sélectionnez le formulaire adaptatif à incorporer dans le [!UICONTROL Chemin de la ressource].
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

#### Configurer les propriétés du formulaire adaptatif _ Incorporer

Vous pouvez personnaliser les paramètres avancés de la variable [!UICONTROL Formulaire adaptatif - Incorporer (v2)] composant. Dans le [!UICONTROL Modifier le Forms adaptatif - Incorporer (v2)] , vous pouvez spécifier ce qui suit.

* **Chemin d’accès à la ressource** : cherchez et sélectionnez le formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
* **Publier l’envoi** : sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.
   * **Afficher le message de remerciement**: Rédigez un message à l’aide de l’éditeur de texte enrichi à afficher lors de l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
   * **Afficher la page de remerciement**: Recherchez et sélectionnez la page à afficher lors de l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Rediriger vers la page de remerciement** : activez cette option pour remplacer la page contenant le formulaire adaptatif incorporé par la page de remerciement. Sinon, la page de remerciement remplace le formulaire adaptatif dans la [!UICONTROL Forms adaptatif - Incorporer] sans actualiser les sites sous-jacents de la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
* **Utiliser la langue de la page** : utilisez les paramètres régionaux de la page AEM Sites au lieu de ceux du formulaire adaptatif.
* **Définir le focus sur le formulaire** : sélectionnez cette option pour définir le focus sur le premier champ du formulaire adaptatif.
* **Le formulaire couvre toute la largeur du cadre.**: Si cette case est cochée, iframe n’est pas utilisé pour générer le formulaire.
* **Hauteur**: Indiquez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
* **Bibliothèque cliente CSS**: Spécifiez le chemin d’accès à une bibliothèque cliente CSS.

### Publier le formulaire adaptatif incorporé {#publishing-embedded-adaptive-form}

Examinons les scénarios suivants concernant la publication d’un formulaire adaptatif incorporé dans une page AEM Sites :

* Si vous publiez la page AEM Sites pour la première fois et qu’elle comporte un formulaire adaptatif incorporé, publiez la page de Sites et la ressource incorporée.
* Si vous n’avez modifié que le formulaire incorporé à une page de site publiée, publiez le formulaire d’origine et les modifications seront répercutées sur la page de site publiée. La page de site publiée comprend une référence à la ressource et ne doit pas être republiée.
* Si vous avez modifié la page de site et le formulaire adaptatif ou la communication interactive incorporé, republiez la page de site et la ressource incorporée.

### Modification d’un formulaire adaptatif incorporé  {#modifying-embedded-adaptive-form}

Pour modifier une configuration ou une propriété du formulaire adaptatif incorporé, procédez de l’une des manières suivantes.

* Ouvrez le formulaire d’origine dans un formulaire adaptatif dans l’éditeur correspondant et modifiez-le.
* Appuyez sur le formulaire adaptatif à partir de la page du site en mode d’édition, puis appuyez sur **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

>[!NOTE]
>
>Les modifications apportées au formulaire d’origine sont répercutées automatiquement dans le formulaire incorporé. Cependant, republiez le formulaire adaptatif, ou la page du site, pour refléter les modifications apportées à la page publiée.

### Bonnes pratiques {#best-practices}

* L’en-tête et le pied de page du formulaire d’origine ne sont pas inclus dans le formulaire incorporé.
* Les brouillons et les envois des formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Forms envoyés du portail Forms.

[Dans la page AEM Sites, le mode Mise en page](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode) permet de redimensionner un formulaire adaptatif qui a été créé ou incorporé dans une page d’un site AEM.

![AF-layout-support](/help/forms/assets/afsite-layoutsupport.gif)

AEM page de sites conserve une référence au formulaire adaptatif. Lorsque vous traduisez une page AEM Sites, elle traduit automatiquement un formulaire adaptatif et les ressources référencées qui lui sont associées à l’aide de la fonction [projets de traduction](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job) dans d’autres langues.
