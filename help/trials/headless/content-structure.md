---
title: Création de la structure de contenu pour votre application
description: Découvrez comment créer la structure qui sert de base à tout votre contenu headless à l’aide des modèles de fragment de contenu AEM.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Création de la structure de contenu pour votre application {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Création de la structure de contenu pour votre application"
>abstract="Lorsque vous suivez cette série de guides interactifs, vous apprenez à créer une structure (appelée modèle de fragment de contenu) qui sert de base à votre contenu sans interface."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="Lancement de la console de modèles"
>abstract="Découvrez comment créer un schéma réutilisable, appelé modèle de fragment de contenu, pour votre contenu dans Adobe Experience Manager as a Cloud Service. Regardez la vidéo pour comprendre pourquoi il s’agit d’une étape importante. <br><br>Lancez ce module dans un nouvel onglet en cliquant sur le bouton ci-dessous, puis suivez ce guide."
>additional-url="https://video.tv.adobe.com/v/3413261" text="Vidéo d&#39;introduction Structure de contenu"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Félicitations ! Vous avez appris à créer un modèle de fragment de contenu pour représenter la structure de vos données sans interface utilisateur et vous avez fait la première étape de la diffusion de contenu omnicanal à l’échelle et de manière standard."
>abstract=""

## Création d’un modèle {#create-model}

Cliquez sur le bouton **Lancement de la console de modèles** Le bouton ci-dessus ouvre la console Modèles de fragments de contenu dans un nouvel onglet.

![La console de modèle de fragment de contenu](assets/content-structure/content-fragment-model-console.png)

Considérez la console de modèle de fragment de contenu comme votre bibliothèque de modèles, dans laquelle vous créez de nouveaux modèles et gérez les modèles existants. Votre console commence vide, alors créons un nouveau modèle !

1. Dans la console du modèle de fragment de contenu, cliquez sur le **Créer** en haut à droite de l’écran pour commencer à créer un modèle de fragment de contenu.

1. L’assistant Créer un modèle démarre et vous guide.

   ![Assistant de modèle de fragment de contenu](assets/content-structure/model-wizard.png)

   Fournissez les informations obligatoires.

   * **Titre du modèle** - Il s’agit d’une brève description du modèle et indique généralement l’objectif du modèle.
   * **Activer le modèle** - Cette option est cochée par défaut et doit être cochée pour pouvoir créer des fragments de contenu en fonction de ce modèle.

1. Une fois les champs obligatoires renseignés, cliquez sur **Créer** en haut à gauche pour créer le modèle.

1. Le **Succès** confirme la création du modèle.

   ![Boîte de dialogue de réussite pour la création d’un modèle de fragment de contenu](assets/content-structure/success.png)

## Ajouter des champs au modèle {#configure-model}

Avant de pouvoir utiliser le modèle, vous devez définir la structure de ses données.

1. Cliquez sur **Ouvrir** dans le **Succès** de l’étape précédente pour ouvrir votre nouveau modèle dans l’éditeur de modèles de fragments de contenu, où vous pouvez définir ses champs.

1. Faites glisser un champ depuis le **Types de données** à droite de l’éditeur et déposez-le sur votre modèle de fragment de contenu.

   ![Ajouter un type de données](assets/content-structure/drop-fields.png)

1. Une fois un type de données placé, la variable **Types de données** remplacée automatiquement par **Propriétés** vous permettant de définir les détails du type de données que vous venez de placer.

   ![Onglet Propriétés du champ de données](assets/content-structure/data-type-properties.png)

1. Une fois que vous avez ajouté tous les champs nécessaires au modèle de fragment de contenu, cliquez sur **Enregistrer** en haut à droite de la fenêtre.

Le modèle est enregistré et vous revenez à la console de modèles de fragments de contenu où vous pouvez ajouter d’autres modèles si nécessaire.

![Module terminé](assets/content-structure/content-fragment-model-console-populated.png)
