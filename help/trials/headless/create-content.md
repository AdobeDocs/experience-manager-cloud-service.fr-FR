---
title: Créer du contenu découplé
description: Utilisez le modèle de fragment de contenu que vous avez créé précédemment pour créer du contenu qui peut être utilisé pour la création de pages ou comme base pour votre contenu découplé.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

---


# Créer du contenu découplé {#create-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Créer du contenu découplé"
>abstract="En utilisant le modèle que vous avez créé dans le module précédent, vous apprendrez à créer du contenu qui peut être utilisé pour la création de pages ou comme base à votre contenu découplé."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="Démarrer la console Fragments de contenu"
>abstract="La création de contenu cohérent et de qualité supérieure qui fonctionne en toute simplicité sur vos applications et sites Web vous permet d’offrir de superbes expériences client. Ce module vous guide tout au long de la création de votre premier contenu découplé à l’aide de la console Fragments de contenu.<br><br>Lancez ce module dans un nouvel onglet en cliquant sur le bouton ci-dessous, puis suivez ce guide."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide_footer"
>title="Très bon travail. Dans ce module, vous avez appris à créer un contenu découplé comme fragment de contenu en fonction du modèle que vous avez créé précédemment. Vous comprenez désormais comment les équipes de contenu peuvent créer et gérer du contenu pour les applications et les sites Web, indépendamment des cycles de développement."
>abstract=""

## Créer un fragment de contenu {#create-fragment}

Les fragments de contenu représentent votre contenu découplé et sont basés sur des structures prédéfinies, appelées modèles de fragment de contenu. Vous avez déjà créé un modèle dans un module précédent.

Dans ce module, vous allez créer un fragment de contenu basé sur ce modèle à l’aide de la console Fragments de contenu. Envisagez la console Fragments de contenu comme votre bibliothèque de contenu découplé. Utilisez-la pour créer des fragments de contenu et gérer des fragments existants.

La console Fragments de contenu est utilisée pour créer et modifier du contenu découplé sur les canaux de diffusion et indépendamment du contexte, ce qui peut être la méthode la plus efficace dans de nombreux cas de création. Dans un module ultérieur, nous allons explorer la modification de contenu découplé dans le contexte et sur place.

1. Cliquez sur le bouton **Créer** en haut à droite de la console.

1. La boîte de dialogue **Nouveau fragment de contenu** s’ouvre et vous pouvez commencer à créer un fragment de contenu. Le champ **Emplacement** est automatiquement renseigné à l’emplacement du nouveau contenu.

1. Dans la liste déroulante **Modèle de fragment de contenu**, sélectionnez le modèle de fragment de contenu **Aventure** que vous avez créé précédemment.

1. Ajoutez `Tuscany` comme **titre** descriptif pour le fragment de contenu. Cela permet d’identifier votre fragment dans la console.

1. Sélectionnez **Créer et ouvrir**.

![Création d’un fragment de contenu.](assets/do-not-localize/create-content.png)

>[!TIP]
>
>Selon les paramètres de votre navigateur, le nouvel onglet du navigateur peut être supprimé par un bloqueur de pop-up. Si votre nouveau fragment ne s’ouvre pas après avoir cliqué sur **Créer et ouvrir**, vérifiez les paramètres de votre navigateur.

## Ajouter du contenu à votre fragment de contenu {#add-content}

Une fois que vous avez enregistré et ouvert votre nouveau fragment de contenu, l’éditeur de fragments de contenu s’ouvre dans un nouvel onglet. Vous pouvez y ajouter le contenu de votre nouveau fragment.

1. L’éditeur de fragments de contenu affiche les champs que vous avez définis dans le modèle sélectionné. Vous pouvez ajouter du contenu à chaque champ pour compléter votre fragment de contenu. Votre progression est enregistrée automatiquement.

1. Fournissez un **titre** pour votre fragment en saisissant `Tuscan Adventure`.

1. Fournissez une **description** pour votre fragment en collant le texte suivant.

   ```text
   Visiting Tuscany on a bicycle is about experiencing the old world charm of Italy on your own terms. Your efforts on the climbs of Italy's rolling hills during this tour are rewarded with sunny Mediterranean landscapes and unmatched Italian hospitality. Tuscany's natural wonders have always been a well of inspiration for arts and culture. Find out why as you explore the Italian countryside and coastline on bicycle.
   ```

1. Fournissez un **prix** pour votre fragment en saisissant `$700`.

1. Fournissez une **image** qui représente le voyage en appuyant ou en cliquant sur **Ajouter une ressource** dans le champ **Image**.

1. Dans le pop-up de la ressource, cliquez sur **Parcourir les ressources** pour effectuer une sélection à partir d’une ressource existante dans la bibliothèque de ressources.

   ![Ajouter une ressource](assets/do-not-localize/add-asset.png)

1. La boîte de dialogue **Sélectionner une ressource** s’ouvre. À l’aide du navigateur d’arborescence dans le panneau de gauche, accédez à **Toutes les ressources** > **aem-demo-assets** > **en** > **adventures** > **cycling-tuscany**.

1. Le contenu du dossier **cycling-tuscany** s’affiche à droite. Sélectionnez l’image `ADOBESTOCK_141786166.JPEG`.

1. Sélectionnez **Sélectionner**.

   ![Sélectionner une ressource](assets/do-not-localize/select-asset.png)

1. L’image sélectionnée s’affiche dans le fragment de contenu. L’éditeur enregistre automatiquement les modifications.

1. Une fois que vous avez terminé d’ajouter du contenu, cliquez sur le bouton **Publier** en haut à droite de l’éditeur. Votre fragment de contenu peut ainsi être utilisé par des applications externes. Sélectionnez ensuite **Maintenant** dans la liste déroulante. Vous pouvez également planifier sa publication pour plus tard.

   ![Publier le contenu](assets/do-not-localize/publish.png)

1. La boîte de dialogue **Publier des fragments de contenu** s’affiche. AEM effectue automatiquement une vérification des références pour s’assurer que toutes les ressources nécessaires sont publiées pour votre fragment de contenu. Dans ce cas, vous devrez également publier le modèle que vous avez créé. Sélectionnez **Publier**.

   ![Vérification de la publication et des références.](assets/do-not-localize/publish-confirm.png)

1. La publication est confirmée dans une bannière.

Votre contenu est publié et prêt à être diffusé sur votre application ou votre site Web sous la forme d’un fragment de contenu.
