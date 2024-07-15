---
title: Comment ajouter ou créer une page Composants principaux de formulaire adaptatif dans AEM Sites ?
description: Utilisez les composants principaux de formulaire adaptatif dans une page AEM Sites pour remplir et envoyer un formulaire sans quitter les pages AEM Sites.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 89%

---

# Créer et ajouter un formulaire adaptatif à l’aide de l’Éditeur AEM Sites {#add-an-adaptive-form-to-aem-sites-page}

Vous pouvez facilement créer ou incorporer des formulaires adaptatifs dans une page AEM Sites pour permettre à vos utilisateurs et utilisatrices de remplir et d’envoyer un formulaire sans quitter la page Sites. Ils ou elles peuvent ainsi rester dans le contexte des autres éléments de la page web et interagir simultanément avec le formulaire.

Vous pouvez choisir l’une des méthodes suivantes pour créer ou ajouter un formulaire adaptatif à une page AEM Sites :

* **Créer un formulaire adaptatif à l’aide du composant Adaptive Forms Container** : le composant [Conteneur de formulaires adaptatifs](#af-container-component) permet de créer des expériences d’inscription numérique en utilisant les composants Adaptive Forms directement dans l’éditeur AEM Sites. Cette intégration offre une expérience transparente aux auteurs et autrices AEM Sites qui souhaitent créer et gérer des formulaires dans leurs pages AEM Sites.

* **Ajouter un formulaire adaptatif existant** : le composant [ Adaptive Forms - Embed(v2)](#embed-existing-af) permet d’ajouter facilement un formulaire adaptatif préexistant dans une page dans AEM Sites. Cette fonctionnalité améliore l’adaptabilité et la possibilité de réutilisation des formulaires adaptatifs. Cette intégration permet aux clientes et clients de réutiliser les formulaires adaptatifs déjà créés.

* **Utiliser l’assistant de formulaires adaptatifs pour créer un formulaire** : le composant [Formulaires adaptatifs - Incorporer (v2)](#embed-new-af) permet de créer un formulaire adaptatif à partir de l’éditeur AEM Sites à l’aide de l’assistant de création de formulaire. Le formulaire est enregistré en tant qu’entité externe. Vous pouvez également réutiliser ce formulaire dans d’autres pages Sites et dans des formulaires autonomes.

* **Ajouter plusieurs formulaires adaptatifs dans une page AEM Sites** : pour ajouter plusieurs formulaires adaptatifs dans une page AEM Sites, utilisez les composants Conteneur AEM Forms - [Formulaires adaptatifs - Incorporer (v2)](#embed-new-af) et [Conteneur de formulaires adaptatifs](#af-container-component). Si vous devez ajouter plusieurs formulaires adaptatifs en tant que balises div dans une page AEM Sites, vous pouvez utiliser le composant Conteneur de formulaires adaptatifs .

Vous pouvez utiliser l’Éditeur de règles pour ajouter ou contrôler le comportement dynamique des composants Formulaire adaptatif. Par exemple, masquez ou affichez un composant. L’Éditeur de règles n’est pas disponible pour les composants Formulaire non adaptatif. Par conséquent, faites preuve de diligence lors de l’utilisation de composants Formulaire non adaptatif dans le composant Conteneur AEM Forms.

## Créer un formulaire adaptatif à l’aide du composant Conteneur de formulaires adaptatifs {#af-container-component}

Le composant [!UICONTROL Conteneur de formulaires adaptatifs] permet de créer des expériences d’inscription numérique à l’aide des composants Formulaires adaptatifs dans l’éditeur AEM Sites. Vous pouvez créer un formulaire adaptatif en faisant glisser les composants du formulaire.

### Prérequis {#prerequisites-af-container}

+++ Activez le composant **[!UICONTROL Conteneur de formulaires adaptatifs]**.

Pour activer le composant [!UICONTROL Conteneur de formulaires adaptatifs] dans la politique du modèle, procédez comme suit :

1. Accédez à [!UICONTROL Informations sur la page] > [!UICONTROL Modifier le modèle].
1. Cliquez sur [!UICONTROL Politique] et cochez la case **[!UICONTROL Conteneur de formulaires adaptatifs]** sous **[Nom du projet Archetype AEM] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Inclure les bibliothèques clientes de formulaires adaptatifs à une page AEM Sites

Pour utiliser les composants Formulaires adaptatifs dans une page AEM Sites, incluez les bibliothèques clientes Customheaderlibs et Customfooterlibs dans la page AEM Sites à l’aide de l’Archetype AEM/du référentiel Git et du pipeline de déploiement.

1. Ouvrez votre projet [Archétype AEM Forms ou votre référentiel Git cloné](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) dans un éditeur de texte. Par exemple, Visual Studio Code.
1. Accédez à `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Copiez la valeur de `sling:resourceSuperType`. Par exemple, la valeur est `core/wcm/components/page/v3/page`.

   ![ressource sling](/help/forms/assets/slingresource.png)

1. Créez la structure similaire à l’emplacement `ui.apps/src/main/content/jcr_root/apps` identique à `core/wcm/components/page/v3/page`.

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png)

1. Ajoutez les fichiers `customheaderlibs.html` et `customfooterlibs.html`.

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

1. [Exécutez le pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=fr) pour déployer les modifications.

+++

### Créer un formulaire adaptatif à l’aide du composant Conteneur de formulaires adaptatifs {#create-af-using-af-container}


Pour créer un formulaire adaptatif à l’aide du composant [!UICONTROL Conteneur de formulaires adaptatifs] :

1. Ouvrez la page AEM Sites en mode d’édition.
1. Depuis le panneau Explorateur des composants, faites glisser et déposez le composant **[!UICONTROL Conteneur de formulaires adaptatifs]** sur la page.
1. Créez un formulaire adaptatif à l’aide des composants Formulaires adaptatifs.
1. Enregistrez les paramètres.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Votre formulaire est prêt. Lorsque vous publiez la page AEM Sites, elle publie automatiquement le formulaire adaptatif et les ressources référencées qui lui sont associées.

#### Configurer les propriétés du conteneur de formulaires adaptatifs {#configure-additional-settings-container}

Vous pouvez personnaliser les paramètres avancés du composant [!UICONTROL Conteneur de formulaires adaptatifs]. Par exemple,

* Vous pouvez configurer le service de préremplissage pour charger un formulaire adaptatif avec des valeurs préremplies sur une page de Site.
* Vous pouvez configurer les paramètres du modèle de données pour associer le formulaire adaptatif à une source de données.
* Vous pouvez configurer les actions d’envoi pour envoyer les données sur Microsoft® OneDrive, ou d’autres sources de données lors de l’envoi d’un formulaire. Vous pouvez également créer et sélectionner une action d’envoi personnalisée pour vos formulaires adaptatifs.

Pour définir les propriétés du composant **[!UICONTROL Conteneur de formulaires adaptatifs]**, cliquez sur ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) dans la barre d’actions. La boîte de dialogue **[!UICONTROL Modifier le conteneur de formulaires adaptatifs]** s’ouvre.

![Boîte de dialogue de modification](/help/forms/assets/adaptiveformcontainer-editdialog.png)

Dans la boîte de dialogue [!UICONTROL Modifier le conteneur de formulaires adaptatifs], précisez ce qui suit.
* **Onglet De base**
   * **Service de préremplissage** : vous pouvez utiliser le service de préremplissage pour remplir automatiquement les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ouvre un formulaire, les valeurs de ces champs sont préremplies. Pour plus d’informations sur le service de préremplissage, voir [Préremplir les champs de formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager.html?lang=fr).
   * **Catégorie de bibliothèque cliente** : spécifiez les [fonctions JavaScript](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=fr#custom-functions) qui sont utilisées dans les expressions et prises en charge par les formulaires adaptatifs.
* **Modèle de données** : un modèle de données vous permet d’intégrer des entités et des services provenant de sources de données disparates à un formulaire adaptatif. Choisissez le **[!UICONTROL modèle de données de formulaire]** si le formulaire adaptatif que vous créez implique l’extraction et l’écriture de données depuis et vers plusieurs sources de données.
   * **Modèle de données de formulaire** : un modèle de données de formulaire (FDM) permet à un formulaire adaptatif de communiquer avec des sources de données disparates. Pour plus d’informations sur la configuration d’une source de données, voir [Configurer des sources de données](/help/forms/configure-data-sources.md).
   * **Schéma** : le schéma représente la structure dans laquelle les données sont générées ou utilisées par le système back-end de votre organisation. Vous pouvez [associer le schéma à un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html?lang=fr) et utiliser ses éléments pour ajouter du contenu dynamique à un formulaire adaptatif.

     >[!NOTE]
     >
     > Après avoir configuré le modèle de données de formulaire (FDM), vous ne pouvez pas modifier le modèle de formulaire associé. Il est toutefois possible de modifier le schéma associé au modèle de données de formulaire (FDM).

* **Onglet Envoi**

   * **Rediriger vers l’URL**
      * **URL/chemin de redirection** : indique l’URL ou le chemin vers lequel un formulaire adaptatif est redirigé après l’envoi.

      * **Action d’envoi** : une action d’envoi est déclenchée lorsqu’un utilisateur ou une utilisatrice clique sur le bouton Envoyer d’un formulaire adaptatif. Vous pouvez [configurer l’action d’envoi sur le formulaire adaptatif](/help/forms/configuring-submit-actions.md). Les formulaire adaptatifs fournissent certaines actions d’envoi prêtes à l’emploi :
         * Envoyer vers le point d’entrée REST
         * Envoyer un e-mail
         * Envoyer à l’aide du modèle de données de formulaire (FDM)
         * Appeler un workflow AEM
         * Envoyer à SharePoint
         * Envoyer à OneDrive
         * Envoyer au stockage Blob Azure

  Vous pouvez également [étendre les actions d’envoi par défaut](custom-submit-action-form.md) pour créer votre propre action d’envoi.

* **Afficher le message**
   * **Contenu du message** : à l’aide de l’éditeur de texte enrichi, rédigez un message à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.

## Incorporer un formulaire adaptatif  {#aem-container-component}

L’utilisation du composant **[!UICONTROL Formulaires adaptatifs - Incorporer (V2)]** permet d’incorporer un nouveau formulaire adaptatif ou un formulaire adaptatif existant dans la page de Site. Le composant [!UICONTROL Forms adaptatif - Incorporer(v2)] permet d’effectuer les opérations suivantes :

* [Ajouter un formulaire adaptatif existant](#embed-new-af)

* [Créer et ajouter un nouveau formulaire adaptatif](#embed-existing-af)

### Prérequis {#prerequisites}

+++ Activez le composant **Formulaires adaptatifs - Incorporer**.

Pour activer le composant [!UICONTROL Formulaires adaptatifs - Incorporer (v2)] dans la politique du modèle, procédez comme suit :

1. Accédez à [!UICONTROL Informations sur la page] > [!UICONTROL Modifier le modèle].

1. Cliquez sur [!UICONTROL Politique] et cochez la case **[!UICONTROL Formulaire adaptatif - Incorporer (v2)]** sous le groupe **[!UICONTROL [Nom du projet Archetype AEM] - Forms]**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Inclure les bibliothèques clientes de formulaires adaptatifs à une page AEM Sites

Quand l’option **[!UICONTROL Lorsque le formulaire couvre toute la largeur d’une page]** est sélectionnée dans la boîte de dialogue de configuration **[!UICONTROL Conteneurs de formulaires]** et que les **Formulaires adaptatifs utilisant des composants principaux** sont utilisés, il est nécessaire d’inclure les bibliothèques clientes sur la page correspondant de Site.

![Gif de recouvrement](/help/forms/assets/overlaycorecomponent.gif)

Pour utiliser les composants Formulaires adaptatifs dans une page AEM Sites, incluez les bibliothèques clientes `Customheaderlibs` et `Customfooterlibs` sur la page AEM Sites à l’aide de l’Archétype AEM/du référentiel Git et du pipeline de déploiement.

1. Ouvrez votre projet [Archétype AEM Forms ou référentiel Git cloné](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) dans un éditeur de texte. Par exemple, Visual Studio Code.
1. Accédez à `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Copiez la valeur de `sling:resourceSuperType`. Par exemple, la valeur est `core/wcm/components/page/v3/page`.

   ![ressource sling](/help/forms/assets/slingresource.png)

1. Créez la structure similaire à l’emplacement `ui.apps/src/main/content/jcr_root/apps` identique à `core/wcm/components/page/v3/page`.

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png)

1. Ajoutez les fichiers `customheaderlibs.html` et `customfooterlibs.html`.

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

   Le `customfooterlibs.html` est utilisé pour JavaScript et `customheaderlibs.html` pour le CSS.

1. [Exécutez le pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=fr) pour déployer les modifications.

+++

### Ajouter un formulaire adaptatif existant à une page AEM Sites {#embed-existing-af}

1. Ouvrez la page AEM Sites en mode d’édition.
1. À partir du panneau Explorateur des composants, faites glisser et déposez le composant [!UICONTROL Formulaires adaptatifs - Incorporer] sur la page.
1. Sélectionnez le composant [!UICONTROL Forms adaptatif - Incorporer] dans la page des sites et sélectionnez ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) dans la barre d’actions. La boîte de dialogue **[!UICONTROL Modifier les formulaires adaptatifs - Incorporer]** s’ouvre.
1. Recherchez et sélectionnez le formulaire adaptatif à incorporer dans le [!UICONTROL chemin de la ressource].
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### Créer et ajouter un nouveau formulaire adaptatif à une page AEM Sites {#embed-new-af}

1. Ouvrez la page AEM Sites en mode d’édition.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant [!UICONTROL Formulaires adaptatifs - Incorporer (v2)] sur la page.
1. Cliquez sur l’icône **Plus** pour être redirigé vers l’assistant de création de formulaire.

   ![Composant Formulaires adaptatifs - Incorporer](/help/forms/assets/aemformcontainer.png)

1. Créez un formulaire adaptatif à partir de l’assistant [!UICONTROL Création de formulaire].
1. Le [!UICONTROL chemin de la ressource] inclut déjà le chemin d’un formulaire adaptatif créé.
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### Configurer les propriétés du formulaire adaptatif - Incorporer (v2) {#configure-adaptive-form-embed}

Vous pouvez personnaliser les paramètres avancés du composant [!UICONTROL Formulaire adaptatif - Incorporer (v2)]. Dans la boîte de dialogue [!UICONTROL Modifier les formulaires adaptatifs - Incorporer (v2)], vous pouvez spécifier ce qui suit.

* **Chemin d’accès à la ressource** : cherchez et sélectionnez le formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
* **Publier l’envoi** : sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.
   * **Afficher un message de remerciement** : à l’aide de l’éditeur de texte enrichi, rédigez un message à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
   * **Afficher une page de remerciement** : recherchez et sélectionnez la page à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Rediriger vers la page de remerciement** : activez cette option pour remplacer la page contenant le formulaire adaptatif incorporé par la page de remerciement. Autrement, la page de remerciement remplace le formulaire adaptatif dans le composant [!UICONTROL Formulaires adaptatifs - Incorporer] sans actualiser les sites sous-jacents de la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
* **Utiliser la langue de la page** : utilisez les paramètres régionaux de la page AEM Sites au lieu de ceux du formulaire adaptatif.
* **Définir le focus sur le formulaire** : sélectionnez cette option pour définir le focus sur le premier champ du formulaire adaptatif.
* **Le formulaire couvre toute la largeur du cadre** : si cette case est cochée, l’iframe n’est pas utilisé pour générer le formulaire.
* **Hauteur** : indiquez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
* **Bibliothèque cliente CSS** : spécifiez le chemin d’accès à une bibliothèque cliente CSS.

### Publier les formulaires adaptatifs ajoutés à l’aide du composant Formulaire adaptatif - Incorporer (v2)  {#publish-embedded-adaptive-form}

Tenez compte des scénarios suivants pour la publication des formulaires adaptatifs ajoutés à l’aide du composant **[!UICONTROL Formulaire adaptatif - Incorporer (v2)]** :

* Lorsque vous publiez une page AEM Sites pour la première fois, les formulaires ajoutés à la page Sites sont automatiquement publiés.
* Lorsque vous modifiez un formulaire adaptatif ajouté à une page Sites déjà publiée, publiez manuellement les formulaires adaptatifs correspondants.
* Lorsque vous modifiez une page Sites et les formulaires adaptatifs correspondants, republiez la page Sites et tous les formulaires adaptatifs ajoutés à la page Sites.

### Modifier des formulaires adaptatifs ajoutés à l’aide du composant Formulaire adaptatif - Incorporer (v2)  {#modifying-embedded-adaptive-form}

Pour modifier une configuration ou une propriété d’un formulaire adaptatif, procédez de l’une des manières suivantes :

* Ouvrez le formulaire d’origine dans un formulaire adaptatif dans l’éditeur correspondant et modifiez-le.
* Sélectionnez le formulaire adaptatif dans la page du site en mode d’édition, puis sélectionnez **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

## Modifier la disposition d’un formulaire adaptatif ajouté à une page AEM Sites {#change-layout-af-aem-sites-page}

Dans la page AEM Sites, le [mode Disposition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode.html?lang=fr) permet de redimensionner un formulaire adaptatif créé ou ajouté à une page AEM Sites.

![AF-layout-support](/help/forms/assets/afsite-layoutsupport.gif)

La page AEM Sites conserve une référence au formulaire adaptatif. Lorsque vous traduisez une page AEM Sites, un formulaire adaptatif et les ressources référencées qui lui sont associées sont traduits automatiquement dans d’autres langues à l’aide des [projets de traduction](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=fr#adding-pages-assets-to-a-translation-job).

## Bonnes pratiques {#best-practices}

* L’en-tête et le pied de page du formulaire d’origine ne sont pas intégrés dans le formulaire incorporé.
* Les brouillons et les envois de formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Formulaires envoyés du Portail Formulaires.

>[!MORELIKETHIS]
>
>* [Incorporer un formulaire adaptatif basé sur des composants principaux à une page web externe](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
>* [Incorporer le formulaire adaptatif dans une page web externe](/help/forms/embed-adaptive-form-external-web-page.md)