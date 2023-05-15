---
title: Créer la structure de contenu pour votre application
description: Découvrez comment utiliser AEM modèles de fragments de contenu pour créer votre structure de contenu, qui sert de base à votre contenu sans interface.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: ac94981e477e1fe8b883460ed9be009b4c1c088d
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 42%

---


# Créer la structure de contenu pour votre application {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Créer la structure de contenu pour votre application"
>abstract="Avec notre série de guides interactifs, vous apprendrez à créer une structure (également appelée Modèle de fragment de contenu) qui sert de base à tout votre contenu découplé."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="Lancer la console de modèles"
>abstract="Découvrez comment créer un schéma réutilisable, appelé modèle de fragment de contenu, pour votre contenu dans Adobe Experience Manager as a Cloud Service. Regardez la vidéo pour comprendre l’importance de cette étape. <br><br>Dans ce module d’apprentissage, nous utiliserons un site de voyage comme exemple et nous vous guiderons pour créer un modèle de séjour.<br><br>Lancez ce module dans un nouvel onglet en cliquant sur le bouton ci-dessous, puis suivez ce guide."
>additional-url="https://video.tv.adobe.com/v/3413261/?captions=fre_fr" text="Vidéo d’introduction à la structure de contenu"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Félicitations ! Vous avez appris à créer un modèle de fragment de contenu pour représenter la structure de vos données découplées et vous avez réalisé la première étape de la diffusion de contenu omnicanal à l’échelle et de manière standard."
>abstract=""

## Créer un modèle {#create-model}

La console de modèles de fragments de contenu s’ouvre dans un nouvel onglet. Considérez la console de modèles de fragments de contenu comme votre bibliothèque de modèles, dans laquelle vous créez de nouveaux modèles et gérez les modèles existants.

Dans notre exemple, nous allons créer un modèle qui représente la structure de données d’un voyage présenté sur un site Web de voyage. Nous nous référerons à un voyage utilisant ce modèle en tant que **Adventure**.

1. Cliquez sur le bouton **Créer** en haut à droite de l’écran pour commencer à créer un modèle de fragment de contenu.

1. L’assistant Créer un modèle démarre et vous guide tout au long de la création de votre modèle. Fournissez les informations requises.

   * **Titre du modèle** - Il s’agit d’une brève étiquette du modèle qui indique généralement l’objectif du modèle. Nous appellerons notre nouveau modèle `Adventure`.
   * **Activer le modèle** : cette option est activée par défaut et doit être cochée pour pouvoir créer des fragments de contenu basés sur ce modèle.

1. Une fois les champs obligatoires remplis, cliquez sur **Créer** en haut à gauche pour créer le modèle.

1. La boîte de dialogue **Succès** confirme la création du modèle. Cliquez sur **Ouvrir** dans la boîte de dialogue pour ouvrir votre nouveau modèle de fragment de contenu dans l’éditeur, dans un nouvel onglet. Passez ensuite à l’étape suivante qui consiste à ajouter des champs de données à votre modèle.

![Étapes 2 et 3 de la création d’un modèle de fragment de contenu.](assets/do-not-localize/create-model.png)

## Utilisation de l’éditeur de modèles {#configure-model}

Nous avons maintenant un modèle appelé **Adventure**, mais il ne contient aucun détail comme la durée, la destination, les activités, etc. Avant de pouvoir utiliser votre modèle, vous devez définir la structure de ses données.

L’éditeur de modèles de fragments de contenu vous permet de configurer les types de données et les propriétés qui définissent le contenu de votre modèle.

>[!TIP]
>
>Il est important de suivre les schémas de nommage dans les instructions suivantes, car nous nous référerons à ces noms spécifiques dans les modules ultérieurs.

1. Faites glisser un **Texte sur une seule ligne** du champ **Types de données** à droite de l’éditeur et déposez-le sur votre modèle de fragment de contenu.

1. Une fois un type de données placé, la colonne **Types de données** est automatiquement remplacée par l’onglet **Propriétés** vous permettant de définir les détails du type de données que vous venez de placer. Pour ce premier champ, nous allons stocker le titre du voyage ou de l&#39;aventure. Renseignez les propriétés suivantes.

   * **Render As :** **Champ de texte** - Lorsque vous créez une aventure, ce champ stocke le titre de l’aventure.
   * **Libellé du champ :** `Title` - Il s’agit du libellé affiché pour ce champ lors de la création d’une nouvelle aventure.

1. Une fois les propriétés du champ définies, vous pouvez revenir au **Types de données** dans le panneau de droite et ajoutez des champs supplémentaires en les faisant glisser et en les déposant.

Ainsi, vous pouvez ajouter autant de champs que nécessaire à votre modèle pour prendre en charge le type de structure de données dont vous aurez besoin. Les types de champs de données varient, mais le processus de leur ajout à votre modèle reste le même.

Passez à la section suivante pour ajouter les champs nécessaires pour renseigner et enregistrer le **Adventure** model

![Étapes 1, 2 et 3 de l’ajout de champs au modèle.](assets/do-not-localize/define-model-fields.png)

## Ajouter des champs au modèle {#additional-fields}

Vous avez déjà un champ pour le titre de l&#39;aventure. Vous devez maintenant ajouter des champs pour capturer la description, le prix et une image représentative de l’aventure.

>[!TIP]
>
>Le **Adventure** Le modèle est basé sur l’exemple de site WKND pour AEM. Vous pouvez [Visitez le site ici](https://wknd.site/us/en/adventures/yosemite-backpacking.html) pour afficher le contenu qui utilise la variable **Adventure** modèle.

Suivez les mêmes étapes que ci-dessus pour ajouter ces champs supplémentaires. La seule différence réside dans les propriétés que vous devez définir.

1. Ajoutez un champ pour stocker la description de l’aventure en faisant glisser un élément **Texte multi-lignes** et saisissez les propriétés suivantes :

   * **Render As :** **Zone de texte** - Lorsque vous créez une aventure, ce champ stocke une brève description du voyage.
   * **Libellé du champ :** `Description` - Il s’agit du libellé affiché pour ce champ lors de la création d’une nouvelle aventure.

1. Ajoutez un champ pour stocker le prix de l’aventure en faisant glisser un **Texte sur une seule ligne** et saisissez les propriétés suivantes :

   * **Render As :** **Champ de texte** - Lorsque vous créez une aventure, ce champ stocke le prix du voyage.
   * **Libellé du champ :** `Price` - Il s’agit du libellé affiché pour ce champ lors de la création d’une nouvelle aventure.

1. Ajoutez un champ pour stocker une image représentant le voyage. Les images dans AEM sont stockées sous la forme d’un autre type de contenu appelé **Ressources**. Pour créer un champ à leur intention, vous devez faire glisser et déposer une **Référence de contenu** qui fera référence à la ressource de l’image.

   * **Render As :** **Référence de contenu** - Lorsque vous créez une aventure, ce champ pointe vers la ressource image qui représente ce voyage.
   * **Libellé du champ :** `Image` - Il s’agit du libellé affiché pour ce champ lors de la création d’une nouvelle aventure.

1. Une fois que vous avez ajouté tous les champs nécessaires au modèle de fragment de contenu, cliquez sur **Enregistrer** en haut à droite de la fenêtre.

1. Le modèle est enregistré et vous revenez à la console du modèle de fragment de contenu.
