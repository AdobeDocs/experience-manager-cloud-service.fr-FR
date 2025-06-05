---
title: Ajout d’un pipeline Edge Delivery
description: Découvrez comment ajouter un pipeline Edge Delivery pour créer et déployer votre code dans les environnements de production.
index: false
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Utilisateur(Utilisatrice) Précoce" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: true
hidefromtoc: true
source-git-commit: acb919474bfe4285c889b8646f731285f5b759ba
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 38%

---



# Ajout d’un pipeline Edge Delivery {#configure-production-pipeline}

Découvrez comment configurer les pipelines Edge Delivery pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement intermédiaire. Lors de la validation, il déploie le même code dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer les pipelines de production.

>[!NOTE]
>
>Un pipeline de production ne peut pas être configuré tant que les conditions suivantes ne sont pas réunies :
>
>* Le programme est créé.
>* Le référentiel Git comporte au moins une branche.
>* Les environnements de production et d’évaluation sont créés.

Avant de commencer à déployer votre code, configurez les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajouter un nouveau pipeline Edge Delivery {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline production en suivant ces étapes.

>[!TIP]
>
>Avant de configurer un pipeline front-end, consultez le [Parcours de création rapide de site d’AEM](/help/journey-sites/quick-site/overview.md) pour obtenir un guide complet à travers l’outil de création rapide de site d’AEM, facile à utiliser. Ce parcours peut vous aider à rationaliser le développement front-end de votre site AEM, ce qui vous permet de personnaliser rapidement votre site sans aucune connaissance du serveur principal AEM.

**Pour ajouter un nouveau pipeline Edge Delivery, procédez comme suit**

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur **Ajouter** pour sélectionner **Ajouter un pipeline de production**.

   ![Carte Pipelines dans l’aperçu du Gestionnaire de programmes](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. La boîte de dialogue **Ajouter un pipeline de production** s’affiche. Fournissez une **Nom du pipeline** pour identifier votre pipeline avec les options suivantes. Cliquez sur **Continuer**.

   **Déclencheur de déploiement** - Vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** - Démarrez le pipeline manuellement.
   * **Lors des modifications Git** - Démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le **responsable de déploiement** peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** - Paramètre par défaut. Il nécessite une intervention manuelle lors de toute défaillance importante.
   * **Défaillance immédiate** – Si cette option est sélectionnée, le pipeline sera interrompu dès qu’une défaillance importante aura lieu. Ce processus émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Ce processus émule essentiellement la validation manuelle de chaque échec par un utilisateur.

   ![Configuration du pipeline de production](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Dans l’onglet **Code Source**, sélectionnez le type de code que le pipeline doit traiter.

   * **[Configurer un pipeline de code full stack](#full-stack-code)**
   * **[Configuration d’un pipeline de déploiement ciblé](#targeted-deployment)**

Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.

Les étapes de création de votre pipeline de production varient en fonction du type de code source que vous avez sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

