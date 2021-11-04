---
title: Configuration de pipelines hors production
description: Consultez cette page pour en savoir plus sur la configuration d’un pipeline hors production dans Cloud Manager
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 14%

---


# Configuration de pipelines hors production {#configure-non-production-pipeline}

En plus du pipeline principal qui se déploie vers les environnements intermédiaire et de production, les clients peuvent configurer des pipelines supplémentaires, appelés Pipelines hors production.

Il existe deux types de pipelines hors production :

1. Qualité du code : Exécute des analyses de qualité du code sur le code d’une branche Git. Ce pipeline exécute les étapes de génération et de qualité de code.
1. Déploiement : Outre l’exécution des étapes de création et de qualité de code, ce pipeline déploie le code vers la non-production sélectionnée dans AEM environnement as a Cloud Service.

## Ajout d’un nouveau pipeline hors production {#adding-non-production-pipeline}

Sur l’écran d’accueil, ces pipelines sont répertoriés dans une nouvelle carte :

1. Accédez au **Pipelines** à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Ajout d’un pipeline hors production**  s’affiche. Sélectionnez le type de pipeline que vous souhaitez créer, au choix : **Pipeline de qualité du code** ou **Pipeline de déploiement**.

   >[!NOTE]
   >Pour les pipelines de déploiement, vous devez sélectionner l’environnement de déploiement.

   En outre, vous pouvez également configurer **Déclencheur de déploiement** et **Comportement des échecs de mesure importants** de **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. Sélectionner **[Code de pile complet](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** ou **[Code front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. Vous pouvez choisir le **Référentiel** et le **Branche Git**. Cliquez sur **Enregistrer**.

   >[!IMPORTANT]
   >Si un pipeline de code de pile complet existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-confignew1.png)

   >[!NOTE]
   >Avant de commencer à configurer les pipelines front-end, voir [parcours de création rapide de site](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) pour un workflow de bout en bout grâce à l’outil de création rapide de site d’AEM convivial. Ce site de documentation vous aidera à rationaliser le développement frontal de votre site AEM et à personnaliser rapidement votre site sans aucune connaissance AEM du serveur principal.

1. Le nouveau pipeline hors production s’affiche désormais dans la variable **Pipelines** carte.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   Le pipeline s’affiche sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   * **Ajouter** - permet d’ajouter un nouveau pipeline.
   * **Accès aux informations sur le référentiel** - permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lient pour en savoir plus sur les ressources de documentation du pipeline CI/CD.