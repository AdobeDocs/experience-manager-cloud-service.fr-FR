---
title: Comment ajouter un formulaire adaptatif à une page AEM Sites ?
description: Découvrez comment créer ou ajouter un formulaire adaptatif à votre page AEM Sites. Découvrez également les avantages et les différentes manières d’intégrer des formulaires à votre site web.
feature: Adaptive Forms, Foundation Components
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
exl-id: a1846c5d-7b0f-4f48-9d15-96b2a8836a9d
role: User, Developer
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '3306'
ht-degree: 78%

---

# Ajouter un formulaire adaptatif à une page AEM Sites ou un fragment d’expérience {#create-or-add-an-adaptive-form-to-aem-sites-page}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html) |
| AEM as a Cloud Service | Cet article |

## Vue d’ensemble {#overview}

AEM Forms vous permet d’ajouter facilement un formulaire à votre page AEM Sites. Vos visiteurs et visiteuses peuvent ainsi remplir et envoyer facilement des formulaires sans jamais quitter la page sur laquelle ils ou elles se trouvent. Ce faisant, ils ou elles peuvent continuer à utiliser sans effort d’autres éléments du site web tout en interagissant activement avec le formulaire.

Vous pouvez utiliser l’éditeur de page d’AEM pour créer et ajouter rapidement plusieurs formulaires à vos pages AEM Sites. L’utilisation de l’éditeur de page d’AEM permet aux auteurs de contenu de créer des expériences de capture de données transparentes dans une page Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération de documents d’enregistrement et l’automatisation des processus métier. L’éditeur de page permet également d’utiliser différentes fonctionnalités des pages d’AEM Sites, telles que le contrôle de version, le ciblage, la traduction et Multi-Site Manager.

AEM Forms Cloud Service fournit des composants Conteneur de formulaires adaptatifs et Forms adaptatif - Incorporer . Vous pouvez utiliser le conteneur de formulaires adaptatifs pour créer un formulaire dans une page AEM Sites ou un fragment d’expérience, tandis que le composant Forms adaptatif - Incorporer vous permet d’ajouter un formulaire adaptatif existant ou de créer un formulaire à l’aide de l’éditeur de Forms adaptatif.

![Exemple de formulaire adaptatif dans une page AEM Sites](/help/forms/assets/adaptive-form-in-sites-page.png)

## Pourquoi utiliser les composants principaux de Forms adaptatif pour créer un formulaire adaptatif dans une page AEM Sites ou un fragment d’expérience ?

Si vous avez créé par le passé un composant de base de Forms adaptatif ou des formulaires HTML simples pour vos sites, Adobe vous recommande d’utiliser les composants principaux de Forms adaptatif pour créer un formulaire adaptatif dans une page AEM Sites ou un fragment d’expérience. Il vous permet d’utiliser diverses fonctionnalités des pages AEM Sites, telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples, ce qui améliore l’expérience globale de création et de gestion de formulaires pour le Forms adaptatif. Examinons quelques-unes de ces fonctionnalités :

* **Contrôle de version :** les pages AEM Sites vous offrent des [fonctionnalités de contrôle de version fiables](/help/sites-cloud/authoring/sites-console/page-versions.md), ce qui vous permet de suivre et de gérer différentes versions de vos formulaires. Vous pouvez ainsi apporter des modifications et des améliorations aux formulaires tout en conservant la possibilité de restaurer des versions précédentes si nécessaire. Le contrôle de version garantit une approche contrôlée et organisée du développement et de l’évolution des formulaires.
* **Ciblage (intégration à Adobe Target) :** avec les fonctionnalités de ciblage des pages AEM Sites, vous pouvez également [personnaliser l’expérience du formulaire pour différentes audiences](/help/sites-cloud/integrating/integrating-adobe-target.md). En exploitant les segments d’utilisateurs et d’utilisatrices et les critères de ciblage, vous pouvez personnaliser le contenu, la conception ou le comportement du formulaire en fonction de groupes d’utilisateurs et d’utilisatrices spécifiques. Vous pouvez ainsi offrir une expérience de formulaire personnalisée et pertinente, ce qui augmente l’engagement et les taux de conversion.
* **Traduction :** intégration transparente d’AEM Sites [à des services de traduction](/help/sites-cloud/administering/translation/overview.md), ce qui vous permet de traduire facilement des formulaires en plusieurs langues. Cette fonctionnalité simplifie le processus de localisation, en veillant à ce que vos formulaires soient accessibles à une audience globale. Vous pouvez gérer efficacement les traductions dans les projets de traduction d’AEM, ce qui réduit le temps et les efforts requis pour la prise en charge des formulaires multilingues. Pour plus d’informations sur la traduction, reportez-vous à la section Remarques.
* **Gestion multisite et Live Copy :** AEM Sites vous offre une fonctionnalité fiable de [gestion multisite et de Live Copy](/help/sites-cloud/administering/msm/overview.md), vous permettant de créer et de gérer plusieurs sites web au sein d’un seul environnement. Cette fonctionnalité vous permet désormais de réutiliser des formulaires sur différents sites, assurant ainsi la cohérence et réduisant les efforts de duplication. Grâce à un contrôle et une gestion centralisés, vous pouvez gérer et mettre à jour efficacement les formulaires sur plusieurs sites web.
* **Thèmes :** les pages AEM Sites vous fournissent un cadre pour la conception et la gestion de styles visuels cohérents sur plusieurs pages web. Elles définissent les couleurs, les polices, les feuilles de style et d’autres éléments visuels qui contribuent à l’aspect général du site web. [Vous pouvez utiliser les thèmes conçus pour une page AEM Sites pour un formulaire adaptatif afin de gagner du temps.](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **Balisage :** les pages AEM Sites vous permettent d’[affecter des balises ou des étiquettes à une page, à une ressource ou à un autre contenu](/help/implementing/developing/introduction/tagging-framework.md). Les balises sont des mots-clés ou des étiquettes de métadonnées qui permettent de classer et d’organiser du contenu selon des critères spécifiques. Vous pouvez affecter une ou plusieurs balises aux pages, aux ressources ou à tout autre élément de contenu dans AEM afin d’améliorer la recherche et de classer les ressources.
* **Verrouillage et déverrouillage de contenu :** AEM Sites permet à ses utilisateurs et utilisatrices de [contrôler l’accès aux pages et leurs modifications](/help/sites-cloud/authoring/page-editor/edit-content.md) dans l’environnement AEM Sites. Lorsqu’une page est verrouillée, cela signifie qu’elle est protégée contre les changements ou modifications non autorisés par d’autres utilisateurs et utilisatrices. Seule la personne qui a verrouillé le contenu ou l’équipe d’administration désignée peut le déverrouiller pour autoriser les modifications.

En outre, le Forms adaptatif dans l’éditeur de page d’AEM utilise des [composants principaux de Forms adaptatif](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr#features). Ces composants principaux fournissent des méthodes standard et plus simples de mise en forme et de personnalisation des composants, identiques aux [composants WCM d’AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).


## Comment créer ou ajouter un formulaire adaptatif dans une page AEM Sites ou un fragment d’expérience AEM ? {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Vous pouvez tirer pleinement parti de cette fonctionnalité en utilisant les options suivantes :

* **[Créer et ajouter un formulaire adaptatif personnalisé à une page AEM Sites](#create-an-adaptive-form-in-sites-editor-or-experience-fragment) :** vous pouvez utiliser le composant Conteneur de formulaires adaptatifs pour créer entièrement un formulaire, en l’adaptant spécifiquement à vos besoins et préférences de conception.

* **[Créer et ajouter un formulaire adaptatif personnalisé à un fragment d’expérience](#create-an-adaptive-form-in-sites-editor) :** vous pouvez étendre la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites.

* **[Convertir un formulaire adaptatif en fragment d’expérience](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment) :** convertissez un formulaire adaptatif ajouté à une page AEM Sites en un fragment d’expérience pour réutiliser le formulaire sur plusieurs pages AEM Sites.

* **[Créer et ajouter des formulaires basés sur des modèles approuvés à une page AEM Sites :](/help/forms/embed-adaptive-form-aem-sites.md#embed-form-using-adaptive-form-wizzard-aem-sites)** vous pouvez utiliser des modèles préapprouvés pour créer rapidement des Forms adaptatifs conformes aux directives de marque et aux normes de conception de votre entreprise. Cette option est disponible uniquement pour les formulaires adaptatifs créés avec l’éditeur de formulaires adaptatifs ou le composant Formulaires adaptatifs - Incorporer.

* **[Ajouter des formulaires existants à une page AEM Sites :](/help/forms/embed-adaptive-form-aem-sites.md#embed-an-adaptive-form-in-sites-editor)** vous pouvez facilement intégrer les formulaires que vous avez déjà créés dans vos sites web, ce qui permet aux visiteurs et visiteuses d’interagir directement avec eux. Cette option est disponible uniquement pour les formulaires adaptatifs créés avec l’éditeur de formulaires adaptatifs ou le composant Formulaires adaptatifs - Incorporer.


* **Ajouter plusieurs formulaires à une page AEM Sites ou à un fragment d’expérience :** vous pouvez créer ou ajouter plusieurs formulaires adaptatifs à une page AEM Sites afin de proposer plusieurs choix aux utilisateurs et utilisatrices en fonction de leurs préférences et de leurs besoins. Il peut s’agir d’une combinaison de formulaires entièrement nouveaux et de formulaires existants. Vous pouvez utiliser le composant **[!UICONTROL Conteneur de formulaires adaptatifs]** plusieurs fois pour ajouter un Forms adaptatif dans une page AEM Sites. Vous pouvez utiliser le composant **[!UICONTROL Forms adaptative - Incorporer]** plusieurs fois dans une page AEM Sites, uniquement si l’option **[!UICONTROL Le formulaire couvre toute la largeur du cadre]** est sélectionnée. Si l’option **[!UICONTROL Form couvre toute la largeur du cadre]** n’est pas cochée, la page AEM Sites ne prend en charge qu’un seul formulaire adaptatif pour exister sans iframe. Pour ajouter d’autres Forms adaptatives à l’aide du composant **[!UICONTROL Forms adaptatif - Incorporer]**, sélectionnez l’option **[!UICONTROL Le formulaire couvre toute la largeur du cadre]**.

## Remarques relatives à la création d’un formulaire adaptatif dans une page AEM Sites ou dans un fragment d’expérience AEM {#consideration}

* Lorsque vous utilisez le conteneur de formulaires adaptatifs pour créer ou ajouter un formulaire, les formulaires sont traduits et localisés par le biais du flux de traduction AEM Sites. Pour chaque langue, une copie distincte (copie de langue) de la page du site et des formulaires correspondants est générée. Lorsqu’un auteur ou une autrice de contenu modifie une règle dans un formulaire sur la page parente, les mêmes modifications doivent être effectuées dans toutes les copies de langue du formulaire. Le conteneur de formulaires adaptatifs vous permet également d’utiliser diverses fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et Multi-Site Manager.

* Lorsque vous créez ou ajoutez un formulaire à l’aide du composant Formulaire adaptatif - Incorporer, les formulaires sont traduits et localisés à l’aide du flux de traduction AEM Forms. Dans ce cas, un seul formulaire est conservé et référencé dans toutes les copies de langue des pages Sites. Le composant Formulaire adaptatif - Incorporer ne permet pas d’accéder aux différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et Multi-Site Manager.


## Conditions de création ou d’ajout d’un formulaire adaptatif dans une page AEM Sites ou un fragment d’expérience AEM {#before-you-start-creating-an-adaptive-form}

Avant de commencer à créer ou un formulaire adaptatif, ajoutez les bibliothèques clientes Forms adaptatives à votre page AEM Sites :


### Ajout de bibliothèques clientes de Forms adaptatif à une page ou une expérience AEM Sites

**Cas 1 : Utilisation de composants de page Sites distincts**

Pour activer la fonctionnalité complète du composant Conteneur de formulaires adaptatifs, ajoutez les bibliothèques clientes Customheaderlibs et Customfooterlibs à votre page AEM Sites à l’aide du pipeline de déploiement. Pour ajouter les bibliothèques :

1. Accédez à et clonez votre [référentiel Git AEM Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html?lang=fr).
1. Ouvrez le dossier Référentiel Git AEM Cloud Service dans un éditeur de texte brut. Par exemple, Microsoft Visual Code.
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

>[!NOTE]
>
> Codez en dur la bibliothèque cliente de fonction personnalisée uniquement lorsqu’elle est requise pour tous les formulaires. Pour les bibliothèques qui diffèrent en fonction du type de formulaire, ajoutez-les par le biais de politiques de page de modèle, comme expliqué dans la section suivante.

**2e cas : utiliser le même composant de page Sites**

Incluez les bibliothèques clientes d’exécution ou les bibliothèques de fonctions personnalisées dans la politique de page du modèle utilisé pour créer des pages avec des formulaires.

1. Ouvrez la page AEM Sites ou le fragment d’expérience pour modification. Pour ouvrir la page à modifier, sélectionnez-la, puis cliquez sur **[!UICONTROL Modifier]**.
2. Ouvrez le modèle de votre page Sites ou Fragment d’expérience. Pour ouvrir le modèle, accédez aux **[!UICONTROL Informations sur la page]** ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Modifier le modèle]**. Le modèle correspondant s’ouvre dans l’éditeur de modèles.
3. Dans la section **[!UICONTROL Informations sur la page]** ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) du modèle, sélectionnez l’option **[!UICONTROL Politique de page]**. Cette action ouvre les propriétés du modèle AEM Sites, dans lequel vous pouvez définir des fonctions personnalisées ou des bibliothèques clientes d’exécution.
4. Cliquez sur le bouton **[!UICONTROL Ajouter]** dans l’onglet **[!UICONTROL Propriétés]** pour ajouter de nouvelles bibliothèques de fonctions personnalisées ou les bibliothèques d’exécution.
5. Cliquez sur **[Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3476178?quality=12&learn=on)

### Activer le conteneur de formulaires adaptatifs pour votre page AEM Sites ou votre fragment d’expérience

Pour activer le composant [!UICONTROL Conteneur de formulaires adaptatifs] dans la politique du modèle, procédez comme suit :

1. Ouvrez la page AEM Sites ou le fragment d’expérience pour modification. Pour ouvrir la page à modifier, sélectionnez-la, puis cliquez sur Modifier.
1. Ouvrez le modèle de votre page Sites ou Fragment d’expérience. Pour ouvrir le modèle, accédez aux [!UICONTROL Informations sur la page] ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Modifier le modèle]. Le modèle correspondant s’ouvre dans l’éditeur de modèles.
1. Dans la vue Structure, cliquez sur l’icône **[!UICONTROL Politique]** ![Politique](/help/forms/assets/Smock_FeedManagement_18_N.svg) dans la barre de menus. Dans la liste **[!UICONTROL Composants autorisés]**, cochez la case **[!UICONTROL Conteneur de formulaires adaptatifs]** sous **[Nom du projet Archetype AEM] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

## Créer un formulaire adaptatif {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Vous pouvez créer un nouveau formulaire à partir de zéro, en l’adaptant spécifiquement à vos besoins et à vos préférences en matière de conception, directement dans une page AEM Sites ou dans un fragment d’expérience. Pour les formulaires à usage unique, il est recommandé d’effectuer une création directe sur une page AEM Sites, tandis que les fragments d’expérience sont parfaits pour les formulaires qui doivent être réutilisés sur plusieurs pages de votre site web.

* [Créer un formulaire dans une page AEM Sites](#create-an-adaptive-form-in-sites-editor)
* [Créer un formulaire dans un fragment d’expérience](#create-an-adaptive-form-in-experience-fragment)
* [Convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Créer un formulaire dans une page AEM Sites {#create-an-adaptive-form-in-sites-editor}

Vous pouvez utiliser le composant Conteneur de formulaires adaptatifs dans l’éditeur de page d’AEM pour créer un formulaire personnalisé. Le composant vous permet de créer un formulaire en faisant glisser et en déposant les composants du formulaire. Les composants de formulaire sont basés sur les composants principaux. Vous pouvez facilement les personnaliser en fonction des besoins de votre entreprise.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Pour créer un formulaire adaptatif dans une page Sites :

1. Ouvrez la page AEM Sites en mode d’édition.
1. Faites glisser et déposez le composant **[!UICONTROL Conteneur de formulaires adaptatifs]** du navigateur de composants vers la page Sites. Un espace est alors créé sur la page pour le formulaire. Vous pouvez modifier la taille de l’espace conteneur à l’aide du mode Disposition.
1. Faites glisser et déposez les composants principaux de formulaire adaptatif dans l’espace conteneur pour créer le formulaire.
1. Ajoutez le bouton Soumettre.

Ensuite, vous [définissez l’action Soumettre](#configure-submit-action-for-form) et les propriétés avancées.

### Créer un formulaire dans un fragment d’expérience {#create-an-adaptive-form-in-experience-fragment}

Vous pouvez étendre la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation directe sur plusieurs pages ou sites. Par exemple, vous pouvez inclure un formulaire d’inscription à une newsletter dans un fragment d’expérience. Vous pouvez ainsi réutiliser facilement le fragment sur plusieurs pages de votre site web, ce qui évite d’avoir à recréer le formulaire à plusieurs reprises. Toutes les mises à jour ou modifications apportées au formulaire d’inscription à la newsletter dans le fragment d’expérience sont automatiquement propagées à toutes les pages sur lesquelles elles sont utilisées. Cela simplifie le processus et garantit une expérience utilisateur fluide tout en simplifiant la gestion des formulaires de votre site web.

Pour créer un formulaire adaptatif dans un fragment d’expérience :

1. Ouvrez un fragment d’expérience.
1. Faites glisser et déposez le composant de **[!UICONTROL conteneur de formulaires adaptatifs]** du navigateur de composants sur le fragment d’expérience.
1. Faites glisser et déposez les composants principaux de formulaire adaptatif dans l’espace conteneur du fragment d’expérience pour créer le formulaire.
1. Ajoutez le bouton Soumettre.

Ensuite, vous [définissez l’action Soumettre](#configure-submit-action-for-form) et les propriétés avancées.

### Convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Vous pouvez convertir un formulaire adaptatif existant dans un éditeur de page d’AEM Sites en fragment d’expérience afin de réutiliser le formulaire sur plusieurs pages ou sites.

Pour convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience :

1. Ouvrez la page AEM Sites contenant le formulaire adaptatif (dans le composant de conteneur de formulaires adaptatifs) en mode d’édition.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.
1. Dans la barre de menus, sélectionnez l’icône ![ Convertir en fragment d’expérience ](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Convertir en variation de fragment d’expérience .
   ![Cliquez sur le logo de l’armoire à fichiers pour convertir un formulaire adaptatif dans la page AEM Sites en fragment d’expérience](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Une boîte de dialogue pour convertir le conteneur de formulaires adaptatifs en un nouveau fragment d’expérience ou l’ajouter à un fragment d’expérience existant s’affiche
1. Dans la boîte de dialogue Convertir en variation de fragment d’expérience, définissez les valeurs des options suivantes :

   * **Action :** vous pouvez sélectionner pour créer un fragment d’expérience ou ajouter à un fragment d’expérience existant.
   * **Chemin d’accès parent :** spécifiez le chemin du dossier dans lequel héberger le fragment d’expérience. Cette option est disponible uniquement pour créer un fragment d’expérience.
   * **Modèle :** spécifiez le chemin du modèle de fragment d’expérience. Si vous ne disposez pas d’un modèle de fragment d’expérience, [créez-le](/help/implementing/developing/extending/experience-fragments.md). Cette option est disponible uniquement pour l’ajout d’un formulaire adaptatif à un fragment d’expérience existant.
   * **Titre du fragment :** spécifiez le titre du fragment d’expérience. Le titre identifie de manière unique un fragment d’expérience


## Configurer l’action Soumettre pour un formulaire dans une page AEM Sites ou un fragment d’expérience {#configure-submit-action-for-form}

Une action Soumettre vous permet de choisir la destination des données capturées via un formulaire adaptatif. Elle est déclenchée lorsqu’un utilisateur ou une utilisatrice clique sur le bouton Soumettre d’un formulaire adaptatif. Les formulaires adaptatifs incluent certaines actions de soumission prêtes à l’emploi. Vous pouvez également étendre les actions de soumission par défaut pour créer votre propre action de soumission. Pour configurer une action de soumission pour votre formulaire :

1. Ouvrez l’éditeur de page AEM ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.
1. Cliquez sur l’icône de propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue du conteneur de formulaires adaptatifs pour configurer les actions de soumission s’ouvre.
   ![Cliquez sur l’icône Clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer l’action Envoyer pour un formulaire adaptatif](/help/forms/assets/adaptive-forms-container.png)
1. Sélectionnez et configurez une action de soumission en fonction de vos besoins. Pour plus d’informations sur les actions de soumission, voir [Action de soumission de formulaire adaptatif](/help/forms/configuring-submit-actions.md)


## Configurer un schéma ou un modèle de données de formulaire (FDM) pour un formulaire dans une page AEM Sites ou un fragment d’expérience {#configure-schema-or-data-model-for-form}

Vous pouvez utiliser le modèle de données de formulaire (FDM) pour connecter un formulaire à une Source de données afin d’envoyer et de recevoir des données en fonction des actions de l’utilisateur. Vous pouvez également connecter un formulaire à un schéma JSON pour recevoir les données envoyées dans un format prédéfini. Selon les besoins, connectez votre formulaire à un schéma JSON ou à un modèle de données de formulaire (FDM) :

* [Créez un schéma JSON et chargez-le dans votre environnement](/help/forms/adaptive-form-json-schema-form-model.md) ou,
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md)

Pour configurer un schéma JSON ou un modèle de données de formulaire (FDM) pour votre formulaire :

1. Ouvrez l’éditeur de page AEM ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.
1. Cliquez sur l’icône de propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
   ![Cliquez sur l’icône Clé à molette pour configurer des modèles de données pour le formulaire adaptatif](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. Sélectionnez et configurez un schéma JSON ou un modèle de données de formulaire (FDM) en fonction de vos besoins. Pour plus d’informations sur les actions de soumission, voir [Action de soumission de formulaire adaptatif](/help/forms/configuring-submit-actions.md).

   * Lorsque vous sélectionnez l’option **[!UICONTROL Modèle de formulaire]**, utilisez l’option **[!UICONTROL Sélectionner le modèle de données de formulaire]** pour sélectionner un modèle de données de formulaire (FDM) préconfiguré.
   * Lorsque vous sélectionnez l’option **[!UICONTROL Schéma]**, utilisez l’option **[!UICONTROL Schéma]** pour sélectionner un schéma JSON pour votre formulaire.

1. Cliquez sur **[!UICONTROL Terminé]**.

## Configurer un service de préremplissage pour un formulaire dans une page AEM Sites ou un fragment d’expérience {#configure-prefill-service-for-form}

Vous pouvez utiliser le service de préremplissage pour remplir automatiquement les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ou une utilisatrice ouvre un formulaire, les valeurs de ces champs sont préremplies. Vous pouvez effectuer les actions suivantes :

* [Créer un service de préremplissage personnalisé](/help/forms/prepopulate-adaptive-form-fields.md)
* [Utiliser le service de préremplissage de modèle de données de formulaire](#fdm-prefill-service)

### Utiliser le service de préremplissage de modèle de données de formulaire pour préremplir les champs d’un formulaire dans une page AEM Sites ou un fragment d’expérience {#fdm-prefill-service}

Vous pouvez utiliser le service de préremplissage de modèle de données de formulaire pour préremplir les champs d’un formulaire adaptatif dans une page AEM Sites ou un fragment d’expérience à l’aide d’un modèle de données de formulaire ou d’un service de préremplissage personnalisé. Le service de préremplissage de modèle de données de formulaire utilise la méthode [Obtenir le service du modèle de données de formulaire configuré](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) pour récupérer des données. Pour utiliser le service de préremplissage de modèle de données de formulaire pour un formulaire adaptatif :

1. Ouvrez l’éditeur de page AEM ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.
1. Cliquez sur l’icône de propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
   ![Cliquez sur l’icône Clé à molette pour ouvrir la boîte de dialogue Conteneur de formulaires adaptatifs afin de configurer le service de préremplissage du formulaire adaptatif](/help/forms/assets/adaptive-forms-container.png)
1. Sélectionnez un modèle de données de formulaire. Ouvrez l’onglet **[!UICONTROL De base]**. Dans le service de préremplissage, sélectionnez **[!UICONTROL Service de préremplissage de modèle de données de formulaire]**.
1. Cliquez sur **[!UICONTROL Terminé]**. Votre formulaire adaptatif est maintenant configuré pour utiliser le préremplissage du modèle de données de formulaire. Vous pouvez désormais utiliser l’[éditeur de règles](rule-editor.md) pour créer des règles afin de préremplir les champs du formulaire.


## Rediriger des personnes utilisatrices vers une page ou afficher un message de remerciement lors de la soumission du formulaire

Lors de la soumission d’un formulaire, vous pouvez rediriger la personne utilisatrice vers une autre page web ou un message. Pour rediriger la personne utilisatrice ou configurer le message de remerciement :

1. Ouvrez l’éditeur de page AEM ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez le **[!UICONTROL conteneur de formulaires adaptatifs]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs formulaires adaptatifs. Sélectionnez donc avec soin le conteneur de formulaires adaptatifs approprié.

1. Ouvrez l’onglet **[!UICONTROL Envoi]**.

   * Pour configurer une URL de redirection, pour l’option Lors de l’envoi, sélectionnez l’option **[!UICONTROL Rediriger vers l’URL]**, puis parcourez et sélectionnez une page AEM Sites, ou fournissez l’URL d’une page externe.
   * Pour configurer un message de remerciement ou personnalisé, sélectionnez l’option **[!UICONTROL Afficher le message]** et écrivez un message dans la zone **[!UICONTROL Contenu du message]** pour l’option Lors de l’envoi. Il s’agit d’une zone de texte enrichi. Vous pouvez utiliser l’option Plein écran pour afficher tous les éléments de texte enrichi disponibles.


