---
title: Variables d’environnement Cloud Manager
description: Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager et fournies à l’environnement d’exécution, à utiliser dans la configuration OSGi.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 1%

---

# Variables d’environnement Cloud Manager {#environment-variables}

Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Ils sont fournis à l’environnement d’exécution et peuvent être utilisés dans des configurations OSGi. Les variables d’environnement peuvent être des valeurs spécifiques à un environnement ou des secrets d’environnement, en fonction de ce qui est modifié.

## Présentation {#overview}

Les variables d’environnement offrent de nombreux avantages aux utilisateurs d’AEM as a Cloud Service :

* Elles permettent au comportement de votre code et de votre application de varier en fonction du contexte et de l’environnement. Par exemple, ils peuvent être utilisés pour activer différentes configurations dans l’environnement de développement par rapport aux environnements de production ou d’évaluation afin d’éviter des erreurs coûteuses.
* Ils ne doivent être configurés et configurés qu’une seule fois et peuvent être mis à jour et supprimés si nécessaire.
* Leurs valeurs peuvent être mises à jour à tout moment et prennent effet immédiatement sans qu’il faille apporter de modifications au code ni procéder à des déploiements.
* Ils peuvent séparer le code de la configuration et supprimer la nécessité d’inclure des informations sensibles dans le contrôle de version.
* Elles améliorent la sécurité de l’application as a Cloud Service AEM puisqu’elles se trouvent en dehors du code.

Les cas d’utilisation standard pour l’utilisation de variables d’environnement incluent :

* Connexion de l’application AEM à différents points de terminaison externes
* Utilisation d’une référence lors du stockage des mots de passe plutôt que directement dans la base de code
* Lorsque plusieurs environnements de développement existent dans un programme et que certaines configurations diffèrent d’un environnement à l’autre.

## Ajout de variables d’environnement {#add-variables}

1. Connectez-vous à Adobe Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager répertorie les différents programmes disponibles. Sélectionnez celle que vous souhaitez gérer.
1. Sélectionnez la **Environnements** pour le programme sélectionné, sélectionnez ensuite l’environnement pour lequel vous souhaitez créer une variable d’environnement dans le panneau de navigation de gauche.
1. Dans le détail de l&#39;environnement, sélectionnez la variable **Configuration** puis sélectionnez **Ajouter** pour ouvrir le **Configuration de l’environnement** boîte de dialogue.
   * Si vous ajoutez une variable d’environnement pour la première fois, un événement **Ajouter une configuration** au centre de la page. Vous pouvez utiliser ce bouton ou **Ajouter** pour ouvrir le **Configuration de l’environnement** boîte de dialogue.

   ![Onglet Configuration](assets/configuration-tab.png)

1. Saisissez les détails de la variable.
   * **Nom**
   * **Valeur**
   * **Service appliqué** - Définit pour quel service (auteur/publication/aperçu) la variable s’applique ou si elle s’applique à tous les services.
   * **Type** - Définit si la variable est une variable normale ou un secret

   ![Ajouter une variable](assets/add-variable.png)

1. Après avoir saisi la nouvelle variable, vous devez sélectionner **Ajouter** dans la dernière colonne de la ligne contenant la nouvelle variable.
   * Vous pouvez saisir plusieurs variables à la fois en entrant une nouvelle ligne et en sélectionnant **Ajouter**.

   ![Enregistrer des variables](assets/save-variables.png)

1. Sélectionner **Enregistrer** pour conserver vos variables.

Indicateur avec le statut **Mise à jour** s’affiche en haut du tableau et en regard de la variable nouvellement ajoutée pour indiquer que l’environnement est mis à jour avec la configuration. Une fois l’opération terminée, la nouvelle variable d’environnement est visible dans le tableau.

![Mise à jour des variables](assets/updating-variables.png)

>[!TIP]
>
>Si vous souhaitez ajouter plusieurs variables, il est recommandé d’ajouter la première variable, puis d’utiliser la variable **Ajouter** dans le **Configuration de l’environnement** pour ajouter les variables supplémentaires. Vous pouvez ainsi les ajouter avec une mise à jour de l’environnement.

## Mise à jour des variables d’environnement {#update-variables}

Une fois les variables d’environnement créées, vous pouvez les mettre à jour à l’aide de la variable **Ajouter/Mettre à jour** pour lancer le **Configuration de l’environnement** boîte de dialogue.

1. Connectez-vous à Adobe Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager répertorie les différents programmes disponibles. Sélectionnez celle que vous souhaitez gérer.
1. Sélectionnez la **Environnements** pour le programme sélectionné, sélectionnez ensuite l’environnement pour lequel vous souhaitez créer une variable d’environnement dans le panneau de navigation de gauche.
1. Dans le détail de l&#39;environnement, sélectionnez la variable **Configuration** puis sélectionnez **Ajouter/mettre à jour** dans la partie supérieure droite pour ouvrir le **Configuration de l’environnement** boîte de dialogue.

   ![Bouton Ajouter/Mettre à jour pour les variables](assets/add-update-variables.png)

1. À l’aide du bouton représentant des points de suspension dans la dernière colonne de la ligne de la variable que vous souhaitez modifier, sélectionnez **Modifier** ou **Supprimer**.

   ![Modification ou suppression d’une variable](assets/edit-delete-variable.png)

1. Modifiez la variable d’environnement selon vos besoins.
   * Lors de la modification, le bouton représentant des points de suspension se transforme en options pour revenir à la valeur d’origine ou confirmer votre modification.
   * Lors de la modification de secrets, les valeurs ne peuvent être mises à jour que et non affichées.

   ![Modifier la variable](assets/edit-variable.png)

1. Une fois toutes les modifications de configuration requises effectuées, sélectionnez **Enregistrer**.

[Comme pour l’ajout de variables,](#add-variables) un indicateur avec le statut **Mise à jour** s’affiche en haut du tableau et en regard des variables nouvellement mises à jour pour indiquer que l’environnement est mis à jour avec la configuration. Une fois l’opération terminée, la ou les variables d’environnement mises à jour sont visibles dans le tableau.

>[!TIP]
>
>Si vous souhaitez mettre à jour plusieurs variables, il est recommandé d’utiliser la variable **Configuration de l’environnement** pour mettre à jour toutes les variables nécessaires à la fois avant d’appuyer ou de cliquer sur **Enregistrer**. Vous pouvez ainsi les ajouter avec une mise à jour de l’environnement.
