---
title: Comment ajouter un formulaire adaptatif à une page AEM Sites ?
description: Incorporez en toute transparence le Forms adaptatif dans une page AEM Sites ou une page web hébergée en dehors d’AEM.
feature: Adaptive Forms
Keywords: Forms AEM Sites, Embed Form to a Sites page, Adaptive Forms AEM Sites, Embed Adaptive Forms to AEM Page, Embed Forms in an AEM Sites page
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '3164'
ht-degree: 43%

---

# Incorporer un formulaire adaptatif dans une page AEM Sites {#embed-an-adaptive-form-to-aem-sites-page}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-aem-sites.html) |
| AEM as a Cloud Service | Cet article |


## Vue d’ensemble {#overview}

AEM Forms permet aux développeurs et développeuses de formulaires d’incorporer facilement des formulaires adaptatifs dans une page AEM Sites ou dans une page web hébergée en dehors d’AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel, et les utilisateurs et utilisatrices peuvent le remplir et l’envoyer sans quitter la page. Il permet à l’utilisateur ou à l’utilisatrice de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire. Ainsi, vos utilisateurs peuvent facilement remplir et envoyer des formulaires sans jamais quitter la page sur laquelle ils se trouvent. Cette intégration offre un moyen pratique de réutiliser le Forms adaptatif qu’il a déjà créé.

Vous pouvez utiliser AEM éditeur de page pour incorporer rapidement plusieurs formulaires à vos pages AEM Sites. L’utilisation de l’éditeur de page AEM permet aux auteurs de contenu de créer des expériences de capture de données en toute transparence dans une page Sites à l’aide de la puissance des composants Forms adaptatif, notamment le comportement dynamique, les validations, l’intégration de données, ainsi que la génération d’un document d’enregistrement et l’automatisation des processus d’entreprise. Il vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites, telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

Fourniture AEM Forms **[!UICONTROL Conteneur de formulaires adaptatifs]** et **[!UICONTROL Forms adaptatif - Incorporer (v2)]** composants. Vous pouvez utiliser **[!UICONTROL Forms adaptatif - Incorporer (v2)]** pour ajouter un formulaire adaptatif existant ou créer un formulaire à l’aide de l’ éditeur de Forms adaptatif , tandis que **[!UICONTROL Conteneur de formulaires adaptatifs]** pour créer un formulaire dans un fragment d’expérience ou une page AEM Sites.

![Exemple de formulaire adaptatif dans une page AEM Sites](/help/forms/assets/adaptive-form-in-sites-page.png)

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). 

## Why embed an Adaptive Form in AEM Sites page or AEM Experience Fragment? 

Using **[!UICONTROL Adaptive Forms – Embed(v2)]** in AEM Page Editor lets you create seamless data capture experiences within a Sites page using the power of Adaptive Forms components including dynamic behavior, validations, data integration, generate document of record and business process automation. It also lets you use various features of AEM Sites pages like, versioning, targeting, translation, and multi-site manager, enhancing the overall form creation and management experience. Let's explore some of these features:

* **Versioning:** AEM Sites pages offer [robust versioning capabilities](/help/sites-cloud/authoring/features/page-versions.md), allowing you to track and manage different versions of your forms. This enables you to make changes and enhancements to forms while maintaining the ability to roll back to previous versions if needed. Versioning ensures a controlled and organized approach to form development and evolution.
* **Targeting (Integration with Adobe Target):** With AEM Sites pages targeting capabilities, you can also [personalize the form experience for different audiences](/help/sites-cloud/integrating/integration-adobe-target-ims.md). By using user segments and targeting criteria, you can tailor the form's content, design, or behavior to specific groups of users. This enables you to provide a personalized and relevant form experience, increasing engagement and conversion rates.
* **Translation:** AEM Sites [seamless integration with translation services](/help/sites-cloud/administering/translation/overview.md), allowing you to translate forms into multiple languages easily. This feature simplifies the localization process, ensuring that your forms are accessible to a global audience. You can manage translations efficiently within AEM translation projects, reducing time and effort required for multilingual form support. See considerations section for more information on translation.  
* **Multi-site Management and Live Copy:** AEM Sites provide robust [Multi-site Management and Live Copy capabilities](/help/sites-cloud/administering/msm/overview.md), enabling you to create and manage multiple websites within a single environment. This feature now lets you reuse forms across different sites, ensuring consistency and reducing duplication efforts. With centralized control and management, you can efficiently maintain and update forms across multiple websites.
* **Themes:** AEM Sites pages provide a framework for designing and maintaining consistent visual styles across multiple web pages. These define colors, fonts, style sheets, and other visual elements that contribute to the overall look and feel of the website. [You can use the themes designed for an AEM Sites page for an Adaptive Form, saving time and effort](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes). 
* **Tagging:** AEM Sites pages allow you to [assign tags or labels to a page, an asset, or other content](/help/implementing/developing/introduction/tagging-framework.md). Tags are keywords or metadata labels that provide a way to categorize and organize content based on specific criteria. You can assign one or more tags to pages, assets, or any other content items within AEM to improve search and categorize the assets. 
* **Locking and Unlocking content:** AEM Sites allow users to [control access and modifications to pages](/help/sites-cloud/authoring/fundamentals/editing-content.md) within the AEM Sites environment. When a page is locked, it means that it is protected from unauthorized changes or edits by other users. Only the user who has locked the content or a designated administrator can unlock it to allow modifications. 

In addition, Adaptive Forms in AEM Page Editor use [Adaptive Forms Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#features). These Core Components provide a standard and easier methods to style and customize the components, identical to [AEM Sites WCM Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).

-->

## Comment créer ou incorporer un formulaire adaptatif dans une page AEM Sites ou dans AEM fragment d’expérience ? {#various-options-to-create-or-embed-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Vous pouvez tirer pleinement parti de cette fonctionnalité en utilisant les options suivantes :

* **[Créer un formulaire adaptatif à l’aide de modèles approuvés et l’incorporer à une page AEM Sites](#embed-form-using-adaptive-form-wizzard-aem-sites):** Vous pouvez tirer parti de modèles prévalidés pour créer et incorporer rapidement des Forms adaptatives conformes aux directives de marque et aux normes de conception de votre entreprise.

* **[Incorporation de formulaires existants dans une page AEM Sites](#embed-an-adaptive-form-in-sites-editor):** Vous pouvez facilement intégrer des formulaires que vous avez déjà créés dans vos sites web, ce qui permet aux visiteurs d’interagir directement avec eux.

* **[Convertir un formulaire adaptatif incorporé en fragment d’expérience](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Convertissez un formulaire adaptatif incorporé ajouté à une page AEM Sites en un fragment d’expérience pour réutiliser le formulaire sur plusieurs pages AEM Sites.

* **[Créer et ajouter un formulaire adaptatif personnalisé à une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor-or-experience-fragment) :****[!UICONTROL vous pouvez utiliser le composant Conteneur de formulaires adaptatifs pour créer entièrement un formulaire, en l’adaptant spécifiquement à vos besoins et préférences de conception.]**

* **[Créer et ajouter un formulaire adaptatif personnalisé à un fragment d’expérience](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor) :** vous pouvez étendre la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites.

* **Ajouter plusieurs formulaires à une page AEM Sites ou à un fragment d’expérience :** vous pouvez créer ou ajouter plusieurs formulaires adaptatifs à une page AEM Sites afin de proposer plusieurs choix aux utilisateurs et utilisatrices en fonction de leurs préférences et de leurs besoins. Vous pouvez utiliser AEM éditeur de page pour incorporer rapidement plusieurs formulaires à vos pages AEM Sites. Vous pouvez utiliser la variable **[!UICONTROL Conteneur de formulaires adaptatifs]** à plusieurs reprises pour ajouter le Forms adaptatif dans une page AEM Sites. Vous pouvez utiliser la variable **[!UICONTROL Forms adaptatif - Incorporer]** composant plusieurs fois dans une page AEM Sites, uniquement si **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** est sélectionnée. Au cas où la variable **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** n’est pas cochée, la page AEM Sites ne prend en charge qu’un seul formulaire adaptatif pour exister sans iframe. Pour ajouter d’autres Forms adaptatives à l’aide du **[!UICONTROL Forms adaptatif - Incorporer]** component, select **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** .

## Observations relatives à l’intégration d’un formulaire adaptatif dans une page AEM Sites ou dans un fragment d’expérience AEM {#consideration}

* Lorsque vous créez ou ajoutez un formulaire à l’aide de la fonction **[!UICONTROL Forms adaptatif - Incorporer (v2)]** , les formulaires sont traduits et localisés à l’aide du flux de traduction AEM Forms. Dans ce cas, un seul formulaire est conservé et référencé dans toutes les copies de langue des pages Sites. **[!UICONTROL Forms adaptatif - Incorporer (v2)]** ne permet pas d’accéder aux différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

* Lorsque vous utilisez la variable **[!UICONTROL Conteneur de formulaires adaptatifs]** pour créer un formulaire, les formulaires sont traduits et localisés par le biais du flux de traduction AEM Sites. Pour chaque langue, une copie distincte (copie de langue) de la page du site et des formulaires correspondants est générée. Lorsqu’un auteur ou une autrice de contenu modifie une règle dans un formulaire sur la page parente, les mêmes modifications doivent être effectuées dans toutes les copies de langue du formulaire. **[!UICONTROL Conteneur de formulaires adaptatifs]** vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.


## Conditions requises pour incorporer un formulaire adaptatif dans une page AEM Sites ou dans un fragment d’expérience AEM {#before-you-start-embedding-an-adaptive-form}

Avant d’incorporer un nouveau formulaire adaptatif ou un formulaire adaptatif préexistant à l’aide de **[!UICONTROL Forms adaptatif - Incorporer (v2)]**, activez **Composants principaux de Forms adaptatif** et ajouter **Bibliothèques clientes Forms adaptatives** à votre page AEM Sites :

+++  Activer les composants principaux des formulaires adaptatifs pour votre environnement AEM Cloud Service

Assurez-vous que les [composants principaux de formulaires adaptatifs sont activés pour votre environnement AEM Forms as a Cloud Service](enable-adaptive-forms-core-components.md).

+++

+++  Ajouter des bibliothèques clientes de formulaires adaptatifs à votre page AEM Sites ou votre fragment d’expérience

Lorsque la variable **[!UICONTROL Lorsque le formulaire couvre toute la largeur d’une page]** est sélectionnée dans la variable **[!UICONTROL Conteneurs de formulaires]** Configurez la boîte de dialogue et Adaptive Forms à l’aide des composants principaux est utilisé. Il est nécessaire d’inclure les bibliothèques clientes sur la page de votre site correspondant.

![Lorsque l’option Form cover (couvre toute la largeur d’une page) est sélectionnée, le formulaire adaptatif avec les composants principaux est utilisé.](/help/forms/assets/overlaycorecomponent.gif)


Ajoutez la variable **Customheaderlibs** et **Customfooterlibs** bibliothèques clientes vers votre page AEM Sites à l’aide du pipeline de déploiement. Pour ajouter les bibliothèques clientes :

1. Accédez à et clonez votre [référentiel Git AEM Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html?lang=fr).
1. Ouvrez le dossier Référentiel Git AEM Cloud Service dans un éditeur de texte brut. Par exemple, Microsoft® Visual Code.
1. Ouvrez le fichier `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` et ajoutez le code suivant au fichier :

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Ouvrez le fichier `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` et ajoutez le code suivant au fichier :

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Ouvrez le fichier `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` et ajoutez le code suivant au fichier :

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Ouvrez le fichier `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` et ajoutez le code suivant au fichier :

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [Exécutez le pipeline de déploiement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=fr) pour déployer les bibliothèques clientes dans votre environnement AEM as a Cloud Service.

+++

+++ Activer **[!UICONTROL Forms adaptatif - Incorporer (v2)]** pour votre page AEM Sites ou votre fragment d’expérience

Pour activer **[!UICONTROL Forms adaptatif - Incorporer (v2)]** dans la stratégie du modèle, procédez comme suit :

1. Ouvrez la page AEM Sites ou le fragment d’expérience pour modification. Pour ouvrir la page à modifier, sélectionnez-la, puis cliquez sur **[!UICONTROL Modifier]**.
1. Ouvrez le modèle de votre page Sites ou Fragment d’expérience. Pour ouvrir le modèle, accédez aux **[!UICONTROL Informations sur la page]** ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Modifier le modèle]**. Le modèle correspondant s’ouvre dans l’éditeur de modèles.
1. Dans la vue Structure, cliquez sur l’icône **[!UICONTROL Politique]** ![Politique](/help/forms/assets/Smock_FeedManagement_18_N.svg) dans la barre de menus. Dans le **[!UICONTROL Composants autorisés]** et sélectionnez la variable **[!UICONTROL Forms adaptatif - Incorporer (v2)]**  sous la case **[Nom du projet AEM Archetype] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

## Incorporation d’un formulaire adaptatif à l’aide du composant Forms adaptatif - Incorporer (v2) {#embed-an-adaptive-form-in-sites-editor-or-experience-fragment}

Utilisez la variable **[!UICONTROL Forms adaptatif - Incorporer (v2)]** pour créer un formulaire adaptatif directement dans l’éditeur AEM Sites à l’aide de l’assistant de création de formulaire. Le formulaire obtenu est enregistré en tant qu’entité externe, ce qui permet sa réutilisation dans d’autres pages Sites et dans des formulaires autonomes. Vous pouvez incorporer entièrement un nouveau formulaire, en le adaptant spécifiquement à vos besoins et préférences de conception, directement dans une page AEM Sites ou dans un fragment d’expérience. Pour les formulaires à usage unique, il est recommandé d’effectuer une création directe sur une page AEM Sites, tandis que les fragments d’expérience sont idéaux pour les formulaires qui doivent être réutilisés sur plusieurs pages de votre site web.

Vous pouvez facilement incorporer un nouveau formulaire à l’aide de **[!UICONTROL Forms adaptatif - Incorporer (v2)]**.  Imaginez, par exemple, l’incorporation d’un nouveau formulaire de contact dans une page AEM Sites ou dans un fragment d’expérience AEM. Toute mise à jour ou modification apportée au formulaire de contact dans la page AEM Sites ou au fragment d’expérience s’applique automatiquement à toutes les pages sur lesquelles il est déployé. Cela simplifie la gestion des formulaires de votre site web, assurant une expérience utilisateur transparente tout en rationalisant le processus global.

Utilisation **[!UICONTROL Forms adaptatif - Incorporer (v2)]**, vous pouvez :

* [Incorporer un nouveau formulaire à l’aide de l’assistant de Forms adaptatif dans la page AEM Sites](#embed-form-using-adaptive-form-wizzard-aem-sites)
* [Incorporation d’un nouveau formulaire à l’aide de l’assistant de Forms adaptatif dans un fragment d’expérience](#embed-form-using-adaptive-form-wizzard-experience-fragment)
* [Incorporation d’un formulaire adaptatif existant dans une page AEM Sites](#embed-an-adaptive-form-in-sites-editor)
* [Incorporation d’un formulaire existant dans un fragment d’expérience](#embed-an-adaptive-form-in-experience-fragment)
* [Convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Incorporer un nouveau formulaire à l’aide de l’assistant de Forms adaptatif dans la page AEM Sites {#embed-form-using-adaptive-form-wizzard-aem-sites}

Les étapes pour incorporer un nouveau formulaire à une page AEM Sites sont les suivantes :

1. Ouvrez la page AEM Sites en mode d’édition.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant **[!UICONTROL Formulaires adaptatifs - Incorporer (v2)]** sur la page.
1. Cliquez sur l’icône **Plus** pour être redirigé vers l’assistant de création de formulaire.

   ![Composant Formulaires adaptatifs - Incorporer](/help/forms/assets/aemformcontainer.png)

1. Créez un formulaire adaptatif à partir de l’assistant **[!UICONTROL Création de formulaire.]**
Le **[!UICONTROL chemin de la ressource]** inclut déjà le chemin d’un formulaire adaptatif créé.
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

Ensuite, vous pouvez [Définition de l’action Envoyer](/help/forms/configuring-submit-actions.md) et les propriétés avancées d’un formulaire adaptatif incorporé à l’aide de l’assistant de création de formulaire.


### Incorporation d’un nouveau formulaire à l’aide de l’assistant de Forms adaptatif dans un fragment d’expérience {#embed-form-using-adaptive-form-wizzard-experience-fragment}

Les étapes pour incorporer un nouveau formulaire à un fragment d’expérience sont les suivantes :

1. Ouvrez le fragment d’expérience en mode d’édition.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant **[!UICONTROL Formulaires adaptatifs - Incorporer (v2)]** sur la page.
1. Cliquez sur l’icône **Plus** pour être redirigé vers l’assistant de création de formulaire.

   ![Composant Formulaires adaptatifs - Incorporer](/help/forms/assets/aemformcontainer.png)

1. Créez un formulaire adaptatif à partir de l’assistant **[!UICONTROL Création de formulaire.]**
Le **[!UICONTROL chemin de la ressource]** inclut déjà le chemin d’un formulaire adaptatif créé.
1. Enregistrez les paramètres. Le formulaire adaptatif est désormais incorporé au fragment d’expérience.

Ensuite, vous pouvez [Définition de l’action Envoyer](/help/forms/configuring-submit-actions.md) et les propriétés avancées d’un formulaire adaptatif incorporé à l’aide de l’assistant de création de formulaire.

### Incorporation d’un formulaire adaptatif existant dans une page AEM Sites {#embed-an-adaptive-form-in-sites-editor}

Avec la variable **[!UICONTROL Forms adaptatif - Incorporer (v2)]** , vous pouvez intégrer facilement un formulaire adaptatif préexistant à une page dans AEM Sites. Cette fonctionnalité améliore considérablement l’adaptabilité et la réutilisation d’Adaptive Forms, offrant ainsi aux clients un moyen pratique de réutiliser les formulaires qu’ils ont déjà créés. Imaginez par exemple l’incorporation d’un formulaire de contact à une page AEM Sites, ce qui évite d’avoir à le recréer plusieurs fois.

Pour incorporer un formulaire adaptatif existant dans une page Sites :

1. Ouvrez la page AEM Sites en mode d’édition.
1. Faites glisser et déposez le **[!UICONTROL Forms adaptatif - Incorporer (v2)]** du navigateur de composants vers la page Sites.
1. Appuyez sur le bouton **[!UICONTROL Forms adaptatif - Incorporer]** sur la page Sites, puis appuyez sur ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) dans la barre d’actions. La variable **[!UICONTROL Modifier le Forms adaptatif - Incorporer (v2)]** s’ouvre.
1. Recherchez et sélectionnez le formulaire adaptatif à incorporer dans le **[!UICONTROL chemin de la ressource]**.
1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

Ensuite, vous pouvez [Définition de l’action Envoyer](/help/forms/configuring-submit-actions.md) et les propriétés avancées d’un formulaire adaptatif incorporé à l’aide de l’assistant de création de formulaire.

### Incorporation d’un formulaire adaptatif existant dans un fragment d’expérience {#embed-an-adaptive-form-in-experience-fragment}

Vous pouvez également étendre l’accessibilité de vos formulaires en les incorporant au fragment d’expérience AEM. Pour incorporer un formulaire adaptatif dans un fragment d’expérience :

1. Ouvrez un fragment d’expérience en mode d’édition.
1. Faites glisser et déposez le **[!UICONTROL Forms adaptatif - Incorporer (v2)]** du navigateur de composants au fragment d’expérience.
1. Appuyez sur le bouton **[!UICONTROL Forms adaptatif - Incorporer]** dans le fragment d’expérience, puis appuyez sur ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) dans la barre d’actions. La variable **[!UICONTROL Modifier le Forms adaptatif - Incorporer (v2)]** s’ouvre.
1. Recherchez et sélectionnez le formulaire adaptatif à incorporer dans le **[!UICONTROL chemin de la ressource]**.
1. Enregistrez les paramètres. Le formulaire adaptatif est désormais incorporé au fragment d’expérience.

Ensuite, vous pouvez [Définition de l’action Envoyer](/help/forms/configuring-submit-actions.md) et les propriétés avancées d’un formulaire adaptatif incorporé à l’aide de l’assistant de création de formulaire.

### Convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Vous pouvez convertir un formulaire adaptatif existant dans un éditeur de page d’AEM Sites en fragment d’expérience afin de réutiliser le formulaire sur plusieurs pages ou sites.

Pour convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience :

1. Ouvrez la page AEM Sites contenant le formulaire adaptatif (dans le composant de conteneur de formulaires adaptatifs) en mode d’édition.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.
1. Dans la barre de menu, sélectionnez l’![icône Convertir en variation de fragment d’expérience](/help/forms/assets/Smock_FilingCabinet_18_N.svg)icône Convertir en variation de frangment d’expérience.

   ![Cliquez sur le logo de l’armoire à fichiers pour convertir un formulaire adaptatif dans la page AEM Sites en fragment d’expérience](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Une boîte de dialogue pour convertir le conteneur de formulaires adaptatifs en un nouveau fragment d’expérience ou l’ajouter à un fragment d’expérience existant s’affiche.

1. Sur le **[!UICONTROL Convertir en fragment d’expérience]** de la boîte de dialogue variation, définissez les valeurs des options suivantes :

   * **Action :** Sélectionnez cette option pour créer un fragment d’expérience ou Ajouter à un fragment d’expérience existant.
   * **Chemin d’accès parent :** spécifiez le chemin du dossier dans lequel héberger le fragment d’expérience. Cette option est disponible uniquement pour la création d’un fragment d’expérience.
   * **Modèle :** spécifiez le chemin du modèle de fragment d’expérience. Si vous ne disposez pas d’un modèle de fragment d’expérience, [créez-le](/help/implementing/developing/extending/experience-fragments.md). Cette option est disponible uniquement pour l’ajout d’un formulaire adaptatif à un fragment d’expérience existant.
   * **Titre du fragment :** spécifiez le titre du fragment d’expérience. Le titre identifie de manière unique un fragment d’expérience.
   * **Balises de fragment :** Spécifiez la balise du fragment d’expérience. La balise identifie de manière unique la catégorie d’un fragment d’expérience.

## Configuration des propriétés Adaptive Form-Embed(v2)

Vous pouvez personnaliser les paramètres avancés du composant **[!UICONTROL Formulaire adaptatif - Incorporer (v2)]**. Dans le **[!UICONTROL Modifier le Forms adaptatif - Incorporer]** , vous pouvez spécifier les éléments suivants :

* **Chemin de la ressource**: recherchez et sélectionnez un formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
* **Publier l’envoi** : sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.
   * **Afficher un message de remerciement** : à l’aide de l’éditeur de texte enrichi, rédigez un message à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
   * **Afficher une page de remerciement** : recherchez et sélectionnez la page à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Rediriger vers la page de remerciement** : activez cette option pour remplacer la page contenant le formulaire adaptatif incorporé par la page de remerciement. Sinon, la page de remerciement remplace le formulaire adaptatif dans la **[!UICONTROL Forms adaptatif - Incorporer (v2)]** sans actualiser les sites sous-jacents de la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Message de remerciement**: brève confirmation ou confirmation affichée à l’écran après l’envoi réussi d’un formulaire.
   * **Page Merci**: recherchez et sélectionnez la page à afficher après l’envoi réussi d’un formulaire.

* **Utiliser la langue de la page** : utilisez les paramètres régionaux de la page AEM Sites au lieu de ceux du formulaire adaptatif. Cette option s’applique uniquement au formulaire adaptatif (Foundation).
* **Définir le focus sur le formulaire** : sélectionnez cette option pour définir le focus sur le premier champ du formulaire adaptatif. Cette option s’applique uniquement au formulaire adaptatif (Foundation).
* **Thème** : sélectionnez un thème qui définit le style des composants de votre formulaire adaptatif. Style comprend des propriétés d’aspect, comme le style de police, la couleur d’arrière-plan, les dimensions et l’alignement. Cette option s’applique uniquement au formulaire adaptatif (Foundation).

  >[!NOTE]
  >
  > Vous pouvez utiliser la variable **Utiliser la langue de la page**, **Définir la cible d’action sur le formulaire** et **Thème** options uniquement pour le formulaire adaptatif (Foundation).

* **Le formulaire couvre toute la largeur du cadre.**: un cadre intégré (iframe) est un élément de HTML qui charge un formulaire adaptatif sur une page AEM Sites.

   * Si la variable **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** est cochée, un formulaire adaptatif occupe toute la largeur du conteneur dans lequel il est placé. Dans ce cas, un iframe n’est pas utilisé pour générer le formulaire. La mise en page et la conception d’un formulaire adaptatif s’adaptent à toute la largeur du conteneur, ce qui le rend réactif et capable de s’adapter à différentes tailles d’écran. Cette option permet d’incorporer plusieurs Forms adaptatives dans une page AEM Sites.

     >[!NOTE]
     >
     > Pour incorporer plusieurs formulaires dans une page AEM Sites, sélectionnez **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** .

   * Si la variable **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** n’est pas cochée, un formulaire adaptatif ne couvre pas toute la largeur du conteneur. Au lieu de cela, un iframe est utilisé pour générer le formulaire, qui ne peut pas être étendu au-delà d’une largeur spécifique. Cette approche est utile lorsqu’un formulaire adaptatif a des limites définies et doit coexister avec d’autres composants AEM à côté dans le conteneur. Si cette option n’est pas cochée, elle n’autorise l’intégration d’une seule Forms adaptative dans la page AEM Sites sans iframe.

     >[!NOTE]
     >
     > La page AEM Sites ne prend en charge qu’un seul formulaire adaptatif pour exister sans iframe. Pour ajouter d’autres Forms adaptatives à l’aide du **[!UICONTROL Forms adaptatif - Incorporer]** component, select **[!UICONTROL Le formulaire couvre toute la largeur du cadre.]** .

* **Hauteur** : indiquez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
* **Bibliothèque cliente CSS** : spécifiez le chemin d’accès à une bibliothèque cliente CSS.

<!--
In AEM Sites page, you can add an Adaptive Form using:

* **Adaptive Forms - Embed component**
   Adaptive Forms - Embed component enables AEM Sites authors to include an existing Adaptive Form within an AEM Sites page, thereby enhancing the reusability of adaptive forms. Existing Adaptive Forms can be used standalone or embedded in the site page. This integration provides a convenient way for customers to reuse Adaptive Forms they have already created.

* **Asset browser**
  All the forms are available under Assets. You can drag-drop the form as an asset on your page.

## Prerequisites {#prerequisites}

 To embed an Adaptive Form in an AEM Sites page that uses an editable template, ensure that the AEM Form component is configured as an allowed component in the associated template. 

In case **Adaptive Forms - Embed component** is not visible in the **Component browser panel** of AEM sites page, perform the following steps as illustrated in the video.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

In case Sites page is using a static template, you need to configure it in the paragraph system of the site page. 

## Embedding an Adaptive Form {#af-component}

To embed an Adaptive Form using the **[!UICONTROL Adaptive Forms - Embed]** component:

1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the [!UICONTROL Adaptive Forms - Embed] component on the page. Alternatively, you can search for an Adaptive Form in the Assets browser and drag-drop it onto the Sites page. You can add a new Adaptive Form or embed an existing Adaptive Form. 

   >[!NOTE]
   >
   >Multiple Adaptive Forms - Embed components on a page are not supported.

1. To create and embed a new form, on the component toolbar, tap the **Create Form** icon. A window to create the form opens. 

1. Tap the embedded Adaptive Forms - Embed component in the sites page, and then tap ![settings_icon](assets/settings_icon.png) on the action bar. The **[!UICONTROL Edit Adaptive Forms - Embed]** dialog opens.
1. In the Edit Adaptive Forms - Embed dialog, specify the following.

    **Asset Type:** Select the type of asset to embed. 
    * **Asset Path**: Browse and select the Adaptive Form to embed. It is auto-populated if you dropped it from the Assets browser.
    * **Post Submission** : Select the action to trigger on form submission. You can choose to show a thank you message or a thank you page.
        * Show

        * **Thank You Message**: Write a message using the rich text editor to show on form submission. This option is available only when you choose to show a thank you message.
        * **Thank You Page**: Browse and select the page to display on form submission. This option is available only when you choose to show a thank you page.
           * **Redirect to thank you page**: Enable the option to replace the page containing the embedded Adaptive Form with thank you page. Otherwise, the thank you page replaces the Adaptive Form in the [!UICONTROL Adaptive Forms - Embed] component, without refreshing underlying sites the page. This option is available only when you choose to show a thank you page.
    * **Use Page Language**: Use local of the AEM Sites page instead locale of Adaptive Form.
    * **Set Focus on Form**: Select to set the focus on the first field of the Adaptive Form.
    * **Theme**: Select a theme that defines styling for components of your Adaptive Form. Styling includes appearance properties such as font style, background color, dimensions, and alignment.
    * **Form covers entire width of the frame**: If checked, iframe is not used to render the form. 
    * **Height**: Specify the height of the container. Leave it blank to automatically resize the container.
    * **CSS Client library**: Specify path to a CSS client library.

1. Save the settings. The Adaptive Form  is now embedded in the page.


AEM site also lets you create an Adaptive Form on the fly using the Adaptive Forms - Embed component. Follow the steps to create an Adaptive Form using the **Adaptive Forms - Embed component** on AEM sites page:
1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the Adaptive Forms - Embed component on the page.
1. Click the **Plus** icon and you are redirected to the form creation wizard.

    ![Adaptive Forms - Embed Component](/help/forms/assets/aemformcontainer.png)

1. You can now embed an Adaptive Form on AEM site pages using the [!UICONTROL AEM Forms Container Component].
-->

## Publier le formulaire adaptatif incorporé {#publishing-embedded-adaptive-form}

Examinons les scénarios suivants concernant la publication d’un formulaire adaptatif incorporé dans une page AEM Sites :

* Si vous publiez la page AEM Sites pour la première fois et qu’elle comporte un formulaire adaptatif incorporé, publiez la page de Sites et la ressource incorporée.
* Si vous n’avez modifié que le formulaire incorporé à une page de site publiée, publiez le formulaire d’origine et les modifications seront répercutées sur la page de site publiée. La page de site publiée comprend une référence à la ressource et ne doit pas être republiée.
* Si vous avez modifié la page de site et le formulaire adaptatif ou la communication interactive incorporé, republiez la page de site et la ressource incorporée.

## Modification d’un formulaire adaptatif incorporé  {#modifying-embedded-adaptive-form}

Pour modifier une configuration ou une propriété du formulaire adaptatif incorporé, procédez de l’une des manières suivantes.

* Ouvrez le formulaire d’origine dans un formulaire adaptatif dans l’éditeur correspondant et modifiez-le.
* Appuyez sur le formulaire adaptatif à partir de la page du site en mode d’édition, puis appuyez sur **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

>[!NOTE]
>
>Les modifications apportées au formulaire d’origine sont répercutées automatiquement dans le formulaire incorporé. Cependant, republiez le formulaire adaptatif, ou la page du site, pour refléter les modifications apportées à la page publiée.

## Bonnes pratiques {#best-practices}

Lorsque vous incorporez des formulaires adaptatifs à des pages AEM Sites, gardez en tête les points suivants :

* L’en-tête et le pied de page du formulaire d’origine ne sont pas intégrés dans le formulaire incorporé.
* Les brouillons et les envois de formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Formulaires envoyés du Portail Formulaires.
* L’action Envoyer configurée sur le formulaire d’origine est conservée dans le formulaire incorporé.
* Si vous avez configuré Adobe Analytics pour le formulaire d’origine, les données d’analyse du formulaire incorporé seront capturées dans Adobe Analytics. En revanche, elles ne seront pas disponibles dans le rapport d’analyse des formulaires.

## Voir également {#see-also}

* [créer des formulaires adaptatifs autonomes basés sur des composants principaux ;](/help/forms/creating-adaptive-form-core-components.md)
* [créer un formulaire adaptatif basé sur des composants principaux directement dans une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
