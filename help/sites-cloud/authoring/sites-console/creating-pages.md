---
title: Créer des pages
description: Découvrez comment créer des pages pour votre site web à l’aide de la console Sites.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 6e13244d7ba7bb6e7a51525b66274427fe21d664
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 34%

---


# Créer des pages {#creating-pages}

Découvrez comment créer des pages pour votre site web à l’aide de la console **Sites**.

>[!TIP]
>
>Avant de commencer à créer des pages, familiarisez-vous avec [l&#39;organisation de vos pages en AEM.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## Privilèges d’accès {#access-privileges}

Pour créer des pages, votre compte doit disposer des droits d’accès et des autorisations appropriés.

Si vous rencontrez des problèmes, contactez votre administrateur système.

## Création d’une page {#creating-a-new-page}

À moins que toutes les pages n’aient été créées pour vous au préalable, vous devez créer une page avant de commencer à créer du contenu :

1. Ouvrez [la console **Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Accédez à l’emplacement où créer la page.
1. Ouvrez le sélecteur de liste déroulante avec l’option **Créer** de la barre d’outils, puis sélectionnez **Page** dans la liste :

   ![Création d’une page](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. À la première étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Sélectionnez le modèle que vous souhaitez utiliser pour créer la page, puis cliquez sur **Suivant** pour continuer ou **Annuler** pour abandonner le processus.
   * Les modèles sont pris en charge à la fois pour l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) et pour l’[éditeur universel.](/help/edge/wysiwyg-authoring/templates.md)

   ![Sélection d’un modèle pour une nouvelle page](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. À la dernière étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Utilisez les trois onglets pour accéder aux [propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md) que vous souhaitez attribuer à la nouvelle page, puis sélectionnez **Créer** pour réellement créer la page.

   * Utilisez **Précédent** pour revenir à la sélection de modèle.

   Les champs clés sont les suivants :

   * **Titre** :

      * Il est visible par la personne utilisatrice et est obligatoire.

   * **Nom** :

      * Il est utilisé pour générer l’URI. S’il n’est pas spécifié, le nom est dérivé du titre.
      * Si vous indiquez un **nom** de page lors de la création d’une page, AEM [valide le nom en fonction des conventions](/help/implementing/developing/introduction/naming-conventions.md) imposées par AEM et JCR.
      * Vous **ne pouvez pas utiliser de caractères non valides** dans le champ **Nom**. Lorsque AEM détecte des caractères non valides, le champ est mis en surbrillance et un message d’explication s’affiche pour indiquer les caractères à supprimer/remplacer.

   >[!TIP]
   >
   >Voir [Conventions de dénomination de page](#page-naming-conventions).

   Le **Titre** est l’une des informations minimales requises pour créer une page.

   ![Affichage du titre de la page](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Appuyez ou cliquez sur **Créer** pour terminer le processus et créer votre nouvelle page. La boîte de dialogue de confirmation vous demande si vous souhaitez **ouvrir** la page immédiatement ou revenir à la console (**Terminé**). Sélectionnez-en un pour terminer le processus de création de la page.

   ![Réussite de la création de page](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Si vous choisissez **Ouvrir**, la console **Sites** ouvre l’éditeur approprié en fonction du modèle de la nouvelle page, soit :
      * [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md)

Si vous revenez à la console, la nouvelle page s’affiche :

![Nouvelle page résultante](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Si vous créez une page en utilisant un nom qui existe déjà au même emplacement, AEM crée la page avec une variante du nom spécifié en ajoutant un numéro. Par exemple, si `beach` existe déjà, la nouvelle page devient `beach1`.

>[!CAUTION]
>
>Une fois qu’une page a été créée, son modèle ne peut plus être modifié, sauf si vous [ créez un lancement avec un nouveau modèle](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), mais cela perdra tout contenu existant.
