---
title: Modification de programmes
description: Découvrez comment modifier vos programmes de production et d’environnement de test pour ajuster leurs options après les avoir créés.
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 4%

---


# Modification de programmes {#editing-programs}

Les utilisateurs disposant des autorisations requises peuvent modifier [programmes de production créés dans votre organisation](creating-production-programs.md) ainsi que [programmes sandbox créés dans votre entreprise.](creating-sandbox-programs.md) En éditant un programme, vous pouvez :

* Ajoutez la solution Sites à un programme existant avec Assets et vice versa.
* Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
* Ajoutez un second droit de solution inutilisé à un programme existant ou en tant que nouveau programme.
* Supprimez les programmes Sandbox.

>[!NOTE]
>
>Vous devez être membre du **Propriétaire de l’entreprise** rôle permettant de modifier des programmes ou de supprimer des programmes sandbox.

Pour modifier un programme, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme que vous souhaitez éditer pour en afficher le détail.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Modifier le programme**.

   ![Option Modifier le programme](assets/edit-program-overview.png)

1. Le **Modifier le programme** affiche deux onglets : **Général** et **Solutions et modules complémentaires**. Sélectionnez la **Général** pour modifier le nom et la description du programme.

   * Au moins une solution doit être sélectionnée pour un programme.

   ![Onglet Général](assets/edit-program-prod1.png)

1. Sélectionnez la **Solutions et modules complémentaires** pour modifier les solutions du programme.

   ![Solutions sélectionnées](assets/edit-prg.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, tels que la sélection de la variable **Commerce** option de module complémentaire sous **Sites**.

   ![Modifier les modules complémentaires](assets/edit-program-add-on.png)

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications dans le programme.

Une fois vos mises à jour effectuées, si les solutions sélectionnées ont été modifiées, ces modifications prennent effet après le prochain déploiement.

## Suppression de programmes Sandbox {#delete-sandbox-program}

La suppression d’un programme d’environnement de test supprime tous les environnements et pipelines qui y sont associés.

>[!TIP]
>
>Utilisateurs avec la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** les rôles peuvent également supprimer leurs environnements de production et d’évaluation au lieu de l’ensemble du programme sandbox.

Pour supprimer un programme Sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme que vous souhaitez éditer pour en afficher le détail.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Supprimer le programme**.

   ![Option Supprimer le programme](assets/delete-sandbox1.png)

Vous pouvez également cliquer sur le bouton représentant des points de suspension sur la carte de votre programme dans la page d’aperçu de Cloud Manager et sélectionner **Supprimer le programme**.

![Suppression d’un environnement de test d’une carte de programme](assets/delete-sandbox2.png)

>[!NOTE]
>
>Seuls les programmes Sandbox peuvent être supprimés. Les programmes de production ne peuvent pas être supprimés.