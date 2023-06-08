---
title: Création ou ajout d’un formulaire adaptatif à une page AEM Sites
description: Découvrez comment créer ou ajouter facilement un formulaire adaptatif à votre page AEM Sites sans effort. Découvrez les techniques et les bonnes pratiques étape par étape pour intégrer des formulaires dynamiques et personnalisables à votre site web, en optimisant vos expériences numériques pour un impact maximum.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 6b38601e9bd29c71e5f70b46d2fa55a928851adc
workflow-type: tm+mt
source-wordcount: '3182'
ht-degree: 1%

---


# Création ou ajout d’un formulaire adaptatif à une page AEM Sites {#create-or-add-an-adaptive-form-to-aem-sites-page}

Avec AEM Forms, vous pouvez facilement incorporer des formulaires adaptatifs dans vos pages web. Cela permet à vos visiteurs de remplir et d’envoyer facilement des formulaires sans jamais quitter la page sur laquelle ils se trouvent. Ce faisant, ils peuvent rester en contact sans effort avec d’autres éléments du site web tout en interagissant activement avec le formulaire.

Vous pouvez utiliser AEM éditeur de page pour créer et ajouter rapidement plusieurs formulaires à vos pages AEM Sites. L’utilisation de l’éditeur AEM Sites permet aux auteurs de contenu de créer des expériences de capture de données en toute transparence dans une page Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation des processus d’entreprise. Il vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

AEM Forms fournit des composants Adaptive Form Container (Conteneur de formulaires adaptatifs) et Adaptive Forms (Incorporer). Vous pouvez utiliser le conteneur de formulaires adaptatifs pour créer un formulaire dans un fragment d’expérience ou une page AEM Sites, tandis que le composant Forms adaptatif - Incorporer permet d’ajouter un formulaire adaptatif existant ou de créer un formulaire à l’aide de l’éditeur de Forms adaptatif.


![](/help/forms/assets/adaptive-form-in-sites-page.png)

## Avantages de l’utilisation du composant Conteneur de formulaires adaptatifs dans AEM éditeur de page ou dans le fragment d’expérience

L’utilisation du conteneur de formulaires adaptatifs dans AEM éditeur de page vous permet de créer des expériences de capture de données transparentes dans une page Sites à l’aide de la puissance des composants de Forms adaptatif, notamment le comportement dynamique, les validations, l’intégration de données, ainsi que de générer un document d’enregistrement et l’automatisation des processus d’entreprise. Il vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites, telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples, ce qui améliore l’expérience globale de création et de gestion de formulaires. Examinons quelques-unes de ces fonctionnalités :

* **Contrôle de version :** Offre de pages AEM Sites [fonctionnalités de contrôle de version fiables](/help/sites-cloud/authoring/features/page-versions.md), ce qui vous permet de suivre et de gérer différentes versions de vos formulaires. Vous pouvez ainsi apporter des modifications et des améliorations aux formulaires tout en conservant la possibilité de restaurer des versions précédentes si nécessaire. Le contrôle de version garantit une approche contrôlée et organisée du développement et de l’évolution des formulaires.
* **Ciblage (intégration à Adobe Target) :** Avec les fonctionnalités de ciblage des pages AEM Sites, vous pouvez également [personnaliser l’expérience du formulaire pour différentes audiences ;](/help/sites-cloud/integrating/integration-adobe-target-ims.md). En exploitant les segments d’utilisateurs et les critères de ciblage, vous pouvez personnaliser le contenu, la conception ou le comportement du formulaire en fonction de groupes d’utilisateurs spécifiques. Cela vous permet de fournir une expérience de formulaire personnalisée et pertinente, ce qui augmente l’engagement et les taux de conversion.
* **Traduction :** AEM Sites [intégration transparente avec les services de traduction](/help/sites-cloud/administering/translation/overview.md), ce qui vous permet de traduire facilement des formulaires en plusieurs langues. Cette fonctionnalité simplifie le processus de localisation, en veillant à ce que vos formulaires soient accessibles à une audience globale. Vous pouvez gérer efficacement les traductions dans AEM projets de traduction, ce qui réduit le temps et les efforts requis pour la prise en charge des formulaires multilingues. Pour plus d’informations sur la traduction, reportez-vous à la section Remarques .
* **Gestion multisite et Live Copy :** AEM Sites offre une fonctionnalité robuste [Fonctionnalités de gestion multisite et de Live Copy](/help/sites-cloud/administering/msm/overview.md), vous permettant de créer et de gérer plusieurs sites web au sein d’un seul environnement. Cette fonctionnalité vous permet désormais de réutiliser des formulaires sur différents sites, ce qui assure la cohérence et réduit les efforts de duplication. Grâce à un contrôle et une gestion centralisés, vous pouvez gérer et mettre à jour efficacement les formulaires sur plusieurs sites web.
* **Thèmes :** Les pages AEM Sites fournissent une structure pour la conception et la maintenance de styles visuels cohérents sur plusieurs pages web. Elles définissent les couleurs, les polices, les feuilles de style et d’autres éléments visuels qui contribuent à l’aspect général du site web. [Vous pouvez utiliser les thèmes conçus pour une page AEM Sites pour un formulaire adaptatif, ce qui vous permet de gagner du temps et de gagner des efforts.](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **Balisage :** Les pages AEM Sites vous permettent de [affecter des balises ou des étiquettes à une page, à une ressource ou à un autre contenu ;](/help/implementing/developing/introduction/tagging-framework.md). Les balises sont des mots-clés ou des étiquettes de métadonnées qui permettent de classer et d’organiser le contenu selon des critères spécifiques. Vous pouvez affecter une ou plusieurs balises aux pages, aux ressources ou à tout autre élément de contenu dans AEM afin d’améliorer la recherche et de classer les ressources.
* **Verrouillage et déverrouillage du contenu :** AEM Sites permet aux utilisateurs de [contrôler l’accès et les modifications aux pages ;](/help/sites-cloud/authoring/fundamentals/editing-content.md) dans l’environnement AEM Sites. Lorsqu’une page est verrouillée, cela signifie qu’elle est protégée contre les modifications ou modifications non autorisées par d’autres utilisateurs. Seul l’utilisateur qui a verrouillé le contenu ou un administrateur désigné peut le déverrouiller pour autoriser les modifications.


## Diverses options pour ajouter un formulaire adaptatif dans AEM éditeur de page

Vous pouvez tirer pleinement parti de cette fonctionnalité en utilisant les options suivantes :

* **Ajoutez un formulaire adaptatif personnalisé à une page AEM Sites :** Créez entièrement un nouveau formulaire, en le adaptant spécifiquement à vos besoins et préférences de conception.

* **Ajouter un formulaire adaptatif personnalisé à un fragment d’expérience :** Étendez la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites.

* **Ajouter plusieurs formulaires à une page AEM Sites ou à un fragment d’expérience :**  Ajoutez plusieurs formulaires à une page afin de proposer aux utilisateurs plusieurs choix en fonction de leurs préférences et de leurs besoins. Il peut s’agir d’une combinaison de formulaires entièrement nouveaux et de formulaires existants.

* **Convertir un formulaire adaptatif en fragment d’expérience :** Convertissez un formulaire adaptatif ajouté à une page AEM Sites en un fragment d’expérience pour réutiliser le formulaire sur plusieurs pages AEM Sites.

* **Créez et ajoutez des formulaires basés sur des modèles approuvés dans une page AEM Sites :** Tirez parti des modèles prévalidés pour créer rapidement des formulaires conformes aux directives de marque et aux normes de conception de votre entreprise. Cette option est disponible uniquement pour les Forms adaptatives créées avec l’éditeur de Forms adaptatif ou le composant Forms adaptatif - Incorporer .

* **Ajouter des formulaires existants à une page AEM Sites :** Intégrez facilement des formulaires que vous avez déjà créés dans vos sites web, ce qui permet aux visiteurs d’interagir directement avec eux. Cette option est disponible uniquement pour les Forms adaptatives créées avec l’éditeur de Forms adaptatif ou le composant Forms adaptatif - Incorporer .

Vous pouvez utiliser l’éditeur AEM Sites pour créer et ajouter rapidement plusieurs formulaires à vos pages AEM Sites. L’utilisation de l’éditeur AEM Sites permet aux auteurs de contenu de créer des expériences de capture de données en toute transparence dans une page Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation des processus d’entreprise. Il vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.


## Considérations {#consideration}

AEM Forms fournit des composants Adaptive Form Container (Conteneur de formulaires adaptatifs) et Adaptive Forms (Incorporer). Vous pouvez utiliser le conteneur de formulaires adaptatifs pour créer et ajouter un formulaire dans un fragment d’expérience ou une page AEM Sites, tandis que le composant Forms adaptatif - Incorporer permet d’ajouter un formulaire adaptatif existant ou de créer un formulaire à l’aide de l’éditeur de Forms adaptatif.

Lorsque vous utilisez le conteneur de formulaires adaptatifs pour créer ou ajouter un formulaire, les formulaires sont traduits et localisés par le biais du flux de traduction AEM Sites. Pour chaque langue, une copie distincte (copie de langue) de la page de sites et des formulaires correspondants est générée. Lorsqu’un auteur de contenu modifie une règle dans un formulaire sur la page parente, les mêmes modifications doivent être effectuées dans toutes les copies de langue du formulaire. Le conteneur de formulaires adaptatifs vous permet également d’utiliser diverses fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

Lorsque vous créez ou ajoutez un formulaire à l’aide du composant d’intégration de formulaire adaptatif, les formulaires sont traduits et localisés à l’aide du flux de traduction AEM Forms. Dans ce cas, un seul formulaire est conservé et référencé dans toutes les copies de langue des pages Sites. Le composant d’intégration de formulaire adaptatif ne permet pas d’accéder aux différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.


## Avant de commencer {#before-you-start}

+++  Activation des composants principaux de Forms adaptatif pour votre environnement

Assurez-vous que la variable [Les composants principaux Forms adaptatifs sont activés pour votre environnement as a Cloud Service AEM Forms](enable-adaptive-forms-core-components.md).

+++

+++  Ajout de bibliothèques clientes Forms adaptatives à la page AEM Sites et aux composants de page Fragment d’expérience

Pour activer la fonctionnalité complète du composant Conteneur de Forms adaptatif, ajoutez les bibliothèques clientes Customheaderlibs et Customfooterlibs à votre page AEM Sites à l’aide du pipeline de déploiement. Pour ajouter les bibliothèques :

1. Accédez à et clonez vos [Référentiel AEM Cloud Service Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Ouvrez le dossier Référentiel Git AEM Cloud Service dans un éditeur de texte de plan. Par exemple, le code visuel de Microsoft.
1. Ouvrez le `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` et ajoutez le code suivant au fichier :

       &quot;
       //Customheaderlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;}&quot; />
       &lt;/sly>
       
       &quot;
   
1. Ouvrez le `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` et ajoutez le code suivant au fichier :

       &quot;
       
       //customfooterlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;, async=true}&quot; />
       &lt;/sly>
       &quot;
   
1. Ouvrez le `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` et ajoutez le code suivant au fichier :

       &quot;
       //Customheaderlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;}&quot; />
       &lt;/sly>
       
       &quot;
   
1. Ouvrez le `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` et ajoutez le code suivant au fichier :

       &quot;
       
       //customfooterlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;, async=true}&quot; />
       &lt;/sly>
       &quot;
   
1. [Exécution du pipeline de déploiement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) pour déployer les bibliothèques clientes dans votre environnement as a Cloud Service AEM.

+++

+++ Activer **[!UICONTROL Conteneur Forms adaptatif]

Pour activer [!UICONTROL Conteneur Forms adaptatif] dans la stratégie du modèle, procédez comme suit :

1. Ouvrez la page AEM Sites ou le fragment d’expérience à modifier. Pour ouvrir la page à modifier, sélectionnez-la, puis cliquez sur Modifier.
1. Ouvrez le modèle de votre page Sites ou Fragment d’expérience . Pour ouvrir le modèle, accédez au [!UICONTROL Informations sur la page] ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Modifier le modèle]. Il ouvre le modèle correspondant dans l’éditeur de modèles.
1. Dans la vue Structure, cliquez sur le **[!UICONTROL Stratégie]** ![Stratégie](/help/forms/assets/Smock_FeedManagement_18_N.svg) dans la barre de menus. Dans le **[!UICONTROL Composants autorisés]** et sélectionnez la variable **[!UICONTROL Conteneur Forms adaptatif]**  sous la case **[Nom du projet AEM Archetype] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Créer un formulaire adaptatif {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Vous pouvez créer entièrement un nouveau formulaire, en le adaptant spécifiquement à vos besoins et à vos préférences de conception, directement dans une page de sites AEM ou dans un fragment d’expérience. Pour les formulaires à usage unique, il est recommandé d’effectuer une création directe sur une page de sites AEM, tandis que les fragments d’expérience sont idéaux pour les formulaires qui doivent être réutilisés sur plusieurs pages de votre site web.

* [Création d’un formulaire dans une page AEM Sites](#create-an-adaptive-form-in-sites-editor)
* [Création d’un formulaire dans un fragment d’expérience](#create-an-adaptive-form-in-experience-fragment)

### Création d’un formulaire dans une page AEM Sites {#create-an-adaptive-form-in-sites-editor}

Vous pouvez utiliser le composant Conteneur de formulaires adaptatifs dans l’éditeur AEM Sites pour créer un formulaire personnalisé. Le composant vous permet de créer un formulaire en le faisant glisser et en le déposant. Les composants de formulaire sont basés sur les composants principaux. Vous pouvez facilement les personnaliser en fonction des besoins de votre entreprise.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Pour créer un formulaire adaptatif dans une page Sites :

1. Ouvrez la page AEM Sites en mode d’édition.
1. Faites glisser et déposez le **[!UICONTROL Conteneur Forms adaptatif]** du navigateur de composants vers la page Sites. Un espace est alors créé sur la page pour le formulaire. Vous pouvez modifier la taille de l’espace conteneur à l’aide du mode Mise en page.
1. Faites glisser et déposez les composants principaux de formulaire adaptatif dans l’espace conteneur pour créer le formulaire.
1. Ajoutez le bouton Envoyer .

Ensuite, vous [Définition de l’action Envoyer](#configure-submit-action-for-form) et propriétés avancées.

### Création d’un formulaire dans un fragment d’expérience {#create-an-adaptive-form-in-experience-fragment}

Vous pouvez étendre la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites. Par exemple, vous pouvez inclure un formulaire d’inscription à une newsletter dans un fragment d’expérience. Vous pouvez ainsi réutiliser facilement le fragment sur plusieurs pages de votre site web, ce qui évite d’avoir à recréer le formulaire à plusieurs reprises. Toutes les mises à jour ou modifications apportées au formulaire d’inscription à la newsletter dans le fragment d’expérience sont automatiquement propagées à toutes les pages sur lesquelles elles sont utilisées. Cela simplifie le processus et garantit une expérience utilisateur transparente tout en simplifiant la gestion des formulaires de votre site web.

Pour créer un formulaire adaptatif dans un fragment d’expérience :

1. Ouvrez un fragment d’expérience.
1. Faites glisser et déposez le **[!UICONTROL Conteneur Forms adaptatif]** du navigateur de composants au fragment d’expérience.
1. Faites glisser et déposez les composants principaux de formulaire adaptatif dans l’espace conteneur du fragment d’expérience pour créer le formulaire.
1. Ajoutez le bouton Envoyer .

Ensuite, vous [Définition de l’action Envoyer](#configure-submit-action-for-form) et propriétés avancées.

### Convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience

Vous pouvez convertir un formulaire adaptatif existant dans un éditeur de page de sites en fragment d’expérience afin de réutiliser le formulaire sur plusieurs pages ou sites.

Pour convertir un formulaire adaptatif dans une page AEM Sites en fragment d’expérience :

1. Ouvrez la page AEM Sites contenant le formulaire adaptatif (dans le composant Conteneur de Forms adaptatif) en mode d’édition.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Dans la barre de menus, sélectionnez l’option ![Icône Convertir en variation de fragment d’expérience](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Icône de variation Convertir en fragment d’expérience .
   ![](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Une boîte de dialogue pour convertir le conteneur de formulaires adaptatifs en un nouveau fragment d’expérience ou l’ajouter à un fragment d’expérience existant s’affiche.
1. Dans la boîte de dialogue Convertir en variation de fragment d’expérience , définissez les valeurs des options suivantes :

   * **Action :** Sélectionnez pour créer un fragment d’expérience ou Ajouter à un fragment d’expérience existant.
   * **Chemin d’accès parent :** Spécifiez le chemin du dossier dans lequel héberger le fragment d’expérience. Cette option est disponible uniquement pour créer un fragment d’expérience.
   * **Modèle :** Spécifiez le chemin du modèle de fragment d’expérience. Si vous ne disposez pas d’un modèle de fragment d’expérience, [créer](/help/implementing/developing/extending/experience-fragments.md). Cette option est disponible uniquement pour l’ajout d’un formulaire adaptatif à un fragment d’expérience existant.
   * **Titre du fragment :** Spécifiez le titre du fragment d’expérience. Le titre identifie de manière unique un fragment d’expérience.


## Configuration de l’action Envoyer pour le formulaire {#configure-submit-action-for-form}

Une action Envoyer vous permet de choisir la destination des données capturées via un formulaire adaptatif. Elle est déclenchée lorsqu’un utilisateur clique sur le bouton Envoyer d’un formulaire adaptatif. Les formulaires adaptatifs incluent certaines actions d’envoi prêtes à l’emploi. Vous pouvez également étendre une action d’envoi par défaut pour créer votre propre action d’envoi personnalisée. Pour configurer une action Envoyer pour votre formulaire :

1. Ouvrez l’éditeur de page AEM Sites ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Cliquez sur les propriétés du conteneur de formulaires adaptatifs . ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) icône . La boîte de dialogue Conteneur de formulaires adaptatifs s’ouvre pour configurer les actions d’envoi.
   ![](/help/forms/assets/adaptive-forms-container.png)
1. Sélectionnez et configurez une action Envoyer en fonction de vos besoins. Pour plus d’informations sur les actions d’envoi, voir [Action d’envoi de formulaire adaptatif](/help/forms/configuring-submit-actions.md)


## Configuration d’un schéma ou d’un modèle de données de formulaire pour un formulaire {#configure-schema-or-data-model-for-form}

Vous pouvez utiliser le modèle de données de formulaire pour connecter un formulaire à une source de données afin d’envoyer et de recevoir des données en fonction des actions de l’utilisateur. Vous pouvez également connecter un formulaire à un schéma JSON pour recevoir les données envoyées dans un format prédéfini.

Avant de connecter un formulaire à un schéma ou à un modèle de données de formulaire

* [Création d’un schéma JSON et chargement dans votre environnement](/help/forms/adaptive-form-json-schema-form-model.md)
* [Création d’un modèle de données de formulaire](/help/forms/create-form-data-models.md)

Pour configurer un schéma JSON ou un modèle de données de formulaire pour votre formulaire :

1. Ouvrez l’éditeur de page AEM Sites ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Cliquez sur les propriétés du conteneur de formulaires adaptatifs . ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) icône . La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
   ![](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. Sélectionnez et configurez un schéma JSON ou un modèle de données de formulaire, en fonction de vos besoins. Pour plus d’informations sur les actions d’envoi, voir [Action d’envoi de formulaire adaptatif](/help/forms/configuring-submit-actions.md).

   * Lorsque vous sélectionnez la variable **[!UICONTROL Modèle de formulaire]** , utilisez l’option **[!UICONTROL Sélectionner un modèle de données de formulaire]** pour sélectionner un modèle de données de formulaire préconfiguré.
   * Lorsque vous sélectionnez la variable **[!UICONTROL Schéma]** , utilisez l’option **[!UICONTROL Schéma]** pour sélectionner un schéma JSON pour votre formulaire.

1. Cliquez sur **[!UICONTROL Terminé]**.

## Configuration d’un service de préremplissage pour un formulaire {#configure-prefill-service-for-form}

Vous pouvez utiliser le service de préremplissage pour remplir automatiquement les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ouvre un formulaire, les valeurs de ces champs sont préremplies. Vous pouvez :

* [Création d’un service de préremplissage personnalisé](/help/forms/prepopulate-adaptive-form-fields.md)
* [Utilisation du service de préremplissage de modèle de données de formulaire](#fdm-prefill-service)
* Utilisation du service de préremplissage de brouillon du portail Forms

### Utilisation du service de préremplissage de modèle de données de formulaire {#fdm-prefill-service}

Vous pouvez utiliser le service de préremplissage de modèle de données de formulaire pour préremplir les champs d’un formulaire à l’aide d’un modèle de données de formulaire configuré. Le service Form Data Model Prefill utilise la méthode [Obtention du service du modèle de données de formulaire configuré](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) pour récupérer des données. Pour utiliser le service de préremplissage de modèle de données de formulaire pour un formulaire adaptatif :

1. Ouvrez l’éditeur de page AEM Sites ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Cliquez sur les propriétés du conteneur de formulaires adaptatifs . ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) icône . La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
   ![](/help/forms/assets/adaptive-forms-container.png)
1. Sélectionner un modèle de données de formulaire. Ouvrez le **[!UICONTROL De base]** . Dans le service de préremplissage, sélectionnez **[!UICONTROL Service de préremplissage du brouillon du portail Forms]**.
   ![](/help/forms/assets/prefill-service-fdm-aem-sites-page-editor.png)

1. Cliquez sur **[!UICONTROL Terminé]**.

### Utilisation du service de préremplissage de brouillon du portail Forms {#forms-portal-prefill-service}

Vous pouvez utiliser le service de préremplissage de brouillon du portail Forms pour préremplir les champs d’un formulaire à l’aide d’un brouillon du formulaire adaptatif enregistré. Avant d’utiliser le service de préremplissage de brouillon du portail Forms, assurez-vous que [Les composants du portail Forms adaptatif sont activés et configurés. ](configure-forms-portal.md#configure-azure-storage-for-adaptive-forms-configure-azure-storage-adaptive-forms) pour votre environnement.

1. Ouvrez l’éditeur de page AEM Sites ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez les propriétés de la page et configurez la configuration du cloud.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Cliquez sur les propriétés du conteneur de formulaires adaptatifs . ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) icône . La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
1. Ouvrez le **[!UICONTROL De base]** . Dans le service de préremplissage, sélectionnez **[!UICONTROL Service de préremplissage du brouillon du portail Forms]**.
   ![](/help/forms/assets/prefill-service-aem-sites-page-editor.png)

1. Cliquez sur **[!UICONTROL Terminé]**.


## Rediriger l’utilisateur vers un nouvel utilisateur lors de l’envoi du formulaire ou afficher un message de remerciement

Lors de l’envoi d’un formulaire, vous pouvez rediriger l’utilisateur vers une autre page web ou un message. Pour rediriger l’utilisateur ou configurer le message de remerciement :

1. Ouvrez l’éditeur de page AEM Sites ou le fragment d’expérience contenant le formulaire adaptatif.
1. Ouvrez l’arborescence de contenu, puis sélectionnez l’option **[!UICONTROL Conteneur Forms adaptatif]** qui héberge votre formulaire adaptatif. Une page AEM Sites peut héberger plusieurs Forms adaptatifs. Sélectionnez donc avec soin le conteneur de Forms adaptatif approprié.
1. Cliquez sur les propriétés du conteneur de formulaires adaptatifs . ![Propriétés Adaptive Form Container](/help/forms/assets/configure-icon.svg) icône . La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
1. Ouvrez le **[!UICONTROL Envoi]** .

   * Pour configurer une URL de redirection, pour l’option Lors de l’envoi, sélectionnez l’option Rediriger vers l’URL et indiquez une adresse absolue, une URL de redirection ou le chemin relatif d’une page AEM Sites.

   * Pour configurer un message de remerciement ou personnalisé, sélectionnez l’option Afficher le message dans le champ Contenu du message pour l’option Envoyer. Il s’agit d’une zone de texte enrichi. Vous pouvez utiliser l’option Plein écran pour afficher tous les éléments de texte enrichi disponibles.


## Suivant

* [Donner un style à votre Forms adaptatif basé sur les composants principaux](using-themes-in-core-components.md)
* [Utilisation de l’éditeur de règles pour ajouter un comportement dynamique à Forms adaptatif](rule-editor.md)
* [Modification de la mise en page d’un formulaire adaptatif](/help/sites-cloud/authoring/features/responsive-layout.md)

