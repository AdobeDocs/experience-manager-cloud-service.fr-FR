---
title: Personnalisation du contenu d’un exemple d’application React
description: Utilisez un exemple d’application React pour savoir comment personnaliser du contenu à l’aide de l’ensemble de fonctionnalités sans interface utilisateur dans AEM as a Cloud Service.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---


# Personnalisation du contenu d’un exemple d’application React {#customize-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="Personnalisation du contenu dans un exemple d’application React"
>abstract="Votre essai AEM sans interface est intégré à un exemple d’application React que vous pouvez personnaliser."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="Lancement de l’éditeur de fragment de contenu"
>abstract="Votre essai AEM sans interface est intégré à un exemple d’application React. Vous pouvez ainsi voir à quel point il est facile pour n’importe qui de gérer le contenu indépendamment sans avoir à passer par le temps de développement.<br><br>Lancez ce module dans un nouvel onglet en cliquant ci-dessous, puis suivez ce guide."
>additional-url="https://video.tv.adobe.com/v/328618" text="Vidéo Personnaliser l’introduction de l’application"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="Dans ce module, vous avez appris à personnaliser un exemple d’application React.<br><br>Durée de mise sur le marché : Accéléré !<br>Les cycles de développement : Réduit !<br><br>Vous comprenez maintenant à quel point la gestion du contenu sans interface pour les sites web et les applications s’effectue sans interface utilisateur AEM."
>abstract=""

## Aperçu de l’application {#preview}

Cliquez sur le bouton **Lancement de l’éditeur de fragment de contenu** Le bouton ci-dessus ouvre l’éditeur de fragment de contenu dans un nouvel onglet.

![Éditeur de fragment de contenu](assets/customize-app/content-fragment-editor.png)

L’exemple d’application fourni avec votre AEM sans interface utilisateur graphique repose sur les fragments de contenu fournis via GraphQL. Utilisez l’éditeur de fragment de contenu pour vous familiariser avec le contenu en prévisualisant l’exemple.

1. Appuyez ou cliquez sur le bouton **Aperçu** en haut à droite de l’écran de l’éditeur.

1. L’application de démonstration s’ouvre dans un nouvel onglet. L&#39;application est pour la marque fictive de style de vie en plein air WKND. Cliquez pour parcourir l’exemple de contenu.

   ![Aperçu de l’application de démonstration](assets/customize-app/preview-demo-app.png)

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu pour continuer.

## Modification d’un en-tête dans l’application {#edit-app}

L’éditeur de fragment de contenu affiche la disposition de base de l’application sous la forme d’un fragment de contenu de page. Le **Panneaux** représentent différentes pages de l’application, chacune d’elles étant son propre fragment de contenu. En modifiant ces fragments, vous pouvez modifier le contenu de l’application.

1. Appuyez ou cliquez sur **Mtn Biker à Canyon** dans le **Panneaux** .

   ![Appuyez sur Mtn Biker dans le fragment Canyon .](assets/customize-app/mtn-biker-in-canyon.png)

1. L’éditeur ouvre le panneau d’en-tête de l’application pour le VTT. Chaque panneau est constitué de calques représentant différentes images et différents textes qui composent l’expérience.

   ![Panneaux](assets/customize-app/panels.png)

1. Sélectionner le calque de texte **Moker Mtn dans la couche de texte de canyon**. Le détail du calque s’affiche alors dans l’éditeur. Le calque est constitué de plusieurs fragments de contenu qui contrôlent le texte affiché dans ce panneau de l’application.

   ![Sélectionnez Mtn Biker dans le titre du canyon.](assets/customize-app/mtn-biker-in-canyon-text-layer.png)

1. Sélectionnez la **Mtn Biker dans le titre du canyon** élément de texte. L’éditeur de fragment de contenu s’ouvre alors.

   ![Sélectionnez l’élément de texte Mtn Biker dans le titre du canyon .](assets/customize-app/mtn-biker-in-canyon-title.png)

1. Modifier le texte à partir de `Your next great adventure is calling` to `Choose your own adventure`. La modification est enregistrée automatiquement par l’éditeur.

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour afficher vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet.

   ![Aperçu de l’application de démonstration](assets/customize-app/preview-demo-app-text.png)

Il est facile de mettre à jour le contenu d’une application React lorsqu’elle est intégrée à AEM CMS sans interface.

## Permutation d’une image dans l’application {#change-image}

Maintenant que vous avez modifié un titre dans l’application, essayez de modifier une image.

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu.

1. Vous devez revenir au bon endroit dans l’éditeur de fragment de contenu. Les chemins de navigation situés en haut à gauche de l’éditeur indiquent où vous vous trouvez dans la hiérarchie du contenu. Appuyez ou cliquez sur **Mtn Biker à Canyon** dans les chemins de navigation pour revenir à cette page.

   ![Chemin de navigation](assets/customize-app/breadcrumbs.png)

1. Sélectionnez la **Mtn Biking - Biker** calque d’image. L’éditeur de fragment de contenu s’ouvre alors.

   ![Modifier le fragment d’image](assets/customize-app/mtn-biking-biker.png)

1. Appuyez ou cliquez sur le bouton **X** pour supprimer l’image du motard. L’image disparaît et l’éditeur affiche une erreur, car l’image est une donnée requise pour ce modèle de fragment de contenu.

   ![Image supprimée du fragment](assets/customize-app/mtn-biking-biker-no-image.png)

1. Appuyez ou cliquez sur **Ajout d’une ressource**.

1. Le **Sélectionner une ressource** La boîte de dialogue s’ouvre et le chemin d’accès **sample-wknd-app** > **en** > **image-files** est automatiquement sélectionnée.

1. Sélectionner l’image `biker-yellow.png` puis appuyez ou cliquez sur **Sélectionner**.

   ![Sélectionner une ressource](assets/customize-app/select-asset.png)

1. L’image du motard est remplacée par l’image sélectionnée. L’éditeur enregistre automatiquement les modifications.

   ![Fragment modifié de l’image du motard](assets/customize-app/mtn-biking-biker-edited.png)

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour afficher vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet. Cliquez sur Actualiser dans le navigateur pour afficher votre nouvelle image de motard avec des shorts jaunes dans l’application.

Mettez à jour facilement les images et les ressources de vos applications avec AEM CMS sans interface.

## Ajout d’une référence à un nouveau fragment de contenu dans l’application {#create-moment}

Maintenant que vous avez mis à jour l’image du biker, nous allons découvrir comment ajouter du nouveau contenu à une application en créant et en référençant un nouveau fragment de contenu. Vous allez ajouter un appel de produit géré par un fragment de contenu &quot;moment d’achat&quot; au deuxième panneau de l’application.

![Exemple d&#39;un moment commercial](assets/customize-app/example-shoppable-moment.png)

1. Revenez à l’onglet du navigateur de l’éditeur de fragments de contenu.

1. Vous devez revenir au bon endroit dans l’éditeur de fragment de contenu. Les chemins de navigation situés en haut à gauche de l’éditeur indiquent où vous vous trouvez dans la hiérarchie du contenu. Appuyez ou cliquez sur **Accueil WKND** dans les chemins de navigation pour revenir à cette page.

   ![Revenez à l’écran de mise en page.](assets/customize-app/breadcrumbs-2.png)

1. Sélectionnez la **Mtn Biker sur WKND Yellow** du panneau.

   ![Créer un moment Shoppable](assets/customize-app/mtn-biker-on-wknd-yellow.png)

1. Sélectionnez la **Vélo Mtn - Shoppable** calque.

   ![Sélectionner le calque d’instant Shoppable](assets/customize-app/mtn-biking-shoppable.png)

1. Pour créer un appel à l’extérieur sur ce panneau, vous devez créer un fragment de contenu à moment Shoppable. Appuyez ou cliquez sur le bouton **+ Créer un fragment** bouton .

   ![Ajout d’un moment Shoppable](assets/customize-app/create-new-fragment.png)

1. Vous devez d’abord choisir un modèle sur lequel baser le nouveau fragment de contenu. Sélectionnez la **Article d’instant Shoppable** du modèle **Modèle de fragment de contenu** menu déroulant.

1. Attribuez un nom au fragment de contenu. Par exemple, saisissez `Shorts` dans la **Nom** champ .

   ![Nommez le moment Shoppable](assets/customize-app/new-content-fragment.png)

1. Appuyez ou cliquez sur **Créer et ouvrir**.

1. L’éditeur s’ouvre pour votre nouveau fragment de contenu.

1. Donnez un nom au moment Shoppable dans la variable **Texte** par exemple `Yellow shorts`.

1. Définir des valeurs pour **X** et **Y**. C’est là que cet appel à l’extérieur doit être superposé sur le panneau. Les modifications apportées au fragment sont automatiquement enregistrées par l’éditeur.
   * **X**: `-18`
   * **Y**: `-28`

   ![Modification du moment Shoppable](assets/customize-app/edit-shoppable-moment.png)

1. Appuyez ou cliquez sur **Aperçu** en haut à droite de la fenêtre pour afficher vos modifications. L’aperçu de l’application de démonstration s’ouvre dans un nouvel onglet. Cliquez sur Actualiser dans le navigateur pour tester le positionnement et effectuer les ajustements nécessaires dans l’éditeur.

Vous comprenez maintenant comment créer du contenu et le référencer en tant que fragment de contenu dans votre application peut être terminé sans cycle de développement.
