---
title: Appliquer des workflows aux pages
description: Lors de la création, vous pouvez appeler des workflows pour agir sur vos pages. Il est également possible d’appliquer plusieurs workflows.
exl-id: 86e71f0e-e53e-40bc-901d-2a1ab347bd0a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 83%

---

# Appliquer des workflows aux pages {#applying-workflows-to-pages}

Lors de la création, vous pouvez appeler des workflows pour agir sur vos pages. Il est également possible d’appliquer plusieurs workflows.

Lorsque vous appliquez le workflow, vous spécifiez les informations suivantes :

* Workflow à appliquer.
   * Vous pouvez appliquer n’importe quel workflow (auquel vous avez accès, selon les affectations réalisées par votre administrateur AEM).
* Éventuellement, un titre qui permet d’identifier l’instance de workflow dans la boîte de réception d’une personne utilisatrice.
* La payload du workflow. Il peut s’agir d’une ou de plusieurs pages.

Les workflows peuvent être démarrés à partir des interfaces suivantes :

* [via la console Sites](#starting-a-workflow-from-the-sites-console).
* [lors de la modification d’une page, via Informations sur la page](#starting-a-workflow-from-the-page-editor).

>[!NOTE]
>
>Voir également :
>
>* Application de workflows à des ressources de gestion des ressources numériques.
>* [Utilisation des workflows de projet](/help/sites-cloud/authoring/projects/workflows.md).

<!-- 
>* [How to apply workflows to DAM assets](/help/assets/assets-workflow.md).
>* [Working with Project Workflows](/help/sites-cloud/authoring/projects/workflows.md).
-->

>[!NOTE]
>
>Les administrateurs AEM peuvent commencer des workflows à l’aide de plusieurs autres méthodes.

<!-- 
>AEM administrators can [start workflows using several other methods](/help/sites-administering/workflows-starting.md).
-->

## Démarrage d’un workflow à partir de la console Sites {#starting-a-workflow-from-the-sites-console}

Vous pouvez démarrer un workflow des deux manières suivantes :

* [Utiliser l’option Créer de la barre d’outils Sites](#starting-a-workflow-from-the-sites-toolbar).
* [Utiliser le rail Chronologie de la console Sites](#starting-a-workflow-from-the-timeline).

Dans les deux cas, vous devez [spécifier les détails du workflow dans l’assistant Créer un workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Démarrage d’un workflow à partir de la barre d’outils Sites {#starting-a-workflow-from-the-sites-toolbar}

Vous pouvez démarrer un workflow à partir de la barre d’outils de la console **Sites** :

1. Recherchez et sélectionnez la page voulue.

1. À partir de l’option **Créer** de la barre d’outils, vous pouvez maintenant sélectionner **Workflow**.

   ![Création d’un workflow à partir de la barre d’outils](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. L’assistant **Créer un workflow** vous aidera à [spécifier les détails du workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Démarrage d’un workflow à partir de la chronologie {#starting-a-workflow-from-the-timeline}

Dans la **Chronologie**, vous pouvez démarrer un workflow à appliquer à la ressource sélectionnée.

1. [Sélectionnez la ressource](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) et ouvrez la [Chronologie](/help/sites-cloud/authoring/basic-handling.md#timeline) (ou ouvrez la chronologie, puis sélectionnez la ressource).
1. La pointe de la flèche située en regard du champ de commentaire peut être utilisée pour afficher **Démarrer le workflow** :

   ![Créer un workflow à partir de la chronologie](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. L’assistant **Créer un workflow** vous aidera à [spécifier les détails du workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Spécification des détails du workflow dans l’assistant Créer un workflow {#specifying-workflow-details-in-the-create-workflow-wizard}

L’assistant **Créer un workflow** vous aide à sélectionner le workflow et à indiquer les détails requis.

Ouvrez l’assistant **Créer un workflow** de l’une des manières suivantes :

* [Utiliser l’option Créer de la barre d’outils Sites](#starting-a-workflow-from-the-sites-toolbar).
* [Utiliser le rail Chronologie de la console Sites](#starting-a-workflow-from-the-timeline).

Indiquez les détails suivants :

1. L’étape **Propriétés** permet de définir les options de base du workflow :

   * **Modèle de workflow**
   * **Titre du workflow**

      * Vous pouvez donner un titre à l’instance afin de l’identifier plus tard.

   Selon le modèle de workflow, les options suivantes sont également disponibles. Elles permettent de conserver le package créé en tant que payload une fois le workflow terminé.

   * **Conserver le package de workflow**
   * **Titre de package**

      * Donnez un titre au package afin de l’identifier plus tard.

   >[!NOTE]
   >
   >L’option **Conserver le package de workflow** est disponible lorsque le workflow a été configuré pour la prise en charge multi-ressource et que plusieurs ressources ont été sélectionnées.

   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   Une fois que vous avez terminé, cliquez sur **Suivant** pour continuer.

   ![Spécification des propriétés de workflow](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. À l’étape **Domaine**, vous pouvez sélectionner :

   * **Ajoutez du contenu** pour ouvrir le [navigateur de chemins d’accès](/help/sites-cloud/authoring/path-selection.md) et sélectionner des ressources supplémentaires. Lorsque vous êtes dans le navigateur, sélectionnez **Sélectionner** pour ajouter le contenu à l’instance de workflow.

   * Une ressource existante pour afficher d’autres actions :

      * **Inclure les enfants** pour indiquer que les enfants de la ressource seront inclus dans le workflow.
Une boîte de dialogue s’ouvre pour vous permettre d’affiner la sélection en fonction des éléments suivants :

         * Inclure seulement les enfants immédiats
         * Inclure seulement les pages modifiées
         * Inclure seulement les pages déjà publiées

        Tous les enfants spécifiés sont ajoutés à la liste des ressources auxquelles le workflow s’appliquera.

      * **Supprimer la sélection** pour supprimer cette ressource du workflow.

   ![Définir la portée du workflow](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Si vous ajoutez des ressources, vous pouvez utiliser l’option **Retour** pour ajuster le paramètre **Conserver le package de workflow** à l’étape **Propriétés**.

1. Utilisez l’option **Créer** pour fermer l’assistant et créer l’instance du workflow. Une notification s’affiche dans la console Sites.

## Démarrage d’un workflow à partir de l’éditeur de page {#starting-a-workflow-from-the-page-editor}

Lorsque vous modifiez une page, vous pouvez sélectionner **Informations sur la page** dans la barre d’outils. Le menu déroulant contient l’option **Démarrer dans le workflow**. Une boîte de dialogue s’ouvre, dans laquelle vous pouvez spécifier le workflow requis, ainsi qu’un titre si nécessaire :

![Démarrage d’un workflow à partir de l’éditeur de page](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
