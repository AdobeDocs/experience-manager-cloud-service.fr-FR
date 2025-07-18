---
title: Gérer des pages
description: Découvrez comment gérer les pages de votre site web dans AEM, notamment en déplaçant, copiant et supprimant.
exl-id: 355b60c5-a82e-4bbb-98ea-bfcc0126b7fd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 45805d4baa8b93df2225b44152fee1457b421150
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 67%

---

# Gérer des pages {#managing-pages}

Découvrez comment gérer les pages de votre site web dans AEM, notamment en déplaçant, copiant et supprimant.

>[!TIP]
>
>Avant de commencer à gérer vos pages, familiarisez-vous avec [l’organisation de vos pages dans AEM](/help/sites-cloud/authoring/sites-console/organizing-pages.md).

>[!TIP]
>
>Il existe un certain nombre de [raccourcis clavier](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) à utiliser à partir de la console Sites web qui facilitent l’organisation des pages.

## Privilèges d&#39;accès {#access-privileges}

Votre compte a besoin des droits d’accès et des autorisations appropriés pour agir sur les pages, comme créer, copier, déplacer, modifier et supprimer.

En cas de problème, contactez l’administrateur ou l’administratrice système.

## Ouverture d’une page pour la modifier {#opening-a-page-for-editing}

Après avoir [créé une page](/help/sites-cloud/authoring/sites-console/creating-pages.md) ou accédé à une page existante à l’aide de [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md), vous pouvez l’ouvrir pour la modifier.

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à la page à modifier.
1. Sélectionnez votre page à l’aide de l’une des options suivantes :

   * [Actions rapides](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * Le [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) et la barre d’outils

1. Appuyez ou cliquez sur l’icône **Modifier**.

   ![Bouton Modifier](/help/sites-cloud/authoring/assets/edit.png)

1. La page s’ouvre et vous pouvez la modifier selon vos besoins. Selon le mode de création de la page sélectionnée, l’action **Modifier** ouvre l’éditeur approprié.
   * [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) - Pour les pages créées avec l’éditeur de page d’AEM
   * [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) - Pour les pages créées avec l’éditeur universel

## Copier et coller une page {#copying-and-pasting-a-page}

Vous pouvez copier une page ainsi que toutes ses sous-pages à un nouvel emplacement :

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à la page à copier.
1. Sélectionnez votre page à l’aide de l’une des options suivantes :

   * [Actions rapides](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * Le [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) et la barre d’outils

1. Appuyez ou cliquez sur l’icône de page **Copier**.

   ![Copier](/help/sites-cloud/authoring/assets/copy.png)

1. Accédez à l’emplacement destiné à la nouvelle copie de la page.
1. Sélectionnez l’icône **Coller** qui est devenue disponible.

   ![Coller](/help/sites-cloud/authoring/assets/paste.png)

1. La boîte de dialogue de collage présente un résumé de la transaction de collage et permet d’effectuer les opérations suivantes :
   * **Nouveau nom du site :** modifiez le nom de la page collée.
   * **Coller sans enfants :** omettez les pages enfants de la page sélectionnée lors du collage (par défaut, les pages enfants sont collées).

   ![Boîte de dialogue de collage](/help/sites-cloud/authoring/assets/paste-dialog.png)

1. Sélectionnez le bouton **Coller** pour confirmer la transaction de collage et créer la ou les nouvelles pages.

>[!NOTE]
>
>Si vous copiez la page à un emplacement où il existe une page du même nom que l’original, le système génère automatiquement une variante du nom en y ajoutant un numéro. Par exemple, si `beach` existe déjà, une nouvelle page portant le nom `beach` devient `beach1`.

>[!NOTE]
>
>Si vous débutez l’action de collage en mode de sélection, cette page est fermée dès qu’elle est copiée.

## Déplacement ou changement de nom d’une page {#moving-or-renaming-a-page}

La procédure pour déplacer ou renommer une page est plus ou moins la même et les deux actions sont gérées par le même assistant de déplacement des pages. Cet assistant permet d’effectuer les opérations suivantes :

* Renommer une page sans la déplacer
* Déplacer la page sans la renommer
* Déplacer et renommer une page simultanément

AEM vous offre la possibilité de mettre à jour les liens internes qui font référence à la page renommée ou déplacée. Cette opération peut être effectuée page par page afin d’offrir une flexibilité totale.

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à la page à déplacer.
1. Sélectionnez votre page à l’aide de l’une des options suivantes :

   * [Actions rapides](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * Le [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) et la barre d’outils

1. Appuyez ou cliquez sur l’icône de page **Déplacer** pour ouvrir l’assistant de déplacement de page.

   ![Bouton Déplacer](/help/sites-cloud/authoring/assets/move.png)

1. L’étape **Renommer** de l’assistant vous fournit **Informations** à propos de la page, y compris la date de création, le chemin d’accès et le nombre de références directes. À partir de là, vous pouvez :

   * Indiquez le nom que vous souhaitez donner à la page après l’avoir déplacée, puis sélectionnez **Suivant** pour continuer.
   * Cliquez/appuyez sur **Annuler** pour interrompre le processus.

   ![Déplacer et renommer la page](/help/sites-cloud/authoring/assets/move-page-rename.png)

   * Le nom de la page peut rester identique si vous déplacez uniquement la page.

   >[!NOTE]
   >
   >Si vous déplacez la page à un emplacement où il existe une page du même nom, le système génère automatiquement une variante du nom en y ajoutant un numéro. Par exemple, si `beach` existe déjà, une nouvelle page portant le nom `beach` devient `beach1`.

1. À partir de l’étape **Sélectionner la destination** de l’assistant, vous pouvez effectuer l’une des opérations suivantes :

   * Utilisez la [vue Colonne](/help/sites-cloud/authoring/basic-handling.md#column-view) pour accéder au nouvel emplacement de la page :

      * Sélectionnez la destination en cliquant sur sa miniature.
      * Cliquez sur **Suivant** pour continuer.

   * Utilisez **Précédent** pour revenir à la spécification du nom de page.

   >[!NOTE]
   >
   >Par défaut, le parent de la page que vous déplacez/renommez est sélectionné comme destination.

   ![Sélectionner la destination de la page déplacée](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Si vous déplacez la page à un emplacement où il existe une page du même nom, le système génère automatiquement une variante du nom en y ajoutant un numéro. Par exemple, si `winter` existe déjà, `winter` devient `winter1`.

1. Si la page est liée ou référencée, ou si elle a été publiée, les détails sont répertoriés dans l’étape **Ajuster/republier**.

   * Vous pouvez indiquer quelles pages sont les pages à adapter et/ou à republier.

   >[!NOTE]
   >
   >* Si la page n’est ni liée ni référencée, cette étape ne sera pas disponible.
   >* Cette étape répertorie les références directes et indirectes. Cette valeur peut être différente de la valeur indiquée à l’étape **Renommer** de l’assistant, ainsi que des références indiquées par le rail Références, qui indiquent toutes deux des références directes uniquement pour des raisons de performances.

   ![Republier la page lors du déplacement](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Appuyez ou cliquez sur **Déplacer** pour définir le moment où l’action de déplacement doit se produire.

   * **Maintenant** déclenchera une [tâche asynchrone](#asynchronous-actions) pour déplacer la page immédiatement.
   * **Ultérieurement** vous permet de planifier une date pour le traitement du déplacement.

   ![Définir quand déplacer](assets/managing-pages-move-page-now-later.png)

1. Appuyez ou cliquez sur **Continuer** pour terminer le déplacement de la page.

>[!NOTE]
>
>Si la page a déjà été publiée, son déplacement la dépublie automatiquement. Par défaut, elle est republiée une fois le déplacement terminé, mais ce paramètre peut être modifié en décochant le champ **Republier** à l’étape **Ajuster/Republier**.

>[!NOTE]
>
>La modification du nom d’une page est également soumise aux [Conventions de dénomination de page](#page-naming-conventions) lors de la spécification du nouveau nom de la page.

>[!NOTE]
>
>Une page ne peut être déplacée qu’à un emplacement où le modèle sur lequel la page est basée est autorisé. Pour plus d’informations, voir [Disponibilité des modèles](/help/implementing/developing/components/templates.md#template-availability).

### Actions asynchrones {#asynchronous-actions}

Les actions de déplacement de page sont toujours traitées de manière asynchrone, ce qui permet à l’utilisateur ou à l’utilisatrice de continuer à créer dans l’IU sans entraves.

Pour consulter le statut des tâches asynchrones, accédez au tableau de bord [**Statut des tâches asynchrones**](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations), disponible sous **Navigation globale** > **Outils** > **Opérations** > **Tâches**.

>[!TIP]
>
>Pour plus d’informations sur le traitement asynchrone des tâches et sur la manière de configurer la limite pour les actions de déplacement/changement de nom de page, consultez le document [Tâches asynchrones](/help/operations/asynchronous-jobs.md) dans le guide d’utilisation relatif aux opérations.

### Suppression d’une page {#deleting-a-page}

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à la page à supprimer.
1. En [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources), sélectionnez la page requise, puis utilisez la commande **Supprimer** de la barre d’outils :

   ![Bouton Supprimer](/help/sites-cloud/authoring/assets/delete.png)

1. Une boîte de dialogue de confirmation s’affiche.

   ![Boîte de dialogue Supprimer](/help/sites-cloud/authoring/assets/delete-page.png)

   * **Voulez-vous archiver les pages avant la suppression ?** – Si cette case est cochée, les versions des pages sélectionnées pour suppression sont créées lors de la suppression.
      * [Il est possible de restaurer les versions ultérieurement](/help/sites-cloud/authoring/sites-console/page-versions.md).
      * Les pages supprimées sans versions précédentes ne peuvent pas être restaurées.
1. Appuyez ou cliquez sur **Annuler** pour abandonner l’action ou sur **Supprimer** pour confirmer l’action.
   * Si la page ne comporte aucune référence, elle est supprimée.
   * Si la page comporte des références, un message vous informe qu’**une ou plusieurs pages sont référencées.** Vous pouvez sélectionner **Forcer la suppression** ou **Annuler**.

>[!NOTE]
>
>Si une page est déjà publiée, la publication est automatiquement annulée avant la suppression.

### Verrouillage d’une page {#locking-a-page}

Vous pouvez [verrouiller/déverrouiller une page](/help/sites-cloud/authoring/page-editor/edit-content.md#locking-a-page) à partir d’une console ou lors de la modification d’une page individuelle. Les deux environnements indiquent également si une page est verrouillée ou non.

![Bouton Verrouiller](/help/sites-cloud/authoring/assets/lock.png)
![Bouton Déverrouiller](/help/sites-cloud/authoring/assets/unlock.png)

### Création d’un dossier {#creating-a-new-folder}

Vous pouvez créer des dossiers pour classer vos fichiers et vos pages.

1. Ouvrez [la console **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Accédez à l’emplacement qui vous intéresse.
1. Pour ouvrir la liste des options, sélectionnez **Créer** dans la barre d’outils
1. Sélectionnez **Dossier** pour ouvrir la boîte de dialogue. Vous pouvez y entrer le **nom** et le **titre** :

   ![Créer un dossier](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Pour créer le dossier, sélectionnez **Créer**.

>[!NOTE]
>
>* Les dossiers sont également soumis aux [Conventions de dénomination de page](#page-naming-conventions) lors de la spécification du nom du nouveau dossier.
>* Les dossiers ne peuvent être créés que directement sous **Sites** ou sous d’autres dossiers. Ils ne peuvent pas être créés sous une page.
>* Les opérations standard (déplacer, copier, coller, supprimer, publier, dépublier et afficher/modifier les propriétés) peuvent être effectuées sur un dossier.
>* Dans une Live Copy, les dossiers ne peuvent pas être sélectionnés.
