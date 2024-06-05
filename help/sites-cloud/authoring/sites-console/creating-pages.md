---
title: Créer des pages
description: Découvrez comment créer des pages pour votre site web à l’aide de la console Sites.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 36%

---

# Créer des pages {#creating-pages}

Découvrez comment créer des pages pour votre site web à l’aide du **Sites** console.

>[!TIP]
>
>Avant de commencer à créer des pages, familiarisez-vous avec [la manière dont vos pages sont organisées en AEM.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## Privilèges d’accès {#access-privileges}

Pour créer des pages, votre compte doit disposer des droits d’accès et des autorisations appropriés.

Si vous rencontrez des problèmes, contactez votre administrateur système.

## Création d’une page {#creating-a-new-page}

À moins que toutes les pages n’aient été créées pour vous au préalable, vous devez créer une page avant de commencer à créer du contenu :

1. Ouvrir [la valeur **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Accédez à l’emplacement où créer la page.
1. Ouvrez le sélecteur de liste déroulante avec l’option **Créer** de la barre d’outils, puis sélectionnez **Page** dans la liste :

   ![Création d’une page](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. À la première étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Sélectionnez le modèle à utiliser pour créer la page, puis sélectionnez **Suivant** pour continuer.

   * Cliquez/appuyez sur **Annuler** pour interrompre le processus.

   ![Sélection d’un modèle pour une nouvelle page](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. À la dernière étape de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Utilisez les trois onglets pour saisir la variable [propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md) que vous souhaitez attribuer à la nouvelle page, puis sélectionnez **Créer** pour créer réellement la page.

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

1. Appuyez ou cliquez sur **Créer** pour terminer le processus et créer votre page. La boîte de dialogue de confirmation vous demande si vous souhaitez **Ouvrir** la page immédiatement ou revenir à la console (**Terminé**). Sélectionnez-en un pour terminer le processus de création de la page.

   ![Réussite de la création de page](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Si vous choisissez **Ouvrir**, la variable **Sites** La console ouvre l’éditeur approprié en fonction du modèle de la nouvelle page :
      * [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md)

Si vous revenez à la console, la nouvelle page s’affiche :

![Nouvelle page résultante](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Si vous créez une page en utilisant un nom qui existe déjà au même emplacement, AEM crée la page avec une variante du nom spécifié en ajoutant un numéro. Par exemple, si `beach` existe déjà, la nouvelle page devient `beach1`.

>[!CAUTION]
>
>Une fois une page créée, son modèle ne peut plus être modifié, sauf si vous [créer un lancement avec un nouveau modèle ;](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), mais vous perdrez tout contenu existant.
