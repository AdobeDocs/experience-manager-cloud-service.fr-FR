---
title: Création ou ajout d’un formulaire adaptatif à une page AEM Sites
description: Découvrez comment créer ou ajouter facilement un formulaire adaptatif à votre page AEM Sites sans effort. Découvrez les techniques et les bonnes pratiques étape par étape pour intégrer des formulaires dynamiques et personnalisables à votre site web, en optimisant vos expériences numériques pour un impact maximum.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 7dc36220c1f12177037aaa79d864c1ec2209a301
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Création ou ajout d’un formulaire adaptatif à une page AEM Sites {#create-or-add-an-adaptive-form-to-aem-sites-page}

Avec AEM Forms, vous pouvez facilement incorporer des formulaires adaptatifs dans vos pages web. Cela permet à vos visiteurs de remplir et d’envoyer facilement des formulaires sans jamais quitter la page sur laquelle ils se trouvent. Ce faisant, ils peuvent rester en contact sans effort avec d’autres éléments du site web tout en interagissant activement avec le formulaire.

Vous pouvez tirer pleinement parti de cette fonctionnalité en utilisant les options suivantes :

* **Ajoutez un formulaire personnalisé :** Créez entièrement un nouveau formulaire, en le adaptant spécifiquement à vos besoins et préférences de conception.

* **Amélioration des fragments d’expérience :** Étendez la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites.

* **Utiliser les modèles validés :** Tirez parti des modèles prévalidés pour créer rapidement des formulaires conformes aux directives de marque et aux normes de conception de votre entreprise.

* **Ajouter des formulaires existants :** Intégrez facilement des formulaires que vous avez déjà créés dans vos sites web, ce qui permet aux visiteurs d’interagir directement avec eux.

* **Ajouter plusieurs formulaires :**  Ajoutez plusieurs formulaires à une page afin de proposer aux utilisateurs plusieurs choix en fonction de leurs préférences et de leurs besoins. Il peut s’agir d’une combinaison de formulaires entièrement nouveaux et de formulaires existants.

Vous pouvez utiliser l’éditeur AEM Sites pour créer et ajouter rapidement plusieurs formulaires à vos pages AEM Sites. L’utilisation de l’éditeur AEM Sites permet aux auteurs de contenu de créer des expériences de capture de données en toute transparence dans une page Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation des processus d’entreprise. Il vous permet également d’utiliser différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

## Objectif

* Découvrez comment créer un formulaire adaptatif à l’aide de l’éditeur AEM Sites et du fragment d’expérience
* Découvrez comment définir la mise en page et le thème d’un formulaire adaptatif ajouté à une page AEM Sites et
* Création d’un formulaire adaptatif à l’aide de l’éditeur AEM Sites et du fragment d’expérience


## Considérations {#consideration}

AEM Forms fournit des composants Adaptive Form Container (Conteneur de formulaires adaptatifs) et Adaptive Forms (Incorporer). Vous pouvez utiliser le conteneur de formulaires adaptatifs pour créer et ajouter un formulaire dans un fragment d’expérience ou une page AEM Sites, tandis que le composant Forms adaptatif - Incorporer permet d’ajouter un formulaire adaptatif existant ou de créer un formulaire à l’aide de l’éditeur de Forms adaptatif.

Lorsque vous utilisez le conteneur de formulaires adaptatifs pour créer ou ajouter un formulaire, les formulaires sont traduits et localisés par le biais du flux de traduction AEM Sites. Pour chaque langue, une copie distincte (copie de langue) de la page de sites et des formulaires correspondants est générée. Lorsqu’un auteur de contenu modifie une règle dans un formulaire sur la page parente, les mêmes modifications doivent être effectuées dans toutes les copies de langue du formulaire. Le conteneur de formulaires adaptatifs vous permet également d’utiliser diverses fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.

Lorsque vous créez ou ajoutez un formulaire à l’aide du composant d’intégration de formulaire adaptatif, les formulaires sont traduits et localisés à l’aide du flux de traduction AEM Forms. Dans ce cas, un seul formulaire est conservé et référencé dans toutes les copies de langue des pages Sites. Le composant d’intégration de formulaire adaptatif ne permet pas d’accéder aux différentes fonctionnalités des pages AEM Sites telles que le contrôle de version, le ciblage, la traduction et le gestionnaire de sites multiples.


## Avant de commencer {#before-you-start}

+++  Activation des composants principaux de Forms adaptatif pour votre environnement

Assurez-vous que la variable [Les composants principaux Forms adaptatifs sont activés pour votre environnement as a Cloud Service AEM Forms](enable-adaptive-forms-core-components.md).

+++

+++ Activer **[!UICONTROL Conteneur Forms adaptatif]

Pour activer [!UICONTROL Conteneur Forms adaptatif] dans la stratégie du modèle, procédez comme suit :

1. Ouvrez la page AEM Sites pour modification. Pour ouvrir la page à modifier, sélectionnez-la, puis cliquez sur Modifier.
1. Ouvrez le modèle de votre page Sites. Pour ouvrir le modèle, accédez au [!UICONTROL Informations sur la page] ![Informations sur la page](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Modifier le modèle]. Il ouvre le modèle correspondant dans l’éditeur de modèles.
1. Dans la vue Structure, cliquez sur le **[!UICONTROL Stratégie]** ![Stratégie](/help/forms/assets/Smock_FeedManagement_18_N.svg) dans la barre de menus. Dans le **[!UICONTROL Composants autorisés]** et sélectionnez la variable **[!UICONTROL Conteneur Forms adaptatif]**  sous la case **[Nom du projet AEM Archetype] - Formulaire adaptatif**.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++


+++  Ajout de bibliothèques clientes Forms adaptatives à votre page AEM Sites

Pour activer la fonctionnalité complète du composant Conteneur de Forms adaptatif, ajoutez les bibliothèques clientes Customheaderlibs et Customfooterlibs à votre page AEM Sites à l’aide du pipeline de déploiement. Pour ajouter les bibliothèques :

1. Accédez à et clonez vos [Référentiel AEM Cloud Service Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Ouvrez le dossier Référentiel Git AEM Cloud Service dans un éditeur de texte de plan. Par exemple, le code visuel de Microsoft.
1. Ouvrez le `ui.apps/src/main/content/jcr_root/apps/[your-project]/components/page/.content.xml` pour modifier et notez la valeur de `sling:resourceSuperType`. Par exemple, notez la valeur `core/wcm/components/page/v3/page`.


   ![ressource sling](/help/forms/assets/slingresource.png)

1. Accédez à `  ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\` `ui.apps/src/main/content/jcr_root/apps` et créer une structure de dossiers identique à la valeur indiquée à l’étape précédente. Par exemple, si la valeur est similaire à l’exemple de l’étape précédente, la structure de noeud finale est `ui.apps/src/main/content/jcr_root/apps/core/wcm/components/page/v3/page`

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png)

1. Créer `customheaderlibs.html` et `customfooterlibs.html` fichiers à la structure de noeud créée à l’étape précédente et ajoutez le contenu suivant aux fichiers :

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

1. [Exécution du pipeline de déploiement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) pour déployer les bibliothèques clientes dans votre environnement as a Cloud Service AEM.

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

Vous définissez ensuite l’action Envoyer et les propriétés avancées.

### Création d’un formulaire dans un fragment d’expérience {#create-an-adaptive-form-in-experience-fragment}

Vous pouvez étendre la portée de vos formulaires en les ajoutant aux fragments d’expérience AEM, ce qui permet une réutilisation transparente sur plusieurs pages ou sites. Par exemple, vous pouvez inclure un formulaire d’inscription à une newsletter dans un fragment d’expérience. Vous pouvez ainsi réutiliser facilement le fragment sur plusieurs pages de votre site web, ce qui évite d’avoir à recréer le formulaire à plusieurs reprises. Toutes les mises à jour ou modifications apportées au formulaire d’inscription à la newsletter dans le fragment d’expérience sont automatiquement propagées à toutes les pages sur lesquelles elles sont utilisées. Cela simplifie le processus et garantit une expérience utilisateur transparente tout en simplifiant la gestion des formulaires de votre site web.

Pour créer un formulaire adaptatif dans un fragment d’expérience :

## Modification de la mise en page d’un formulaire adaptatif {#change-layout-of-an-adaptive-form}

Dans la page AEM Sites, utilisez la méthode [Mode Mise en page](/help/sites-cloud/authoring/features/responsive-layout.md) pour redimensionner un composant Conteneur de formulaires adaptatifs ajouté à une page AEM Sites.
