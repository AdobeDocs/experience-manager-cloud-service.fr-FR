---
title: Ajout d’un pipeline Edge Delivery
description: Découvrez comment ajouter un pipeline Edge Delivery pour créer et déployer votre code dans les environnements de production.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: false
index: false
hidefromtoc: false
exl-id: 5ad342fa-dd71-4105-a9cb-2d999d402780
source-git-commit: b367e7d62596c33a4ba399008e856a97d12fb45b
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 4%

---

# Ajout d’un pipeline Edge Delivery {#configure-production-pipeline}

Découvrez comment configurer les pipelines Edge Delivery pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement intermédiaire. Lors de la validation, il déploie le même code dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer les pipelines de production.

>[!IMPORTANT]
>
>Un pipeline Edge Delivery ne peut pas être configuré tant que les actions suivantes n’ont pas été effectuées :
>
>* Un programme contenant un site Edge Delivery Services et un domaine mappé est créé. Sinon, l’option **Ajouter un pipeline Edge Delivery** apparaît désactivée dans l’interface utilisateur et une info-bulle explique les exigences manquantes. Voir [Création d’un site Edge Delivery dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)
>* Le référentiel Git comporte au moins une branche. Voir [Gestion des référentiels dans Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).
>* Les environnements de production et d’évaluation sont créés. Voir [Présentation des pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

<!-- CMGR‑69680 -->


Avant de commencer à déployer votre code, configurez les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

**Pour ajouter un pipeline Edge Delivery, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [experience.adobe.com/experiencemanager](https://my.cloudmanager.adobe.com/) puis, dans le panneau de gauche, cliquez sur **Cloud Manager**.

1. Sélectionnez l’organisation de votre choix.

1. Sur la page **Mes programmes**, sélectionnez le programme de votre choix.

   ![Page Mes programmes dans Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. Utilisez l’une des méthodes suivantes :

   * **Ajouter un pipeline Edge Delivery à partir de la carte Pipelines**

      1. Dans le rail de gauche, sous **Programme**, cliquez sur **![Icône Aperçu](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [Aperçu](/help/implementing/cloud-manager/navigation.md#my-programs)**.
      1. Sur la page **Aperçu du programme**, sous la vignette **Pipelines**, cliquez sur **![Signe plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)Ajouter**, puis sélectionnez **Ajouter un pipeline Edge Delivery**.

         ![Vignette Pipelines de la page Aperçu du programme ](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

   * **Ajouter un pipeline Edge Delivery à partir de la page Pipelines**

      1. Dans le rail de gauche, sous **Programme**, cliquez sur **![Icône de workflow ou Icône de pipelines](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Pipelines**.
      1. Sur la page Pipelines, près du coin supérieur droit, cliquez sur **Ajouter un pipeline** > **Ajouter un pipeline Edge Delivery**.

         ![Page Pipelines avec le bouton Ajouter un pipeline ](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

1. Dans la boîte de dialogue **Ajouter un pipeline Edge Delivery**, dans le champ de texte **Nom du pipeline**, saisissez un libellé de pipeline descriptif.

   ![Boîte de dialogue Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. Sélectionnez l’option de pipeline **Déclencheur de déploiement** de votre choix.

   * **Manuel** - Vous démarrez le déploiement.
   * **Lors des modifications Git** - les validations Git démarrent le déploiement automatiquement. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

1. Cliquez sur **Continuer**.

1. Sous **Code Source**, définissez les options suivantes :

   * **Environnement de déploiement** - Affiche le champ de l’environnement cible ; reste en lecture seule.

   * **Référentiel** - Utilisez la liste déroulante pour pointer le pipeline vers le référentiel Git exact qui stocke la configuration Edge Delivery.

     Voir aussi [Ajouter et gérer des référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Utilisez la liste déroulante pour sélectionner une branche spécifique dans le référentiel sélectionné. Si nécessaire, cliquez sur ![icône de recyclage ou icône d’actualisation](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) pour recharger la liste déroulante Branche Git après les notifications push récentes
   * **Emplacement du code** - Définit le chemin du dossier à l’intérieur du référentiel où commence le code prêt pour le pipeline ( `/` est égal à la racine du référentiel).

   ![Configurer le pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. Cliquez sur **Enregistrer**.

Vous pouvez désormais [gérer votre pipeline](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme** ou à partir de la page **Pipelines**.
