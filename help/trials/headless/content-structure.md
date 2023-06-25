---
title: Créer la structure de contenu pour votre application
description: Découvrez comment utiliser AEM modèles de fragments de contenu pour créer votre structure de contenu, qui sert de base à votre contenu sans interface.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 20%

---


# Créer la structure de contenu pour votre application {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Créer la structure de contenu pour votre application"
>abstract="Lorsque vous suivez cette série de guides interactifs, vous apprenez à créer une structure (appelée modèle de fragment de contenu) qui sert de structure de base à votre contenu sans en-tête."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="Lancer la console de modèles"
>abstract="Découvrez comment créer un schéma réutilisable, appelé modèle de fragment de contenu, pour votre contenu dans Adobe Experience Manager as a Cloud Service. Regardez la vidéo pour comprendre pourquoi cette étape est importante. <br><br>Dans ce module d’apprentissage, vous utilisez un site de voyage comme exemple et vous parcourez la création d’un modèle qui représente un voyage.<br><br>Lancez ce module dans un nouvel onglet en cliquant sur le bouton ci-dessous, puis suivez ce guide."
>additional-url="https://video.tv.adobe.com/v/3413261/?captions=fre_fr" text="Vidéo d’introduction à la structure de contenu"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Félicitations ! Vous avez appris à créer un modèle de fragment de contenu pour représenter la structure de vos données découplées et vous avez réalisé la première étape de la diffusion de contenu omnicanal à l’échelle et de manière standard."
>abstract=""

## Créer un modèle {#create-model}

La console de modèles de fragments de contenu s’ouvre dans un nouvel onglet. Considérez la console de modèle de fragment de contenu comme votre bibliothèque de modèles, dans laquelle vous créez des modèles et gérez les modèles existants.

Par exemple, vous créez un modèle qui représente la structure de données d’un voyage présenté sur un site Web de voyage. Un voyage utilisant ce modèle est appelé **Adventure**.

1. Dans le coin supérieur droit de l’écran, cliquez sur **Créer** pour commencer à créer un modèle de fragment de contenu.

1. L’assistant Créer un modèle vous guide tout au long de la création de votre modèle. Fournissez les informations requises.

   * **Titre du modèle** - Une brève étiquette du modèle et indique généralement l’objectif du modèle. Vous pouvez appeler le nouveau modèle. `Adventure`.
   * **Activer le modèle** : cette option est activée par défaut et doit être cochée pour pouvoir créer des fragments de contenu basés sur ce modèle.

1. Une fois les champs obligatoires renseignés, cliquez sur **Créer** en haut à gauche pour créer le modèle.

1. Le **Succès** confirme la création du modèle. Cliquez sur **Ouvrir** dans la boîte de dialogue afin que vous puissiez ouvrir votre nouveau modèle de fragment de contenu dans l’éditeur d’un nouvel onglet. Passez ensuite à l’étape suivante pour ajouter des champs de données à votre modèle.

![Étapes 2 et 3 de la création d’un modèle de fragment de contenu.](assets/do-not-localize/create-model.png)

## Utilisation de l’éditeur de modèles {#configure-model}

Vous avez maintenant un modèle appelé **Adventure**, mais il ne contient aucun détail tel que la durée, la destination et les activités. Avant de pouvoir utiliser votre modèle, vous devez définir la structure de ses données.

L’éditeur de modèles de fragments de contenu vous permet de configurer les types de données et les propriétés qui définissent le contenu de votre modèle.

>[!TIP]
>
>Il est important de suivre les schémas de nommage dans les instructions suivantes, car ces noms spécifiques sont référencés dans les modules ultérieurs.

1. Faites glisser un **Texte sur une seule ligne** du champ **Types de données** à droite de l’éditeur et déposez-le sur votre modèle de fragment de contenu.

1. Une fois un type de données placé, la variable **Types de données** remplacée automatiquement par **Propriétés** vous permettant de définir les détails du type de données que vous avez placé. Pour ce premier champ, vous souhaitez stocker le titre du voyage ou de l’aventure. Renseignez les propriétés suivantes.

   * **Render As :** **Champ de texte** - Lorsque vous créez une aventure, ce champ stocke le titre de l’aventure.
   * **Libellé du champ :** `Title` - Libellé affiché pour ce champ lors de la création d’une aventure.

1. Après avoir défini les propriétés du champ, vous pouvez revenir au **Types de données** dans le panneau de droite et ajoutez des champs supplémentaires en les faisant glisser et en les déposant.

Ainsi, vous pouvez ajouter autant de champs que nécessaire à votre modèle pour prendre en charge la structure de données dont vous avez besoin. Les types de champs de données varient, mais le processus de leur ajout à votre modèle reste le même.

Passez à la section suivante afin de pouvoir ajouter les champs nécessaires pour renseigner et enregistrer le **Adventure** model

![Étapes 1, 2 et 3 de l’ajout de champs au modèle.](assets/do-not-localize/define-model-fields.png)

## Ajouter des champs au modèle {#additional-fields}

Vous avez déjà un champ pour le titre de l&#39;aventure. Vous devez maintenant ajouter des champs pour capturer la description, le prix et une image représentative de l’aventure.

>[!TIP]
>
>Le **Adventure** Le modèle est basé sur l’exemple de site WKND pour AEM. Vous pouvez [Visitez le site ici](https://wknd.site/us/en/adventures/yosemite-backpacking.html) pour afficher le contenu qui utilise la variable **Adventure** modèle.

Suivez les mêmes étapes que ci-dessus pour ajouter ces champs supplémentaires. La seule différence réside dans les propriétés que vous devez définir.

1. Ajoutez un champ afin de stocker la description de l’aventure en faisant glisser un élément **Texte multi-lignes** et saisissez les propriétés suivantes :

   * **Render As :** **Zone de texte** - Lorsque vous créez une aventure, ce champ contient une brève description du voyage.
   * **Libellé du champ :** `Description` - Libellé affiché pour ce champ lors de la création d’une aventure.

1. Ajoutez un champ afin de stocker le prix de l’aventure en faisant glisser un **Texte sur une seule ligne** et saisissez les propriétés suivantes :

   * **Render As :** **Champ de texte** - Lorsque vous créez une aventure, ce champ stocke le prix du voyage.
   * **Libellé du champ :** `Price` - Libellé affiché pour ce champ lors de la création d’une aventure.

1. Ajoutez un champ afin de stocker une image représentant le voyage. Les images dans AEM sont stockées sous la forme d’un autre type de contenu appelé **Ressources**. Pour créer un champ à leur intention, vous devez faire glisser et déposer un **Référence de contenu** qui fait référence à la ressource de l’image.

   * **Render As :** **Référence de contenu** - Lorsque vous créez une aventure, ce champ pointe vers la ressource image qui représente ce voyage.
   * **Libellé du champ :** `Image` - Libellé affiché pour ce champ lors de la création d’une aventure.

1. Après avoir ajouté les champs nécessaires au modèle de fragment de contenu, dans le coin supérieur droit de la fenêtre, cliquez sur **Enregistrer**.

1. Le modèle est enregistré et vous revenez à la console du modèle de fragment de contenu.
