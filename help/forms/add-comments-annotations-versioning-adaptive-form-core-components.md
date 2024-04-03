---
title: Ajoutez des versions, des commentaires et des annotations à un formulaire.
description: Utilisez les composants principaux de formulaire adaptatif pour ajouter des commentaires, des annotations et des versions à un formulaire adaptatif.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Adaptive Forms, Core Components
hidefromtoc: true
source-git-commit: 4e60d7315fe7a92d608f0858a7108f7590e9aefa
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# Contrôle de version, révision et commentaires sur un formulaire adaptatif

<!--Before you can use versionings, comments, and annotations in an Adaptive Form, you must ensure you have [enabled Adaptive Form Core Components](
https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components).-->

<!--Adaptive Form Core Components facilitates to add versionings, comments, and annotations to a form. These features helps form authors and users to enhance the form development process where they can create multiple versions of a form, collaborate and add their comments to a form, and add annotations to form components.-->

<span class="preview"> Il s’agit d’une fonctionnalité de préversion accessible via notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>


Les composants principaux de formulaire adaptatif offrent une fonctionnalité qui permet aux auteurs de formulaires d’incorporer des fonctions de contrôle de version, de commentaires et d’annotations dans les formulaires. Ces fonctionnalités permettent de rationaliser le processus de développement de formulaire en permettant aux utilisateurs de créer et gérer plusieurs versions d’un formulaire, d’engager des discussions collaboratives par le biais de commentaires et d’associer des annotations à des composants de formulaire spécifiques, améliorant ainsi l’expérience globale de création de formulaire.


## Contrôle de version des formulaires adaptatifs {#adaptive-form-versioning}

Le contrôle de version de formulaire adaptatif permet d’ajouter des versions à un formulaire. Les auteurs de formulaires peuvent facilement créer plusieurs versions d’un formulaire et enfin utiliser celle qui convient aux objectifs de l’entreprise. En outre, les utilisateurs de formulaires peuvent également rétablir les versions précédentes du formulaire. Cela permet également aux auteurs de comparer deux versions d’un formulaire en les prévisualisant, ce qui leur permet d’analyser les formulaires mieux du point de vue de l’interface utilisateur. Allons plus en détail pour chaque fonctionnalité de contrôle de version de formulaire adaptatif :

### Création d’une version de formulaire {#create-a-form-version}

Pour créer une version d’un formulaire, procédez comme suit :

1. Créez un formulaire ou utilisez un formulaire existant.
1. Dans l’interface utilisateur d’AEM, accédez au **[!UICONTROL Formulaire]**&quot;**[!UICONTROL Forms et documents]** et sélectionnez votre **Formulaire**.
1. Dans la liste déroulante de sélection du panneau de gauche, sélectionnez **[!UICONTROL Versions]**.
   ![Sélection d’un formulaire](select-a-form.png)
1. Cliquez sur le bouton **trois points** situé dans le panneau inférieur gauche, cliquez sur **[!UICONTROL Enregistrer comme version]**.
1. Maintenant, fournissez un libellé à la version du formulaire et vous pouvez fournir des informations sur le formulaire par le biais du commentaire.
   ![Création d’une version de formulaire](create-a-form-version.png)

### Mettre à jour une version de formulaire {#update-a-form-version}

Lorsque vous modifiez et mettez à jour votre formulaire adaptatif, vous ajoutez une nouvelle version au formulaire. Suivez les étapes de la dernière section pour nommer une nouvelle version du formulaire, comme illustré dans l’image :

![Mettre à jour une version de formulaire](update-a-form-version.png)

### Rétablissement d’une version de formulaire {#revert-a-form-version}

Pour rétablir la version précédente d’un formulaire, sélectionnez une version, puis cliquez sur **[!UICONTROL Revenir à cette version]**.

![Rétablir la version de formulaire](revert-form-version.png)

### Comparaison des versions de formulaire {#compare-form-versions}

Les auteurs de formulaires peuvent comparer deux versions différentes d’un formulaire à des fins d’aperçu. Pour comparer des versions, sélectionnez une version de formulaire, puis cliquez sur **[!UICONTROL Comparer à actuel]**. Il affiche deux versions de formulaire différentes en mode d’aperçu.

![Comparaison des versions de formulaire](compare-form-versions.png)

## Ajouter des commentaires {#add-comments}

Une révision est un mécanisme qui permet à un ou plusieurs réviseurs de commenter des formulaires. Tout utilisateur de formulaire peut commenter un formulaire ou le réviser au moyen de commentaires. Pour ajouter des commentaires à un formulaire, sélectionnez une **[!UICONTROL Formulaire]**, puis ajoutez une **[!UICONTROL Commentaire]** au formulaire.

>[!NOTE]
> Lorsque vous utilisez des commentaires dans les composants principaux de formulaire adaptatif comme décrit ci-dessus, la fonctionnalité de formulaire [Création et gestion de révisions des formulaires](/help/forms/create-reviews-forms.md) est désactivée.


![Ajouter des commentaires sur un formulaire](form-comments.png)

## Ajout d’annotations {#adaptive-form-annotations}

Dans de nombreux cas, les utilisateurs d’un groupe de formulaires doivent ajouter des annotations à un formulaire à des fins de révision, par exemple, sur un onglet spécifique d’un formulaire ou de composants d’un formulaire. Dans ce cas, les auteurs peuvent utiliser des annotations. Pour ajouter des annotations à un formulaire, procédez comme suit :

1. Ouvrez un formulaire dans le **[!UICONTROL Modifier]** mode .

1. Cliquez sur le bouton **icône ajouter** situé sur le rail supérieur droit, comme indiqué dans l’image.
   ![Annotation](annotation.png)

1. Cliquez sur le bouton **icône ajouter** situé sur le rail supérieur gauche comme indiqué dans l’image à ajouter à la notation.
   ![Ajouter une annotation](add-annotation.png)

1. Vous pouvez maintenant ajouter des commentaires, dessiner des esquisses de plusieurs couleurs pour former des composants.

1. Pour afficher toutes les annotations ajoutées à un formulaire, sélectionnez le formulaire. Les annotations ajoutées dans le panneau de gauche sont alors visibles dans l’image.

   ![Voir les annotations ajoutées](see-annotations.png)











