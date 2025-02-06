---
title: Créer des pages
description: Découvrez comment créer des pages pour votre site web à l’aide de la console Sites.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 34%

---


# Créer des pages {#creating-pages}

Découvrez comment créer des pages pour votre site web à l’aide de la console **Sites**.

>[!TIP]
>
>Avant de commencer à créer des pages, familiarisez-vous avec [l’organisation de vos pages dans AEM](/help/sites-cloud/authoring/sites-console/organizing-pages.md).

## Privilèges d&#39;accès {#access-privileges}

Votre compte a besoin des droits d’accès et des autorisations appropriés pour créer des pages.

Si vous rencontrez des problèmes, contactez votre administrateur système.

## Création d’une page {#creating-a-new-page}

À moins que toutes les pages n’aient été créées pour vous au préalable, vous devez créer une page avant de commencer à créer du contenu :

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à l’emplacement où créer la page.
1. Ouvrez le sélecteur de liste déroulante avec l’option **Créer** de la barre d’outils, puis sélectionnez **Page** dans la liste :

   ![Création d’une page](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. À partir de la première étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Sélectionnez le modèle à utiliser pour créer la page, puis sélectionnez **Suivant** pour continuer ou **Annuler** pour abandonner le processus.
   * Les modèles sont pris en charge pour l’[Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) ainsi que pour l’[Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md).

   ![Sélection d’un modèle pour une nouvelle page](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. À partir de la dernière étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Utilisez les trois onglets pour saisir les [propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md) qui doivent être affectées à la nouvelle page, puis sélectionnez **Créer** pour créer réellement la page.

   * Utilisez **Précédent** pour revenir à la sélection de modèle.

   Les champs clés sont les suivants :

   * **Titre** :

      * Il est visible par la personne utilisatrice et est obligatoire.

   * **Nom** :

      * Il est utilisé pour générer l’URI. S’il n’est pas spécifié, le nom est dérivé du titre.
      * Si vous indiquez un **nom** de page lors de la création d’une page, AEM [valide le nom en fonction des conventions](/help/implementing/developing/introduction/naming-conventions.md) imposées par AEM et JCR.
      * Vous **ne pouvez pas utiliser de caractères non valides** dans le champ **Nom**. Lorsqu’AEM détecte des caractères non valides, le champ est mis en surbrillance et un message d’explication s’affiche pour indiquer les caractères à supprimer/remplacer.

   >[!TIP]
   >
   >Voir [Conventions de dénomination de page](#page-naming-conventions).

   Le **Titre** est l’une des informations minimales requises pour créer une page.

   ![Affichage du titre de la page](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Appuyez ou cliquez sur **Créer** pour terminer le processus et créer votre page. La boîte de dialogue de confirmation vous demande si vous souhaitez **Ouvrir** la page immédiatement ou revenir à la console (**Terminé**). Sélectionnez-en un pour terminer le processus de création de page.

   ![Réussite de la création de page](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Si vous choisissez **Ouvrir**, la console **Sites** ouvre l’éditeur approprié en fonction du modèle de la nouvelle page :
      * [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md)

Si vous revenez à la console, vous pouvez voir votre nouvelle page :

![Nouvelle page résultante](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Si vous créez une page en utilisant un nom qui existe déjà au même emplacement, AEM crée la page avec une variante du nom spécifié en ajoutant un nombre. Par exemple, si `beach` existe déjà, la nouvelle page devient `beach1`.

>[!CAUTION]
>
>Une fois la page créée, son modèle ne peut plus être modifié, à moins de [créer un lancement avec un nouveau modèle](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template) ; vous perdrez alors tout contenu existant.
