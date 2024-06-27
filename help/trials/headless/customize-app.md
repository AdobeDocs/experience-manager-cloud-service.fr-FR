---
title: Personnaliser du contenu dans un exemple d’application React
description: Utilisez un exemple d’application React pour découvrir comment personnaliser du contenu à l’aide de l’ensemble de fonctionnalités découplées dans AEM as a Cloud Service.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: ht
source-wordcount: '1017'
ht-degree: 100%

---


# Personnaliser du contenu dans un exemple d’application React {#customize-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="Personnaliser du contenu dans un exemple d’application React"
>abstract="Votre essai d’AEM découplé est intégré à un exemple d’application React que vous pouvez personnaliser."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="Lancer l’éditeur de fragment de contenu"
>abstract="Maintenant, découvrons comment fonctionne la création de contenu sans interface. Votre essai d’AEM découplé est intégré à un exemple d’application React. Vous pouvez ainsi voir à quel point il est facile pour n’importe qui de gérer le contenu indépendamment sans avoir à passer par le temps de développement.<br><br>Lancez ce module dans un nouvel onglet en cliquant ci-dessous, puis suivez ce guide."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="Dans ce module, vous avez appris à personnaliser un exemple d’application React.<br><br>Délai de mise sur le marché : accéléré !<br>Cycles de développement : réduits !<br><br>Vous comprenez maintenant à quel point la gestion du contenu découplé est facile pour les sites web et les applications gérés par les fonctionnalités découplées d’AEM."
>abstract=""

## Aperçu de l’application {#preview}

Commencez dans l’éditeur de fragment de contenu avec l’exemple d’application fourni avec votre essai d’AEM découplé déjà chargé. L’exemple d’application est optimisé par les fragments de contenu fournis via GraphQL. Utilisez l’éditeur de fragment de contenu pour vous familiariser avec l’éditeur en prévisualisant l’exemple d’application.

1. Appuyez ou cliquez sur le bouton **Aperçu** en haut à droite de l’écran de l’éditeur.

1. L’application de démonstration s’ouvre dans un nouvel onglet. L’application est pour la marque fictive de plein air WKND. Faites défiler la page vers le bas pour parcourir l’exemple de contenu.

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu pour continuer.

![Aperçu de l’application](assets/do-not-localize/preview-app-1.png)

## Modifier un en-tête dans l’application {#edit-app}

L’éditeur de fragment de contenu affiche la disposition de base de l’application sous la forme d’un fragment de contenu de page. Les **Panneaux** représentent différentes pages de l’application, chacune d’elles étant son propre fragment de contenu. En modifiant ces fragments, vous pouvez changer le contenu de l’application.

1. Appuyez ou cliquez sur **Mtn Biker in Canyon** dans la section **Panneaux**.

   ![Sélectionner le panneau de texte](assets/do-not-localize/edit-header-1.png)

1. L’éditeur ouvre le panneau d’en-tête de l’application pour le cycliste VTT. Chaque panneau est constitué de calques représentant différentes images et différents textes qui composent l’expérience.

1. Sélectionnez le calque de texte **Mtn Biker in Canyon Text Layer** pour ouvrir le détail du calque dans l’éditeur. Le calque est constitué de plusieurs fragments de contenu qui contrôlent le texte affiché dans ce panneau de l’application.

1. Sélectionnez l’élément de texte **Mtn Biker in Canyon Title**. L’éditeur de fragment de contenu s’ouvre, affichant le contenu de ce fragment et vous permettant de le modifier.

1. Remplacez le texte `Your next great adventure is calling` par `Choose your own adventure`. La modification est enregistrée automatiquement par l’éditeur.

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour voir vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet.

   ![Aperçu de l’application de démonstration](assets/do-not-localize/edit-header-5-6.png)

C’est aussi simple que cela de mettre à jour le contenu d’une application React lorsqu’elle est intégrée à un CMS AEM découplé.

## Changer une image dans l’application {#change-image}

Maintenant que vous avez modifié un titre dans l’application, essayez de changer une image.

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu à partir de l’aperçu.

1. Vous devez revenir au bon endroit dans l’éditeur de fragment de contenu. Les chemins de navigation situés en haut à gauche de l’éditeur indiquent où vous vous trouvez dans la hiérarchie du contenu. Sélectionnez **Mtn Biker in Canyon** dans le chemin de navigation pour revenir à cette page.

   ![Chemin de navigation](assets/do-not-localize/swap-image-2.png)

1. Sélectionnez le calque d’image **Mtn Biking - Biker**. L’éditeur de fragment de contenu s’ouvre alors.

1. Sélectionnez la variable **X** pour supprimer l’image du motard. L’image disparaît et l’éditeur affiche une erreur, car l’image est une donnée requise pour ce modèle de fragment de contenu.

   ![Supprimer une image du fragment](assets/do-not-localize/swap-image-4.png)

1. Sélectionner **Ajout d’une ressource** puis **Parcourir les ressources** dans le menu contextuel.

1. La boîte de dialogue **Sélectionner une ressource** s’ouvre et le chemin d’accès **sample-wknd-app** > **en** > **image-files** est automatiquement sélectionné.

1. Sélectionner l’image `biker-yellow.png` puis sélectionnez **Sélectionner**.

1. L’image du cycliste est remplacée par l’image sélectionnée. L’éditeur enregistre automatiquement les modifications.

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour voir vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet. Cliquez sur Actualiser dans le navigateur pour afficher votre nouvelle image du cycliste avec un short jaune dans l’application.

Mettez à jour facilement les images et les ressources de vos applications avec le CMS découplé d’AEM.

## Ajouter une référence à un nouveau fragment de contenu dans l’application {#create-moment}

Maintenant que vous avez mis à jour l’image du cycliste, nous allons découvrir comment ajouter du nouveau contenu à une application en créant et en référençant un nouveau fragment de contenu. Vous allez ajouter un appel de produit géré par un fragment de contenu « moment d’achat » au deuxième panneau de l’application.

![Exemple d’un moment d’achat](assets/do-not-localize/example-shoppable-moment.png)

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu depuis l’onglet Aperçu.

1. Vous devez revenir au bon endroit dans l’éditeur de fragments de contenu. Les chemins de navigation situés en haut à gauche de l’éditeur indiquent où vous vous trouvez dans la hiérarchie du contenu. Appuyez ou cliquez sur **Accueil WKND** dans les chemins de navigation pour revenir à cette page.

1. Sélectionnez le panneau **Mtn Biker on WKND Yellow**.

1. Sélectionnez le calque **Mtn Biking - Shoppable**.

1. Pour créer un nouvel appel à l’extérieur sur ce panneau, vous devez créer un fragment de contenu de moment d’achat. Sélectionnez la variable **+ Créer un fragment** bouton .

   ![Ajouter un moment d’achat](assets/do-not-localize/add-reference-1-5.png)

1. Vous devez d’abord choisir un modèle sur lequel baser le nouveau fragment de contenu. Sélectionnez le modèle **Article de moment d’achat** dans le menu déroulant **Modèle de fragment de contenu**.

1. Attribuez un nom au fragment de contenu. Par exemple, saisissez `Shorts` dans le champ **Nom**.

1. Sélectionner **Créer et ouvrir**.

   ![Attribuer un nom au moment d’achat](assets/do-not-localize/add-reference-6-7-8.png)

1. L’éditeur de votre nouveau fragment de contenu s’ouvre.

1. Attribuez un nom au moment d’achat dans le champ **Texte**, par exemple `Yellow shorts`.

1. Définissez les valeurs de **X** et **Y**. C’est à ce moment que cet appel doit être superposé sur le panneau. L’éditeur enregistre automatiquement les modifications du fragment.

   * **X** : `-5`
   * **Y** : `-10`

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour voir vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet. Cliquez sur Actualiser dans le navigateur pour tester le positionnement et effectuer les ajustements nécessaires dans l’éditeur.

   ![Aperçu](assets/do-not-localize/add-reference-10-11-12.png)

Vous savez à présent qu’il est possible de créer du contenu et le référencer en tant que fragment de contenu dans votre application sans cycles de développement.
