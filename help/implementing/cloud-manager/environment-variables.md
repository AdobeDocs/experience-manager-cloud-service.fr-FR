---
title: Variables d’environnement Cloud Manager
description: Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Elle sont fournies à l’environnement d’exécution, pour une utilisation dans la configuration OSGi.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 100%

---

# Variables d’environnement Cloud Manager {#environment-variables}

Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Elles sont fournies à l’environnement d’exécution et peuvent être utilisés dans des configurations OSGi. Les variables d’environnement peuvent être des valeurs spécifiques à un environnement ou des secrets d’environnement, en fonction de ce qui est modifié.

## Présentation {#overview}

Les variables d’environnement offrent de nombreux avantages aux utilisateurs d’AEM as a Cloud Service :

* Elles permettent au comportement de votre code et de votre application de varier en fonction du contexte et de l’environnement. Par exemple, elles peuvent être utilisées pour activer différentes configurations dans l’environnement de développement par rapport aux environnements de production ou d’évaluation, ceci afin d’éviter des erreurs coûteuses.
* Elles ne doivent être configurées et paramétrées qu’une seule fois, et peuvent être mises à jour et supprimées si nécessaire.
* Leurs valeurs peuvent être mises à jour à tout moment et prennent effet immédiatement sans qu’il faille apporter de modifications au code ni procéder à des déploiements.
* Elles peuvent séparer le code de la configuration et supprimer la nécessité d’inclure des informations sensibles dans le contrôle de version.
* Elles améliorent la sécurité de l’application AEM as a Cloud Service puisqu’elles se trouvent en dehors du code.

Les cas d’utilisation les plus courants des variables d’environnement incluent :

* La connexion de votre application AEM avec différents points d’entrée externes.
* L’utilisation d’une référence lors du stockage des mots de passe au lieu de le faire directement dans la base de code.
* Lorsque plusieurs environnements de développement existent dans un programme et que certaines configurations diffèrent d’un environnement à l’autre.

## Ajouter des variables d’environnement {#add-variables}

1. Connectez-vous à Adobe Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager répertorie les différents programmes disponibles. Sélectionnez celui que vous souhaitez gérer.
1. Sélectionnez l’onglet **Environnements** pour le programme choisi, puis sélectionnez l’environnement pour lequel vous souhaitez créer une variable d’environnement dans le panneau de navigation de gauche.
1. Dans le détail de l’environnement, sélectionnez l’onglet **Configuration**, puis sélectionnez **Ajouter** pour ouvrir la boîte de dialogue **Configuration de l’environnement**.
   * Si vous ajoutez une variable d’environnement pour la première fois, le bouton **Ajouter une configuration** s’affiche au centre de la page. Vous pouvez utiliser ce bouton ou **Ajouter** pour ouvrir la boîte de dialogue **Configuration de l’environnement**.

   ![Onglet Configuration](assets/configuration-tab.png)

1. Saisissez les détails de la variable.
   * **Nom**.
   * **Valeur**.
   * **Service appliqué** : définit le service (auteur/publication/prévisualisation) auquel la variable s’applique, ou si elle s’applique à tous les services.
   * **Type** : définit si la variable est une variable normale ou un secret.

   ![Ajouter une variable](assets/add-variable.png)

1. Après avoir saisi la nouvelle variable, vous devez sélectionner **Ajouter** dans la dernière colonne de la ligne contenant la nouvelle variable.
   * Vous pouvez saisir plusieurs variables à la fois en saisissant une nouvelle ligne et en sélectionnant **Ajouter**.

   ![Enregistrer des variables](assets/save-variables.png)

1. Sélectionnez **Enregistrer** pour conserver vos variables.

Un indicateur avec le statut **Mise à jour en cours** s’affiche en haut du tableau et en regard de la variable nouvellement ajoutée pour indiquer que l’environnement est en cours de mise à jour avec la configuration. Une fois cette opération terminée, la nouvelle variable d’environnement est visible dans le tableau.

![Mettre à jour les variables](assets/updating-variables.png)

>[!TIP]
>
>Si vous souhaitez ajouter plusieurs variables, il est recommandé d’ajouter la première variable, puis d’utiliser le bouton **Ajouter** dans la boîte de dialogue **Configuration de l’environnement** pour ajouter les variables supplémentaires. De cette façon, vous pouvez les ajouter en une seule mise à jour de lʼenvironnement.

## Mettre à jour les variables d’environnement {#update-variables}

Une fois les variables d’environnement créées, vous pouvez les mettre à jour à l’aide du bouton **Ajouter/mettre à jour** pour lancer la boîte de dialogue **Configuration de l’environnement**.

1. Connectez-vous à Adobe Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager répertorie les différents programmes disponibles. Sélectionnez celui que vous souhaitez gérer.
1. Sélectionnez l’onglet **Environnements** pour le programme choisi, puis sélectionnez l’environnement pour lequel vous souhaitez créer une variable d’environnement dans le panneau de navigation de gauche.
1. Dans le détail de l’environnement, sélectionnez l’onglet **Configuration**, puis sélectionnez **Ajouter/mettre à jour** dans le coin supérieur droit pour ouvrir la boîte de dialogue **Configuration de l’environnement**.

   ![Bouton Ajouter/mettre à jour pour les variables](assets/add-update-variables.png)

1. À l’aide du bouton représentant des points de suspension qui se trouve dans la dernière colonne de la ligne de la variable à modifier, sélectionnez **Modifier** ou **Supprimer**.

   ![Modifier ou supprimer une variable](assets/edit-delete-variable.png)

1. Modifiez la variable d’environnement selon vos besoins.
   * Lors de la modification, le bouton représentant des points de suspension est remplacé par des options permettant de revenir à la valeur initiale ou de confirmer votre modification.
   * Lors de la modification des secrets, les valeurs peuvent seulement être mises à jour, mais pas visualisées.

   ![Modifier la variable](assets/edit-variable.png)

1. Une fois toutes les modifications de configuration requises effectuées, cliquez sur **Enregistrer**.

[Comme lors de l’ajout de variables](#add-variables), un indicateur avec le statut **Mise à jour** sʼaffiche en haut du tableau et en regard de la ou des variables nouvellement mises à jour pour indiquer que l’environnement est mis à jour avec la configuration. Une fois l’opération terminée, la ou les variables d’environnement mises à jour sont visibles dans le tableau.

>[!TIP]
>
>Si vous souhaitez mettre à jour plusieurs variables, il est recommandé d’utiliser la boîte de dialogue **Configuration de l’environnement** pour mettre à jour toutes les variables nécessaires en une seule fois avant d’appuyer ou de cliquer sur **Enregistrer**. De cette façon, vous pouvez les ajouter en une seule mise à jour de lʼenvironnement.
