---
title: Créer des programmes Sandbox
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme Sandbox à des fins de formation, de démonstration, de point de vente ou à d’autres fins hors production.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 87836c7f28c9e3c8269fac073f46c53ce73fecfa
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 15%

---

# Créer des programmes Sandbox {#create-sandbox-program}

Un programme Sandbox est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation, et n’est pas destiné à transporter du trafic en direct. Voir [Présentation des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

Pour en savoir plus sur les types de programme, consultez le document [Présentation des programmes et des types de programme](program-types.md).

## Création d’un programme Sandbox {#create}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, près du coin supérieur droit, cliquez sur **Ajouter un programme**.

   ![Page de destination de Cloud Manager.](assets/log-in.png)

1. Dans l’assistant *Créons votre programme*, dans le champ de texte **Nom du programme**, saisissez le nom que vous souhaitez donner au programme.

1. Sous **Objectif du programme**, sélectionnez ![Icône de baguette magique](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MagicWand_18_N.svg) **Configurer un sandbox**.

   ![Création d’un type de programme](assets/create-sandbox.png)

1. (Facultatif) Dans le coin inférieur droit de la boîte de dialogue de l’assistant, effectuez l’une des opérations suivantes :

   * Faites glisser et déposez un fichier image sur la cible ![Icône Image](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **Ajouter une image de programme**.
   * Cliquez sur ![Icône Image](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **Ajouter une image de programme**, puis sélectionnez une image dans l’explorateur de fichiers.
   * Cliquez sur ![Icône Supprimer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) pour supprimer une image que vous avez ajoutée.

1. Cliquez sur **Continuer**.

1. Dans la zone de liste **Solutions et modules complémentaires**, sélectionnez une ou plusieurs solutions à inclure dans le programme.

   * Cliquez sur le chevron situé à gauche du nom d’une solution pour afficher tous les modules complémentaires facultatifs disponibles que vous souhaitez inclure avec une solution sélectionnée.
   * Les solutions **Sites**, **Assets** et **Edge Delivery Services** sont toujours sélectionnées par défaut lorsque vous créez un programme Sandbox. Vous ne pouvez pas les désélectionner.

   ![Sélection de solutions et de modules complémentaires pour une sandbox](assets/sandbox-solutions-add-ons.png)

1. Cliquez sur **Créer**. Cloud Manager crée votre programme sandbox et l’affiche sur la page de destination pour la sélection.

![Création d’une sandbox à partir de la page d’aperçu](assets/sandbox-setup.png)

## Accès aux sandbox {#access}

Une fois qu’un nouveau programme Sandbox est créé, vous pouvez afficher les détails de la configuration de votre sandbox et accéder à l’environnement en consultant la page de présentation du programme.

1. Sur la page de destination de Cloud Manager, dans le programme Sandbox, cliquez sur ![icône de liste plus petite](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) sur le programme Sandbox que vous avez créé.

   ![Accès à l’aperçu du programme](assets/program-overview-sandbox.png)

1. Une fois l’étape de création du projet terminée, vous pouvez cliquer sur le lien **Accéder aux informations sur le référentiel** pour pouvoir utiliser votre référentiel Git.

   ![Configuration du programme](assets/create-program4.png)

   >[!TIP]
   >
   >Pour en savoir plus sur l’accès à votre référentiel Git et sa gestion, voir [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Une fois l’environnement de développement créé, vous pouvez cliquer sur **Accéder à AEM** et vous connecter à AEM.

   ![Lien Accès à AEM](assets/create-program5.png)

1. Une fois terminé le déploiement du pipeline hors production vers le développement, l’assistant de call-to-action vous permet d’accéder à l’environnement de développement AEM ou de déployer du code dans l’environnement de développement.

   ![Déploiement d’une Sandbox](assets/create-program-setup-deploy.png)

>[!TIP]
>
>Consultez [Navigation dans l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/navigation.md) pour plus d’informations sur la navigation dans Cloud Manager et sur la console **Mes programmes**.
