---
title: Créer du contenu sans affichage
description: Utilisez le modèle de fragment de contenu que vous avez créé précédemment pour créer du contenu qui peut être utilisé pour la création de pages ou comme base pour votre contenu sans en-tête.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
source-git-commit: 4269bc9650f197ae33fcef40a847f8b200097e45
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# Créer du contenu sans affichage {#create-content}

En suivant le module d’apprentissage intégré au produit, apprenez à utiliser [les modèles de fragment de contenu que vous avez créés précédemment ;](content-structure.md) pour créer du contenu qui peut être utilisé pour la création de pages ou comme base pour votre contenu sans en-tête. Ce document sert de complément à la visite interactive, couvrant les mêmes étapes et la liaison à des ressources supplémentaires, le cas échéant.

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Créer un contenu"
>abstract="En vous basant sur les modèles que vous avez créés dans le module 1, vous apprendrez à créer du contenu qui peut être utilisé pour la création de pages ou comme base de votre contenu sans en-tête."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="Lancement de la console Fragment de contenu"
>abstract="Dans AEM CMS sans interface, les &quot;fragments de contenu&quot; sont tous des éléments de contenu qui s’intègrent à la structure prédéfinie appelée &quot;modèle de fragment de contenu&quot;. Dans cette présentation, vous apprendrez à créer du contenu pour votre modèle de fragment de contenu.<br><br>Cliquez ci-dessous pour lancer la fonctionnalité dans un nouvel onglet et suivez ce document d’apprentissage pour créer votre premier fragment de contenu."
>additional-url="https://video.tv.adobe.com/v/328618" text="Espace réservé pour la vidéo d’introduction"

## Fragments de contenu {#introduction}

Dans AEM as a Cloud Service, les fragments de contenu sont des éléments de contenu sans affichage basés sur la structure définie par un modèle de fragment de contenu. Vous pouvez créer votre propre fragment de contenu à partir de la console Fragment de contenu . La console Fragment de contenu peut être considérée comme votre bibliothèque de contenu sans affichage. Vous utilisez la console pour créer des fragments de contenu et gérer les fragments existants. Votre console est vide, alors créons un nouveau fragment !

![Editer le contenu de votre fragment](assets/create-content/content-fragment-console.png)

Si vous souhaitez accéder vous-même à la console Fragment de contenu en dehors des instructions in-app, elle se trouve à l’aide de l’icône Adobe située dans le coin supérieur gauche de la page. Cela ouvre la navigation globale d’AEM. À partir de là, vous choisissez la variable **Navigation** puis **Fragments de contenu**.

>[!TIP]
>
>Si vous souhaitez en savoir plus sur la navigation dans AEM, reportez-vous à la section [Section Ressources supplémentaires](#additional-resources) de ce document pour plus d’informations sur AEM gestion de base.

## Création d’un fragment de contenu {#create-fragment}

Les fragments de contenu représentent votre contenu sans affichage. Mais elles ne peuvent être créées que sur la base d&#39;une structure de contenu prédéfinie. Le modèle de fragment de contenu que vous avez créé précédemment sert de structure.

1. Appuyez ou cliquez sur le bouton **Créer** dans le coin supérieur droit de la console pour ouvrir le **Nouveau fragment de contenu** pour commencer à créer un fragment de contenu.

   ![Boîte de dialogue Créer un fragment de contenu](assets/create-content/create-content-fragment.png)

1. Si vous suivez les conseils in-app, **Emplacement** sera automatiquement renseigné.

   1. Si vous ne suivez pas les instructions, utilisez l’explorateur de chemins d’accès pour sélectionner le dossier de votre projet.

   1. Dans le **Nouveau fragment de contenu** , appuyez ou cliquez sur **Choisir l’emplacement** (icône qui ressemble à un dossier) dans la variable **Emplacement** champ .

      ![Boîte de dialogue Choisir l’emplacement](assets/create-content/choose-location.png)
   * Vous pouvez également sélectionner le chemin dans le panneau de navigation de gauche de la console Fragment de contenu avant de cliquer sur **Créer**.


1. Dans le **Modèle de fragment de contenu** , sélectionnez le modèle de fragment de contenu que vous avez créé précédemment dans la liste déroulante.

1. Ajouter un **Titre** pour le fragment de contenu.

1. Appuyez ou cliquez sur **Créer et ouvrir**.

## Éditeur de fragment de contenu {#edit-fragment}

Une fois que vous avez enregistré votre nouveau fragment de contenu, l’éditeur de fragment de contenu s’ouvre, où vous pouvez fournir le contenu réel du fragment.

1. L’éditeur affiche les champs que vous avez définis dans le modèle sélectionné. Vous pouvez les modifier ici pour compléter votre fragment de contenu. Votre progression est enregistrée automatiquement.

   ![Éditeur de fragment de contenu](assets/create-content/content-fragment-editor.png)

1. Si le modèle de fragment de contenu comporte de nombreux champs, vous pouvez accéder rapidement à n’importe quel champ à l’aide de la variable **Variables** du panneau situé à gauche de l’éditeur. Les champs contenant des erreurs seront marqués ici.

1. Pour que le fragment de contenu puisse être utilisé par une application externe, vous devez le publier. Appuyez ou cliquez sur le bouton **Publier** en haut à droite de l’éditeur.

1. Sélectionner **Maintenant** dans la liste déroulante. Vous pouvez également planifier sa publication ultérieurement.

   ![Bouton Publier](assets/create-content/publish.png)

   >[!TIP]
   >
   >Si vous souhaitez en savoir plus sur la publication de contenu dans AEM, reportez-vous à la section [Section Ressources supplémentaires](#additional-resources) de ce document pour plus d’informations sur la publication.

1. AEM effectue automatiquement une vérification de référence pour s’assurer que toutes les ressources nécessaires sont publiées pour votre fragment de contenu. Dans ce cas, vous devrez également publier le modèle que vous avez créé. Cliquez ou appuyez sur **Publier**.

   ![Vérification de référence](assets/create-content/references.png)

1. La publication est confirmée dans une bannière.

   ![Confirmation de publication](assets/create-content/publish-confirm.png)

## Vous avez appris à créer un fragment de contenu ! {#conclusion}

Dans ce module, vous avez appris à créer un fragment de contenu en fonction du modèle que vous avez créé précédemment. C’est ainsi qu’un auteur de contenu crée du contenu structuré sans interface.

Maintenant que votre contenu est créé et publié, vous pouvez extraire ce contenu via Graph QL via AEM API. Vous en apprendrez plus à ce sujet dans le module [Extrayez du contenu via l’API GraphQL.](extract-content.md)

Vous pouvez revenir à l’écran d’accueil de votre évaluation en cliquant sur **Solutions** en haut à droite de la barre de navigation et en sélectionnant **Experience Manager**.

![Naviguer à la page d’accueil](assets/create-content/home.png)

## Ressources supplémentaires {#additional-resources}

Pour plus d’informations sur les fragments de contenu et les AEM, consultez cette documentation supplémentaire.

* [Manipulation de base](/help/sites-cloud/authoring/getting-started/basic-handling.md) - Documentation sur la navigation et l’utilisation d’AEM pour les nouveaux utilisateurs
* [Gestion des fragments de contenu - Publication et référencement](/help/assets/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment) - Détails sur la publication de contenu dans AEM
* [Fragments de contenu](/help/assets/content-fragments/content-fragments.md) - Présentation des fragments de contenu et des liens pour obtenir une documentation complète sur les fragments de contenu
* [Gestion des fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) - Comment créer et gérer des fragments de contenu
