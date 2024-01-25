---
title: Gestion et modification des programmes
description: Découvrez comment modifier vos programmes de production et Sandbox pour ajuster leurs options après les avoir créés.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: 2dfae31e32d375c82c4f690624e48f7f09feb4df
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 19%

---


# Gestion et modification des programmes {#editing-programs}

La variable **Mes programmes** fournit un aperçu de tous les programmes auxquels vous avez accès. Lors de la sélection d’un programme individuel, la variable **Aperçu du programme** fournit des détails sur le programme en un coup d’oeil.

Dans la **Aperçu du programme**, les utilisateurs disposant des autorisations requises peuvent modifier [programmes de production créés dans votre organisation](creating-production-programs.md) et [programmes sandbox créés dans votre entreprise.](creating-sandbox-programs.md) En éditant un programme, vous pouvez :

* Ajoutez la solution Sites à un programme existant avec Assets et inversement.
* Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
* Ajoutez un second droit de solution inutilisé à un programme existant ou en tant que nouveau programme.
* Supprimer les programmes Sandbox.

## Autorisations {#permissions}

Vous devez être membre de la fonction **Propriétaire de l’entreprise** rôle permettant de modifier des programmes ou de supprimer des programmes Sandbox, ainsi que d’accéder au tableau de bord de licence.

## Mes programmes {#my-programs}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. La variable **Mes programmes** affiche la liste de tous les programmes auxquels vous avez accès en tant que mosaïques.

![Page Mes programmes](/help/implementing/cloud-manager/assets/my-programs.png)

### Appel à l’action {#cta}

En haut de la page se trouve un appel à l’action pertinent pour le statut de votre organisation. Par exemple, si vous avez correctement configuré vos programmes, les statistiques de vos activités au cours des 90 derniers jours peuvent s’afficher, notamment :

* Nombre de [déploiements](/help/implementing/cloud-manager/deploy-code.md)
* Nombre de [problèmes de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) identifié
* Nombre de versions

Si vous ne commencez que la configuration de votre organisation, vous pouvez obtenir des conseils sur les étapes suivantes ou les ressources de documentation.

### Onglet Programmes {#programs-tab}

La variable **Programmes** répertorie les cartes représentant chaque programme auquel vous avez accès. Appuyez ou cliquez sur une carte pour accéder au **Aperçu du programme** page du programme pour plus d’informations sur le programme.

Utilisez les options de tri pour mieux trouver le programme dont vous avez besoin.

![Options de tri](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Trier par
   * Date de création (par défaut)
   * Nom du programme
   * Statut
* ascendant (par défaut) / descendant
* Affichage de la grille (par défaut)
* Vue Liste

### Onglet Licence {#license-tab}

La variable **Licence** permet d’accéder rapidement à la fonction [Tableau de bord de la licence.](/help/implementing/cloud-manager/license-dashboard.md)

## Aperçu du programme {#program-overview}

Une fois que vous avez sélectionné un programme dans la **[Mes programmes](#my-programs)** , Cloud Manager ouvre la variable **Aperçu du programme** pour le programme sélectionné.

![Page Aperçu du programme](/help/implementing/cloud-manager/assets/program-overview.png)

Appuyez ou cliquez sur le nom du programme dans le coin supérieur gauche de la page pour passer rapidement à un autre programme ou revenir au **[Mes programmes](#my-programs)** page. Vous pouvez également [modifier le programme sélectionné ;](#editing) ou [ajoutez un programme.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

![Sélecteur de programmes](/help/implementing/cloud-manager/assets/program-switcher.png)

L’appel à l’action en haut de l’écran vous donnera des informations utiles en fonction de l’état de votre programme. Pour un nouveau programme, vous pouvez voir les prochaines étapes proposées ainsi qu&#39;un rappel d&#39;une date de mise en service, [défini lors de la création du programme.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)

![Appel à l’action pour un nouveau programme](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Pour un programme actif, l’état de votre dernier déploiement avec des liens pour plus de détails et le démarrage d’un nouveau déploiement.

![Appel à l&#39;action](/help/implementing/cloud-manager/assets/info-banner.png)

**Environnements** et **Pipelines** les cartes donnent un aperçu rapide des deux dans le programme sélectionné.

![Cartes](/help/implementing/cloud-manager/assets/environments-pipelines.png)

La variable **Performances** La carte donne un aperçu de la variable **[Tableau de bord du réseau CDN.](/help/implementing/cloud-manager/cdn-performance.md)**

![Carte des performances](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

## Modifier un programme {#editing}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](#my-programs)** , cliquez sur le programme à modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Modifier le programme**.

   ![Option Modifier le programme](assets/edit-program-overview.png)

1. La variable **Modifier le programme** s’ouvre sur la page **Général** .

   ![Onglet Général](assets/edit-program-prod1.png)

1. Les options disponibles pour la modification du programme sont les mêmes que lors de la création du programme.
   * Veuillez consulter les documents [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) et [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) pour plus d’informations sur les différentes options.
   * [Options supplémentaires](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) peut être disponible pour votre programme de production en fonction des droits de votre organisation.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications dans le programme.

Les modifications apportées au programme sont enregistrées.

>[!NOTE]
>
>Chaque fois qu’un programme est modifié, y compris l’ajout ou la suppression d’une solution ou d’un module complémentaire, ces modifications prennent effet après le prochain déploiement.

## Suppression de programmes Sandbox {#delete-sandbox-program}

La suppression d’un programme d’environnement de test supprime tous les environnements et pipelines qui y sont associés.

>[!TIP]
>
>Les utilisateurs avec des rôles de **Propriétaire de l’entreprise** ou **Responsable du déploiement** peuvent également supprimer leurs environnements de production et d’évaluation plutôt que l’ensemble du programme Sandbox.

Pour supprimer un programme sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](#my-programs)** , cliquez sur le programme à modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Supprimer le programme**.

   ![Option Supprimer le programme](assets/delete-sandbox1.png)

Vous pouvez également cliquer sur le bouton représentant des points de suspension sur la vignette de votre programme dans la page de présentation de Cloud Manager et sélectionner **Supprimer le programme**.

![Supprimer Sandbox d’une vignette de programme](assets/delete-sandbox2.png)

>[!NOTE]
>
>Seuls les programmes Sandbox peuvent être supprimés. Les programmes de production ne peuvent pas être supprimés.
